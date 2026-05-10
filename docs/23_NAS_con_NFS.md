---
title: NAS CON NFS
author: Cristina Puga Barreiros
date: 2026-05-06
description: Documentación técnica sobre configuración dun NAS con NFS
tags:
  - ActiveDirectory
  - Server
  - windows
  - NFS
status: published
nav_order: 27
---

# NFS

Imos crear un Share, chamado **Instruccions** dentro dun recurso compartido tipo **NFS**, creado partindo dun grupo de almacenamento **Publico** que da lugar a un disco virtual **publico** que se establece como **Mirroring**, e que se monta nun volumen chamado **M:**.

## Engadir discos a FSserver-teunome

- Engadismos 2 discos de 20GB
  ![Discos de 20GB](images/image-291.png)

  Inicializamos os discos a MBR. No **Administrador de discos**
  ![Inicializar discos](images/image-290.png)

## Paso 1- Instalar o servidor NFS en FSserver-teunome

Engadimos o Rol de **Servidor para NFS**. Dentro de *Servicios de archivos y almacenamiento -> Servidios de iSCSI y archivo*.
![Engadir rol SErvidor NFS](images/image-287.png)

- Agregamos a característica e procedemos a **Instalar**.

## Paso 2 - Crear grupo de almacenamento

Creamos un novo grupo de almacenamento cos dous discos de 20 GB
![Nuevo grupo](images/image-292.png)
![Discos físicos asociados](images/image-294.png)
Creado:
![Grupo crear](images/image-295.png)

- Creamos o **DISCO VIRTUAL** como **Mirroring** (DVPUBLICO)
![dISCO VIRTUAL](images/image-296.png)

Escollemos, aprovisionamento **delgado**.
Tamaño todo os **20GB**

![Resumen disco virtual](images/image-297.png)

E creamos o novo volumen **M:**.

![Novo volumen](images/image-298.png)

## Paso 3 - Crear o export

Dente a ferramenta de **Administración do servidor->Servidor de archivos**, accedemos a **Recursos Compartidos** como fixemos antes con SMB.

Imos empregar todo o espazo do disco virtual que acabamos de crear.

![Novo recurso compartido](images/image-288.png)

Escollemos o perfil **NFS-Rápido**, e escollemos:

- Sistema
- Servidor
- Volume

![NFS Rápido](images/image-289.png)

Escollemos o Volumen **M:**
![Volumen](images/image-299.png)

Establecemos nome de recurso **Instrucciones**

![alt text](images/image-300.png)

Autenticación Kerberos 5:
![Autenticación](images/image-301.png)

Imos darlle permiso á máquina **WSERVER-PROFE** de **solo lectura**.
![solo lectura a wserver-profe](images/image-302.png)
![alt text](images/image-303.png)

Deixamos os permisos da carpeta por defecto:
![Permisos carpeta](images/image-304.png)

Temos o resumo de recursos compartidos:
![Recursos Compartidos](images/image-305.png)

## Paso 4 - Compartir carpeta por NFS

Accedemos desde **FSserver-Profe**, dende o explorador de arquivos, e vemos que aparece unha carpeta onde nos permite o **Uso compartido por NFS**

![Uso compartido NFS](images/image-306.png)

Prememos en **Administrar uso compartido de NFS**
![permisos so lectura](images/image-307.png)

## Paso 5 - Acceder desde o cliente. Instalar cliente NFS

Na máquina cliente hai que instalar o cliente NFS.

Neste caso imos empregar **WSERVER-PROFE** para acceder á carpeta de rede compartida por NFS.

Desde Administrar - > Agregar roles y características. Neste caso **so imos engadir unha característica**, no  servidor **WSERVER-PROFE** a característica **Cliente para NFS**
![Cliente para NFS](images/image-308.png)

- **Montar o recurso compartido**, na unidade **O:**
`mount FSserver-profe:/instrucciones O:`

![Montado recurso](images/image-309.png)

Se quero escribir, debería de cambiar os permisos, podo facelo no recursos compartido, e vemos que nos deixa escribir.
![Permiso cambiado a lectura e escritura](images/image-310.png)
Xa nos deixa escribir desde WSERVER-PROFE.
![escritura](images/image-311.png)

## Proposta

Fai os cambios que consideres para que che deixe acceder como so lectura desde os clientes W11.