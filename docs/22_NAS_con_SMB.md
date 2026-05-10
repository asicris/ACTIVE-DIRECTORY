---
title: NAS con Samba SMB
author: Cristina Puga Barreiros
date: 2026-05-06
description: Documentación técnica sobre configuración NAS con Samba SMB
tags:
  - ActiveDirectory
  - Server
  - windows
  - SMB
status: published
nav_order: 26
---

# Implementando NAS con SMB

O **Escenario** que imos implementar é o seguinte:

![Escenario NAS](images/image-150.png)

Pasos a realizar:

1. **Paso 1 - Configurar a MV Windows Server FSserver-teunome**: Configurar un NOVO SERVIDOR Windows Server chamado **FSserver-teunome** que fará de servidor de ficheiros, como se ve na imaxe do escenario.
2. **Paso 2 - Agregar o servidor FS á pantalla de administración do DC** e Configurar o **rol SERVIDOR DE ARCHIVOS** no novo servidor, configuramos desde o servidor WSERVER-teunome.
3. **Paso 3 - Configurar os discos do servidor**: Os discos no servidor NAS serán dous discos de 10GB nunha controladora LSAS.Configurados como un **Storage Space (grupos de almacenamiento), distribución Simple** (similar a **Raid 0**). Crearase un pool **Docencia-Pool** cos dous discos físicos engadidos.
4. **Paso 4 - Crear un recurso compartido con SMB - Creando un Share:** Crear recurso compartido **Maquinas virtuais** - Compartirá unha carpeta que se chame **Maquinas-Virtuais**, que estará almacenada nun disco virtual dentro do pool "Docencia-Pool", o disco virtual chamarase tamén **Maquinas-Virtuais**

> Farase toda a configuración de FSserver de **forma remota** desde o servidor **WINSERVER-teunome**, a través da ferramenta **Administrador do servidor**

Vai aplicando estes pasos sobre o teu escenario de VBox da aula, e captura as evidendias que consideres.

---

<details>
<summary><strong>Paso 1 - Configurar a MV Windows Server FSserver-teunome
</strong></summary>

## Paso 1 - Configurar a MV Windows Server FSserver-teunome

- Importamos a **.OVA de Windows Server**, ou facemos un **clon enlazado da máquina de Windows Server BASE** (que temos con sysprep). Chamámoslle **FSserver-teunome**
- Cambiamos o nome do hostname.
- Configuramos a rede.
![Configuracion básica FSserver](images/image-149.png)
- Damos de alta o novo servidor no DOMINIO.
![Alta servidor no dominio](images/image-152.png)
- Metemos ao servidor dentro da UO **Servidores de arquivos**
![UO Servidores de arquivos](images/image-153.png)

- Agregamos o servidor ao DNS.
![DNS](images/image-155.png)

</details>

<details>
<summary><strong> Paso 2 - Agregar o servidor FS á pantalla de administración do DC e aplicar rol Servidor Arquivos</strong></summary>

## Paso 2 - Agregar o servidor FS á pantalla de administración do DC e aplicar rol Servidor Arquivos

Desde **DCprofe** asignamos o servidor:
![Administrar->Agregar Servidores](images/image-151.png)
Buscamos o nome do servidor de ficheiros e engadímolo:
![Engadir servidor de ficheiros](images/image-154.png)

Dentro da consola de Administrar Servidor ->**Todos los servidores** vemos que xa está o novo servidor engadido:
![Todos los servidores](images/image-156.png)

### Paso 2A - Agregar o rol Servidor de Ficheiros

Desde a **consola do DCPROFE**, imos agregar un **novo rol**, e agregarémolo sobre o servidor FSserver-PROFE.
![Agregar novo rol](images/image-157.png)

Agregar rol Servidor de archivos dentro de Servidor iSCSI.

![Agregar rol Servidor de archivos dentro de Servidor iSCSI](images/image-158.png)

Continuamos con **Seguinte** en Característica, sen modificar nada, e en Confirmación **instalamos**.

![Confirmacion instalar](images/image-159.png)
![Instalando](images/image-160.png)

</details>

<details>
<summary><strong> Paso 3 - Configurar os discos do servidor (Storage Space - Simple)</strong></summary>

## Paso 3 - Configurar os discos do servidor (SAS-Storage Space - Simple)

Imos asignar dous discos de 10GB ao servidor nunha controladora LSAS.

![2 discos LSAS](images/image-162.png)

Configuramos os espazos de almacenamento no **Servizo de arquivos**
![administrador do servidor](images/image-163.png)

