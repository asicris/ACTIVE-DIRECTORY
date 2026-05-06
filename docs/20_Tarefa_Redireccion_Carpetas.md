---
title: Guía de Creación de infraestrutura Active Directory - REDIRECCIÓN DE CARPETAS
author: Cristina Puga Barreiros
date: 2026-05-06
description: Documentación técnica sobre redirección de carpetas.
tags:
  - ActiveDirectory
  - Server
  - windows
status: published
---

# Exercicio Redirección Carpetas

**Escenario de partida** (rede - OU - Grupos - Usuarios)

Temos o seguinte configurado

![estrutura dominio](images/imageESTRUTURADOMINIOPRACTICA.png)

- As seguintes OU:
![OU PCs](images/image-129.png)
![OU Usuarios](images/image-130.png)

- Os seguintes usuarios e grupos:
![Usuarios a crear](images/image-102.png)
  - Profesores:
    - Cristina Puga Barreiros
    - Lola Liboreiro Pereira
![Configura estes grupos](images/image-122.png)

**Estrutura discos** do servidor DC

- **WSERVER-teunome**
  - **C:** - Disco do sistema
  - **E:** - Disco de 32 GB que engadimos na controladora SATA.
    - Contén a carpeta **Usuarios** e dentro
      - Datos: Empregada para as **carpetas particulares de usuario**
      - **Perfiles**: crearás esta carpeta para gardar os **perfiles móbiles** dos usuarios.

## Tarefa 6 - Redireccionar carpetas 

1. Crea unha carpeta "**Redireccion**", dentro do segundo disco do servidor na ruta `e:\usuarios\Redireccion`
2. Crea Redireccionamento de carpetas sobre todos os usuarios.
3. Entra nun PC Windows co usuario **"Lucas Sanjuas"**:
   1. Comproba se redireccionou a carpeta Documentos e escritorio accedendo ao servidor.
   2. Fai algún cambio no escritorio e na carpeta documentos no Cliente
4. Entre noutro PC Windows co mesmo usuario **"Lucas Sanjuas"**:
   1. Comproba que recolle os cambios feitos desde o outro Pc no escritorio e en documentos.
