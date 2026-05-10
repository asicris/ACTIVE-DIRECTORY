---
title: Guía de Creación de infraestrutura Active Directory - CONFIGURACIÓN DO CONTROLADOR DE DOMINIO
author: Cristina Puga Barreiros
date: 2026-05-06
description: Documentación técnica sobre como configurar o controlador de domino en Windows Server.
tags:
  - ActiveDirectory
  - Server
  - windows
status: published
nav_order: 8

---

# 1. Instalación do Controlador de Dominio

Un controlador de dominio (Domain Controller, DC) serve para ser o núcleo de control e seguridade dunha
rede baseada en Active Directory. É o servidor que xestiona identidades, permisos e recursos dun dominio
Windows.

A instalación de controlador de docminio consta de dúas fases:

- 1- Instalar os servizos de dominio de Active Directory.
- 2- Promover o controlador a Controlador de Dominio Primario.

## 1.0 - Configuración previa. Cambiar o nome do pc servidor

Cambiamos o nome do servidor en **Sistema -> Acerca de -> Cambiar nombre del equipo**.
Poñémoslle **WSERVER-teunome**.
![Cambiar nome servidor](images/image-26.png)
Reiniciamos para que aplique o cambio.
Comprobamos que está ben a iP, debería de quedar así:
![IP e nome Wserver-profe](images/image-25.png)

## 1.1 - Instalar os servizos de dominio de Active Directory

Imos a:

- Herramientas Administrativas →Administración del Servidor.
- Administrar -> Agregar roles y características.

![Agregar Roles y características](images/image-27.png)

- Seleccionar tipo de instalación: **Instalación basada en características o en reoles**
![Tipo de instalación](images/image-28.png)
- Selección de servidor: **Seleccionar un servidor del grupo de servidores**
![Selección do Servidor](images/image-29.png)
- Seleccionar roles de servidor: **SERVICIOS DE DOMINIO DE ACTIVE DIRECTORY**
![Roles de servidor](images/image-30.png)
E agregamos as características:
![Roles de servidor - Agregamos características](images/image-31.png)
- Características: Deixamos as por defecto
![Características](images/image-32.png)
- AD DS - Deixamos as por defecto
![AD DS](images/image-33.png)
- Confirmación - Prememos en **Instalar**
![Confirmacion](images/image-34.png)
Cando finaliza a instalación, xa nos avisa de que faltan pasos adicionais para que esta máquina sexa
Controladora de Dominio, e dános a opción de facelo dende aquí.
Escollemos Cerrar.
![Cerrar mentras instala](images/image-35.png)

## 1.2 - Promover a Controlador de dominio

Se imos as notificacións, xa nos indica que debemos **Promover a controlador de dominio**.
![Promover a controlador de dominio](images/image-36.png)
Indicamos o nome que vai ter o noso dominio **dcprofe.local** no meu caso, no voso caso sería **dcteunome.local**

![dcprofe.local](images/image-37.png)

![Nivel funcional](images/image-38.png)

- Opciones de DNS - Prememos en seguinte
![Opciones de DNS](images/image-39.png)
- Opciones adicionales - aceptamos o nome **NETBIOS** que propón:
![Nome netbios](images/image-40.png)
- Rutas de acceso - Aceptámolas
  ![Rutas de acceso por defecto](images/image-41.png)
  - **Base de Datos**: contén os obxectos do dominio: Usuarios, Equipos, ....
  - **Arquivos de rexistro**: actividades realizadas no AD.
  - **SYSVOL**: almacena información común para todo o dominio que deberá ser accesible por todos os clientes:
    - scripts de inicio de sesión.
    - directivas.
- Revisamos as opcións escollidas e prememos en seguinte:
![Opcions escollidas dc](images/image-42.png)
  
- Comprobación de requisitos
![Instalar despois de comprobar requisitos](images/image-43.png)
Aparecen unas advertencias, pero son normais. Escollemos Instalar e continuamos.
O equipo reiniciarase.

## 1.3 - Configuración servidor DNS

É un dos compoñentes fundamentais do directorio activo. Encárgase de **traducir os enderezos IP a nomes de dominio** e viceversa.

Cando navegamos escribimos http://www.google.com, é un servidor de DNS o que traduce esa URL
a unha dirección IP. Se non existisen os servidores DNS teriamos que lembrar e empregar os enderezos IP.
Nun servidor DNS podemos configurar:

- **zona de búsqueda directa**: procuramos un nome de equipo e devolve un enderezo IP.
- **zona de búsqueda inversa**: procuramos unha IP e devolve un nome de dominio.
- **reenviador DNS**: configúranse servidores DNS externos, aos que se lles preguntará en caso de non poder resolver un equipo no servidor DNS local.


