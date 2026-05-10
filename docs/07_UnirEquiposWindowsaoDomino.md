---
title: Guía de Creación de infraestrutura Active Directory - UNIR PCs WINDOWS AO domino
author: Cristina Puga Barreiros
date: 2026-05-06
description: Documentación técnica sobre como unir equipos Windows ao Dominio.
tags:
  - ActiveDirectory
  - Server
  - windows
status: published
nav_order: 9

---

# Unir equipos Windows ao dominio AD

Unha das posibilidades de Active Directory é de actuar como servizo de autenticación. Deste xeito, un cliente pode configurarse para que solicite ao servidor a validación dun usuario e contrasinal para dar acceso aos seus recursos. Como cliente poden actuar aplicacións de escritorio, aplicacións web ou incluso sistemas operativos. Esta última opción é moi útil para unha rede de ordenadores, pois centraliza a autenticación dos usuarios nun único servizo.

Para poder probar as posibilidades que nos ofrece Active Directory necesitamos ter equipos que actúen como cliente do noso servizo.

Lembramos o esquema de rede:
![CONFIGURACION REDE](images/image-21.png)

Imos configurar o **PC Windows 11 Pro** con IP **172.20.0.3/16**, tal e como se ve na imaxe, e unido ao dominio.
Desta forma o servidor DNS será **172.20.0.100** que é o noso servidor de dominio e **servidor dns**.

## 1. Configuración da rede do Windows 11 Pro cliente

**Características da MV de Windows 11 Pro**
![MV Windows 11 pro](images/image-66.png)

- Nome da MV: **WIN01-DCPROFE**
- Hostname: **WIN01-DCPROFE**
- Rede: 172.20.0.3/16 - DNS:172.20.0.100 - GW - 172.20.0.1 (Para cando o configuremos)
![Rede cliente windows](images/image-67.png)
Comprobamos a conectividade co servidor:
![Conectividade servidor](images/image-69.png)

## 2. Cambiar o nome do hostname do PC
![Nombre del Pc](images/image-68.png)

## 3. Unir o equipo ao dominio
Acceder ás propiedades do sistema, desde algunha das vías e configurar o equipo como **membro do dominio DCPROFE.LOCAL**
![uNIR AO DOMINIO](images/image-70.png)
Vai solicitar a chave dun usuario con permisos de **administración**, con permisos para unir o PC ao dominio, no noso caso podemos usar as credenciais do **Administrador do domino**.
![Unir ao dominio co usuario administrador do dominio](images/image-71.png)

Indica que se uniu correctamente:
![Equipo unido ao dominio](images/image-72.png)

### 3.1 Posibles Erros ao unir ao dominio
Cando unimos un equipo ao dominio, un erro típico pode ser o que aparece na imaxe.

Este erro pode estar asociado a un **erro ao escribir o nome do dominio**, pero se non é o caso, o **erro está na configuración do nivel IP, indicando que o servidor DNS non apunta a IP do controlador de dominio**.
![erro unir ao dominio](images/image-73.png)

## 4. Cambios no servidor ao unir o equipo cliente
Cando se une un novo PC:
- Aparece no apartado **COMPUTERS** da ferramenta de **Usuarios y equipos de Active Directory**
- No apartado DNS aparece este equipo, tanto na búsqueda directa como na búsqueda inversa.
![dns E COMPUTERS](images/image-75.png)

Se comprobamos o dns:
![win01-dcprofe nslookup](images/image-76.png)
Resolución inversa:
![resolucion inversa 172.20.0.3](images/image-77.png)

## 5. Cambios no cliente win01-dcprofe

O administrador do dominio é membro do grupo Administradores local.

![Administrador dominio membro de administradores local](images/image-78.png)

O nome do equipo leva tamén o nome do dominio win01-dcprofe.**dcprofe.local**
![Nome do equipo coa coletilla dcprofe.local](images/image-79.png)

Vemos que se antes existía un usuario local co mesmo nome, a carpeta de perfil de usuario, ao usuario do dominio, lle engade a coletilla cris.**DCPROFE** para distinguila do perfil do **usuario local cris**
![PERFIL USUARIO DOMINIO](images/image-80.png)

## 6. Acceder ao dominio co nome UPN ou con formato clásico
Pódese acceder ao dominio co nome de SAMAccount, ou co nome UPN (que é máis moderno e permite nomes de calquera lonxitude)
Por exemplo, co usuario:
![Usuario lola.liboreiro](images/image-125.png)
![UPN](images/image-126.png)
![SamAccountName](images/image-127.png)
**Formato UPN (User Principal Name)**
Este é o formato moderno, semellante a un correo electrónico. É o que debes usar se o teu nome de usuario é longo (máis de 20 caracteres), xa que non ten a limitación do sAMAccountName.
![acceso formato UPN](images/image-124.png)
    Exemplo: lola.liboreiro.pereira@dcprofe.local
    Cando escribes o @, Windows entende automaticamente a que dominio queres conectar, polo que non importa o que poña debaixo do cadro de texto (onde adoita dicir "Iniciar sesión en: ...").

**Formato Clásico (Down-Level Logon Name)**

Este é o formato tradicional de tipo DOMINIO\usuario. Lembra que aquí o nome de usuario está limitado a 20 caracteres. Se o teu nome no AD se cortou, tes que poñelo exactamente como aparece no campo "Nombre de inicio de sesión (anterior a Windows 2000)".

Se o equipo xa está no dominio, este nome é o que debes poñer.
![nome formato clásico](images/image-123.png)

    Exemplo: DCPROFE\lola.liboreiro.perei

## 7. Acceder ao equipo unido ao dominio como usuario local

Por defecto, cando un equipo se une ao dominio, o usuario que se conecta é o de dominio.

![usuario do domino inicia sesión](images/image-81.png)

Se queremos acceder como usuario local temos dúas opcións:

- Poñer no nome de usuario **.\nomeusuariolocal**, exemplo, no noso caso **.\administrador**
![inicio sesion pc local](images/image-82.png)
- Poñer no nome de usuario **nomePC\nomeusuariolocal**, no noso caso **win01-dcprofe\administrador**
![nomepclocal\usuariolocal](images/image-83.png)
