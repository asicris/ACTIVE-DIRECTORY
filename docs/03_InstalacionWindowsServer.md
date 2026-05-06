---
title: Guía de Creación Instalación de Window Server
author: Cristina Puga Barreiros
date: 2026-05-06
description: Documentación técnica para instalar Windows Server.
tags:
  - ActiveDirectory
  - server
  - windows
status: published
---
# Instalación de Windows Server

## Características MV
Instalamos nunha máquina virtual con:
- 4GB de RAM
- 2 CPUs 
- 150 GB de HD.
- Interface de rede en **modo INTERNA** - Rede **DC-PROFE** (No teu caso DC-TEUNOME)

Escollemos a **versión Standard** (con experiencia de Escritorio)

- Password para **administrador** contrasinal **abc123.**

## Proceso de instalación

- Versión Estándard
![Modo Estándar experiencia de escritorio](images/image-12.png)
![Aceptar licenza](images/image-13.png)
- Modo personalizado
![Instalación Versión Standard](images/image-7.png)
- Escollemos administrador con contrasinal **abc123.**
![Instalación usuario-contrasinal](images/image-8.png)
- Iniciamos sesión co usuario administrador e aparecen estes erros:
![Erros postinstalación](images/image-9.png)

- Instalamos as Virtualbox Additions

![Instalando Guest Additions](images/image-10.png)
- Reiniciar o equipo e actualizar  e unha vez reiniciado o equipo, accedemos ao asistente "Administrador del Servidor", en principio teremos 6 erros pero despois de esperar un par de minutos e clickar en actualizar desaparecen os erros(verde).
![Desaparecen erros despois de actualizar](images/image-11.png)
## Configuracións mellorar rendemento en máquinas de proba
### Desactivar Actualizacións automáticas 
O servidor, ao estar conectado a internet, provoca que o servidor se actualizase coas conseguintes esperas e reinicios.

Para evitalo, veremos como desactivar as actualizacións.

Se esta fose a instalación dun **servidor en produción deberíamos telo sempre
actualizado**.

Executamos desde o **cmd** o comando `sconfig` e seleccionamos a **opción 5 Configuración de la actualización**
![Sconfig - desactivar actualizacións automáticas](images/image-14.png)
e escollemos **3) actualización manual**
![Escollemos actualización manual](images/image-15.png)

Prememos **15 salir**. E quedan desactivadas as actualizacións automáticas. (so para entornos de proba na aula)

## Sysprep - para gardar un Windows sen SID
Aos sistemas operativos de Microsoft posteriores a Windows XP, débeselles aplicar un procedemento denominado **SYSPREP** antes de crear unha imaxe a partir deles.

Nós crearemos clons a partir desta máquina polo que necesitamos facelo.
Este proceso realiza varias tarefas internas, preparando o equipo para ser clonado.
- Limpar o equipo de drivers
- Cambiar o SID (Security Identifier) da máquina.

Podemos consultar o SID da máquina co comando whoami /user dende un intérprete
de comandos cmd (Tecla de Windows+R -> cmd).
![Whoami /user - sid](images/image-16.png)

### Erro que amosa unha máquina cando ten un SID duplicado na rede.
![Erro SID duplicado](images/image-17.png)

### Executar o sysprep

**Importante**: Antes de nada **facemos unha instantánea ou snapshot da máquina** e chamámoslle **Antes de Sysprep**
![Snapshot - antes de sysprep](images/image-18.png)

Executamos **`C:\Windows\System32\Sysprep\Sysprep.exe`**.

Escollemos as opcións da captura.

![Executando sysprep](images/image-19.png)

Unha vez finalizado o proceso do Sysprep, a máquina apágase.


#### Creamos unha OVA.

Agora podemos facer unha **W2022SERVER-BASE-SYSPREP.OVA**.

![ova](images/image-23.png)

#### Creamos un clon COMPLETO - AD-teunome-WSERVER2022
Clon completo da máquina creada, co nome **AD-teunome-WSERVER2022**.
Vemos que ao crear un clon de Win Server con sysprep, o SID que crea é diferente ao anterior, da máquina base.
![despois sysprep novo sid](images/image-24.png)

Quitamos da secuencia de arranque o disco duro da **Máquina Base**, para evitar acendela por erro.
![MaquinaBasePreparada](images/image-20.png)