### 1.3.1 Configuración do DNS

Iniciamos a ferramenta de administración do DNS.
![Herramientas DNS](images/image-44.png)
Inicialmente só se crea a zona de búsqueda directa. E de momento, nesta zona so está dado de alta o PC que é o propio servidor.
![Zona Directa  - dcprofe.local wserver-profe](images/image-45.png)

### 1.3.2 Reenviadores do DNS

No noso caso, para resolver calquera consulta que non sexa do noso DNS podemos acceder ao servidor de domino do Institudo **192.168.10.101** e logo ao de google, por exemplo, **8.8.8.8**, de forma que o que non resolva o noso DNS poda ser reenviado a estes outros.

Por suposto, neste momento estamos en rede interna e non temos saída fóra. No momento que configuremos o ROUTER NAT que nos dea saída ao exterior, este reenviador funcionará.

![Reenviadores - logo configurar GOOGLE](images/image-46.png)

#### 1.3.3 Comprobando configuración DNS

Vemos que como a búsqueda directa está configurada, responde ao nome do PC "wsever-profe" coa súa ip, empregando nslookup.

Pero ao revés, se poñemos a IP non nos devolve o nome, xa que a **búsqueda inversa aínda non está configurada**.
![comprobando dns](images/image-47.png)

## 1.3.4 Creación de DNS zona búsqueda INVERSA

Configuramos a búsqueda inversa, para **traducir IPs en nomes de equipos**.
Imos a Ferramentas -> DNS e en Zonas de búsqueda **inverse** co botón dereito engadimos unha zona **zona nueva**
![DNS-inversa-zona nueva](images/image-48.png)
Engadimos unha **zona principal**
![zona principal](images/image-49.png)
![configuracion zona inversa ambito de replicacion](images/image-50.png)
Definimos a nosa subrede:
![nosa subrede inversa](images/image-51.png)
![Actualizacions dinamicas](images/image-52.png)
Danos un resumo, e prememos Finalizar.
![configuracion final inversa dns](images/image-53.png)

Temos a **zona de búsqueda inversa** creada, pero non temos ningún equipo dado de alta nela, como se ve na imaxe:
![zona inversa dns](images/image-54.png)

- Imos a zona **búsqueda directa** ao pc servidor e dámoslle **actualizar PTR asociado**
- ![DNS directa actualizar ptr](images/image-56.png)
  
- Zona Inversa: Actualizamos o PTR asociado:
![DNS inversa actualizar ptr](images/image-55.png)
E xa aparece o PC servidor, como se ve na imaxen.
![dns inversa asociado](images/image-57.png)

- Comprobamos se fai resolución inversa
![cmd resolucion inversa nslookup](images/image-58.png)

### 1.4 - Uso do servidor DNS - Rexistros SRV

 Empréganse polo servidor DNS para localizar os equipos que ofrecen servizos específicos.

Exemplo: cando un cliente quere autenticarse consulta o DNS para atopar ó servidor Kerberos.
Observamos os rexistros SVR creados.

- **_gc**: catálogo Global.
- **_kerberos**: autenticación dos usuarios no Dominio.
- **_kpasswd**: contrasinal de Kerberos.
- **_ldap**: atopar os obxectos (Usuarios, Equipos...) no Catálogo Global.
![DNS-Resixtros SRV](images/image-59.png)

Os equipos preguntan ao DNS polos proveedores de servizos (LDAP,...)
O DNS responde aos equipos o equipo que proporciona esta información (winserver-profe)
![conten informcón rexistros SRV - DNS](images/image-60.png)

### 1.5 - Xestión de usuarios no DC

Ao ter un controlador de dominio, a **base de datos de usuarios locais xa non existe**.

- Os usuarios locais pasaron a ser **usuarios do dominio**
- Nun controlador de dominio, **non existen usuarios locais** (no pc Server)
![USUARIOS DO dc](images/image-61.png)

Agora poden xestionarse coa ferramenta: **Usuarios  y equipos de Active Directory**

## 1.6- Creando un usuario e un grupo global

Aproveitamos esta ferramenta para crear o grupo **gALUM** e o usuario **teunome** dentro deste grupo.

![Crear grupo galum](images/image-62.png)
![Crea grupo global de seguridade](images/image-63.png)
![Crear usuario dentr do grupo globar gAlum](images/image-64.png)
Engadimos o usuario dentro do grupo gAlum.
![alt text](images/image-65.png)