Creamos un novo grupo de almacenamento - 

![Grupos de almacenamiento novo](images/image-164.png)

Imos chamarlle **Docencia-Pool**.
![Docencia-Pool](images/image-170.png)

Indicámoslle que vai empregar os dous discos físicos que temos.
![Novo grupo con dosus discos](images/image-165.png)
Confirmamos:![Confirmación](images/image-171.png)

Creamos un novo **Disco Virtual**
![Disco Virtual](images/image-166.png)

Escollemos o grupo de almacenamento:
![grupo almacenamento escollido](images/image-167.png)

![Creado o novo Disco virtual](images/image-168.png)
Creamos un Disco Virtual de **distribución simple**, similar a Raid 0.
![raid 0 - simple](images/image-172.png)

Tipo de aprovisionamiento, fijo.
![Aprovisionamiento fijo](images/image-173.png)

 Se escollemos “aprovisionamento fijo” non poderemos crear un disco virtual de maior tamaño que o dispoñible no pool. Se escollemos “aprovisionamento delgado” non temos ese problema.
 ![erro con máis tamaño](images/image-174.png)

 Escollemos o tamaño total que temos 6GB, e quedaría espazo para máis discos virtuais no mesmo pool.
![disco virtual maquinas-virtuais 6GB](images/image-176.png)

No último paso, créase o **volume**.
![Creación volume](images/image-177.png)

Creamos un volume de todo o espazo.
![Volume  de todo o espazo](images/image-178.png)

![tamaño](images/image-179.png)

Asignámoslle a letra P.
![Letra P](images/image-180.png)

Configuramos o sistema de arquivos, imos aplicarlle **NTFS** neste caso e darlle a etiqueta de volumen **Maquinas-Virtuais**:
![Sistema de ficheiros](images/image-181.png)

Vemos o resume do **Volume**:
![volume confirmación](images/image-182.png)

Vemos en **VOLÚMENES**, que aparece o novo volumen.
![Novos volúmenes](images/image-183.png)

</details>

<details>
<summary><strong> Paso 4 - Crear un recurso compartido con SMB - Creando un Share</strong></summary>

## Paso 4 - Crear un recurso compartido con SMB - Creando un Share

Crearemos o share, **Maquinas-Virtuais**, dentro do volume Maquinas-Virtuais creado no servidor FSserver-PROFE.

Imos a **Servicios de archivos y almacenamiento**
![Servicios de arhivos y almacenamiento](images/image-184.png)

Vemos os recursos compartidos (**shares**) xa creados previamente e a súa ruta no sistema de arquivos. En **DC-PROFE** cando instalas Active Directory créanse NETLOGON e SYSVOL:

- **NETLOGON**: gárdanse **scripts de inicio de sesión** dos usuarios.
- **SYSVOL**: é a forma que ten o controlador de dominio de facer chegar as **GPO** aos membros do domino.

Imos crear un novo recurso: escollemos **Nuevo recurso compartido**
![Nuevo recurso compartido](images/image-185.png)

Debemos escoller o **perfil do recurso compartido** entre:

- **SMB-Rápido**: é o método máis rápido para compartir un directorio. Permite escoller o servidor, o nome, a ruta local e os permisos.**Escollemos esta opción**.
- **SMB-Avanzado**: permite o mesmo que o perfil rápido, escoller os propietarios dos arquivos, clasificación dos datos por defecto e cuotas. Necesita o rol adicional de Administrador de  recursos do servidor de arquivos”.
- **SMB-Aplicacións**: configuración especializada para o sistema de virtualización de Microsoft Hiper-V, bases de datos e outras aplicacións de servidores.
![SMB-rapido](images/image-186.png)

Escollemos o servidor onde vai estar o recurso compartido e o volumen onde se creará:
![servidor-volume do recurso compartido](images/image-187.png)

Indicamos o nome do recurso compartido e a ruta local e remota para poder acceder desde outros equipos:
![Ruta Remota](images/image-188.png)

Deixamos todas as opcións sen marcar:
![Parametros compartición](images/image-189.png)

Deixamos todos os permisos por defecto, xa os modificaremos máis adiante.
![Permisos](images/image-190.png)

Continuamos e finalizamos, e podemos ver que aparece o recurso compartido:

![Recurso Compartido](images/image-191.png)

Se imos ao **explorador de arquivos** de calquera dos PCs da rede interna podemos ver que xa está compartida a carpeta:
![Carpeta compartida Maquinas-Virtuais](images/image-192.png)