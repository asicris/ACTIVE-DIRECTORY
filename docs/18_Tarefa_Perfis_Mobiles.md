---
title: Exercicio de aplicación de perfís móbiles
author: Cristina Puga Barreiros
date: 2026-05-06
description: Exercicio de aplicación de perfís móbiles nun AD.
tags:
  - ActiveDirectory
  - Server
  - windows
status: published
nav_order: 22

---

# Exercicio Perfiles móbiles

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

## Tarefa 6 - Crear perfís móbiles so sobre clientes WINDOWS.

1. Crea unha carpeta perfís, dentro do segundo disco do servidor na ruta `e:\usuarios\perfiles`
2. Crea perfís móbiles sobre os usuarios:
   1. Xoan Loureiro Paz
   2. Ana Valladares Comesaña
3. Comproba que de forma normal, o usuario administrador non pode acceder á carpeta perfiles.
4. Crea unha GPO para que o administrador poida acceder ás carpetas de perfiles dos usuarios. Chama a GPO **"Personalización perfís móbiles"**.
5. Aplica a GPO sobre a **OU Equipos**
6. Comproba que agora o administrador pode acceder sobre a carpeta de perfil. (Captura esta pantalla soamente, onde se vexa que é o teu servidor)
7. Cambia algo no perfil dun usuario nun PC Windows, logo inicia sesión desde outro PC Windows do dominio e comproba que se manteñen os cambios feitos.
