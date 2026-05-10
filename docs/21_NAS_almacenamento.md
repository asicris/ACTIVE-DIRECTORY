---
title: Guía de Creación de infraestrutura Active Directory - XESTIÓN DE ALMACENAMENTO NUN NAS
author: Cristina Puga Barreiros
date: 2026-05-06
description: Documentación técnica sobre redirección de carpetas.
tags:
  - ActiveDirectory
  - Server
  - windows
status: published
nav_order: 25
---

# Xestión do almacenamento NAS

Lembramos que o almacenamento DAS é un almacenamento directamente conectado. A este almacenamento só se pode acceder dende a propia máquina.

Para **acceder ao almacenamento desde outras máquinas**, unha das posibilidades é implementar un **almacenamento NAS**.

As tecnoloxías que poden usar son **SMB** e **NFS**.

## **SMB** (Server Message Block)

SMB é un protocolo utilizado maioritariamente en sistemas de Microsoft. Tamén hai implantacións GNU/Linux.
Este protocolo permite ás aplicacións, dende un ordenador cliente, ler ou escribir ficheiros nun servidor da rede local. É dicir, **un PC cliente pode acceder aos arquivos almacenados nun servidor remoto**.

### **Versións** de SMB

Cando un cliente se conecta a un servidor, ambos negocian a versión máis alta que os dous soporten.

Un resumo de versións:

- SMB 1.0: Windows 2000 e Windows XP.
- SMB 2.0 / 2.1: Windows 2008 e Windows 7.
- SMB 3.0: Windows 2012 e Windows 8.
- **SMB 3.1.1**: Introducido con Windows 10 e Server 2016 / 2019 / 2022 / 2025. É a versión actual máis segura. Inclúe:
  - Pre-autenticación de integridade para evitar ataques Man-in-the-Middle.
  - Cifrado AES-128-GCM e AES-Samba 4256-GCM
  - Compresión de SMB (a partir Windows Server 2022).

Non confundir a versión do software libre: **Samba 4.0, que é a implementación libre do protocolo SMB para Linux/Unix**, que permite que un servidor Linux funcione como un Controlador de Dominio de Active Directory compatible con Windows. Pero a versión do software **Samba 4** é unha cousa **distinta** ao protocolo **SMB**.
De feito **Samba 4** emprega os protocolos SMB 2.1 e SMB3.1.1 para comunicarse cos clientes Windows.

> **OLLO!!**: Recoméndase sempre **deshabilitar SMB 1.0** nas organizacións, xa que foi a vía de entrada de virus famosos como WannaCry.

## NFS (Network File System)

Este protocolo utilizado maioritariamente en sistemas GNU/Linux. Tamén hai implantacións
para Microsoft. Windows Server 2016 en adiante tráeo de xeito nativo podendo tanto crear recursos compartidos NFS, como acceder a recursos compartidos NFS.

Este protocolo  permite o acceso a carpetas e arquivos de xeito remoto.

É moi impregado en sistemas GNU/Linux e Windows Server permite a súa implantación.

### Cando implantar NFS en Windows

É interesante implantar o protocolo NFS en Windows:

1. Cando queiras dar acceso aos discos da túa máquina, para gardar **máquinas virtuais nun contorno VMWare**. Gardando por exemplo os .vmdk das máquinas virtuais.
2. Cando deas **servizo** de arquivos a **clientes heteroxéneos**: Windows, GNU/Linux e Mac.
3. Aplicacións científicas ou de análise de datos (Alto rendemento e Big Data) que corren sobre Linux pero necesitan acceder a datos almacenados en servidores Windows. Xa que NFS ten menos sobrecarga de rede que SMB para certos tipos de trasferencias masivas de datos en sistemas non-Windows.

### Pasos para implantar NFS

- Paso 1. Instalar o servidor NFS.
- Paso 2. Crear o share. En NFS reciben o nome de exports.
- Paso 3. Instalar no cliente o cliente NFS.
- Paso 4. Conectarte dende o cliente.
