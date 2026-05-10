---
title: Unir equipo Windows a dominio gnu/linux con Samba 4
author: Cristina Puga Barreiros
date: 2026-05-06
description: Documentación técnica sobre configuración dun NAS con NFS
tags:
  - ActiveDirectory
  - Server
  - dominio
  - gnu/linux
  - samba4
status: published
nav_order: 29
---

# Unir equipo Windows ao Controlador de Dominio Samba4

## Configuracións a facer

1. Configuramos as tarxetas de VBox
Rede Interna - iescris.local
![Rede Interna](images/image-210.png)
2. Configuramos a IP/GW/DNS
![configuración IP-GW-DNS](images/image-211.png)
3. Configuramos nome do equipo
4. Configuramos dominio e unimos ao equipo.
![Equipo Unido Dominio](images/image-209.png)

## Verificación

- Imos ao **servidor de dominio**, e vemos que está aquí dado de alta o novo pc de Wcliente03:
![Wcliente03 dado de alta](images/image-212.png)
- Iniciamos sesión no **pc cliente Wcliente03**:
![Accedemos con usuario do dominio usuprueba](images/image-213.png)