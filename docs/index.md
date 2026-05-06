# Active Directory - Índice de Contidos

## 🏠 Benvido

Este é o índice completo de toda a documentación sobre **Active Directory e infraestrutura de rede**. Selecciona o tema que te interesa ou segue a ruta de aprendizaxe recomendada.

---

## 📚 Ruta de Aprendizaxe Recomendada

Segue este orde para unha aprendizaxe estruturada:

1. [Escenario Inicial](01_Escenario_Inicial_A_Configurar.md) - Entende a arquitectura base
2. [Configuración do Router NAT](00_CONFIGURAR_ROUTERNAT.md) - Prepara a infraestrutura de rede
3. [Versións de Windows Server](02_VersionsWindowsServer.md) - Elixe a versión adecuada
4. [Instalación de Windows Server](03_InstalacionWindowsServer.md) - Instala o servidor
5. [Configuración de Rede](04_ConfiguracionRedeMV.md) - Configura as interfaces de rede
6. [Domain Controller](05_OControladorDedominio.md) - Entende o concepto
7. [Instalar Domain Controller](06_Instalar_DomainControler.md) - Implementación práctica
8. [Unir Windows ao Dominio](07_UnirEquiposWindowsaoDomino.md) - Integra equipos

---

## 🔍 Índice por Seccións

### 1️⃣ Infraestrutura Base e Rede

| Documento | Descrición |
|-----------|-----------|
| [Configurar Router NAT](00_CONFIGURAR_ROUTERNAT.md) | Configuración de encamiñador NAT |
| [Escenario Inicial](01_Escenario_Inicial_A_Configurar.md) | Descrición do escenario a configurar |
| [Outro Escenario - Proxecto Recuperación](01_OUTRO_ESCENARIO_MAIO-PROXECTO-RECUPERACION.md) | Escenario alternativo para recuperación |

### 2️⃣ Windows Server

| Documento | Descrición |
|-----------|-----------|
| [Versións de Windows Server](02_VersionsWindowsServer.md) | Comparativa de versións (2012, 2016, 2019, 2022) |
| [Instalación de Windows Server](03_InstalacionWindowsServer.md) | Proceso de instalación paso a paso |
| [Configuración de Rede (MV)](04_ConfiguracionRedeMV.md) | Configuración de interfaces de rede nas máquinas virtuais |

### 3️⃣ Domain Controller (DC)

| Documento | Descrición |
|-----------|-----------|
| [O Controlador de Dominio](05_OControladorDedominio.md) | Teoría: qué é un DC, funcións e importancia |
| [Instalar Domain Controller](06_Instalar_DomainControler.md) | Guía práctica de instalación |

### 4️⃣ Unión ao Dominio - Windows

| Documento | Descrición |
|-----------|-----------|
| [Unir Equipos Windows ao Dominio](07_UnirEquiposWindowsaoDomino.md) | Proceso de incorporación ao dominio |
| [Boas Prácticas](11_BoasPracticasUnirDominio.md) | Recomendacións e boas prácticas |

### 5️⃣ Integración Linux - Active Directory (Windows)

| Documento | Descrición |
|-----------|-----------|
| [Protocolos e Pasos (Linux-AD)](08_PASOS-PROTOCOLOS-INTERVEÑEN-UNION-LINUX-AD.md) | Protocolos implicados (Kerberos, LDAP, DNS) |
| [Unir Ubuntu a AD de Windows](09_UnirUbuntuaDominioADWindows.md) | Integración de Ubuntu con Active Directory |

### 6️⃣ Xestión do Dominio

| Documento | Descrición |
|-----------|-----------|
| [Organización de OUs e Grupos](10_OrganizacionOUGrupos.md) | Estructura lóxica do dominio |

### 7️⃣ Políticas de Grupo (GPO)

| Documento | Descrición |
|-----------|-----------|
| [Políticas de Grupo (GPO)](12_GPO.md) | Conceptos e teoría sobre GPO |
| [Tarefa: Aplicar GPO en AD](13_Tarefa-aplicarGPOenAD.md) | Exercicio práctico de aplicación de políticas |

### 8️⃣ Xestión de Almacenamento

| Documento | Descrición |
|-----------|-----------|
| [Xestión do Almacenamento](14_Xestion%20do%20almacenamento.md) | Conceptos fundamentais |
| [Exercicio Xestión Almacenamento](14_1_Exercicio_XestionAlmacenamento.md) | Tarefa práctica |
| [Solución Exercicio Almacenamento](14_1_solucion_Exercicio_XestionAlmacenamento.md) | Solución do exercicio |
| [DAS e Carpetas de Usuarios](15_DAS_e_Carpetas_Usuarios.md) | Almacenamento directo e carpetas de usuarios |
| [Tarefa: Configurar DAS e Carpetas](16_Tarefa-ConfigurarDAS-CarpetasUsuarios.md) | Implementación práctica |
| [NAS Almacenamento](21_NAS_almacenamento.md) | Conceptos de almacenamento en rede |

### 9️⃣ Perfis Móbiles e Redirección de Carpetas

| Documento | Descrición |
|-----------|-----------|
| [Perfis Móbiles](17_PerfisMobiles.md) | Teoría e beneficios dos perfis móbiles |
| [Tarefa: Perfis Móbiles](18_Tarefa_Perfis_Mobiles.md) | Implementación práctica |
| [Redirección de Carpetas](19_Redireccion_carpetas.md) | Teoría e configuración |
| [Tarefa: Redirección de Carpetas](20_Tarefa_Redireccion_Carpetas.md) | Exercicio práctico |

### 🔟 NAS (Network Attached Storage)

| Documento | Descrición |
|-----------|-----------|
| [NAS con SMB](22_NAS_con_SMB.md) | Configuración de NAS usando protocolo SMB |
| [NAS con NFS](23_NAS_con_NFS.md) | Configuración de NAS usando protocolo NFS |

### 1️⃣1️⃣ Samba4 como Domain Controller

| Documento | Descrición |
|-----------|----------|
| [Servidor DC con Samba4](24_ServidorDC_LinuxSamba4.md) | Alternativa Linux para Domain Controller |
| [Unir Windows a DC Samba4](25_UnirEquipoWindows_DCenSamba4.md) | Integración de Windows con Samba4 |
| [Configurar RSAT en Windows](27_ConfigurarRSATenWindows.md) | Ferramentas RSAT para xestión remota |

### 1️⃣2️⃣ Integración Linux - Samba (Dominio Samba)

| Documento | Descrición |
|-----------|----------|
| [Unir Linux a Dominio Samba](20_UnirEquioLinux-DOMINIOSAMBA.md) | Integración con dominio Samba |
| 

---

## 🎓 Por Nivel de Experiencia

### Iniciante 🟢
Comeza por aquí se non tes experiencia previa:
- [Escenario Inicial](01_Escenario_Inicial_A_Configurar.md)
- [Versións de Windows Server](02_VersionsWindowsServer.md)
- [Instalación de Windows Server](03_InstalacionWindowsServer.md)
- [O Controlador de Dominio](05_OControladorDedominio.md)

### Intermedio 🟡
Xa tes coñecementos básicos:
- [Instalar Domain Controller](06_Instalar_DomainControler.md)
- [Unir Equipos Windows](07_UnirEquiposWindowsaoDomino.md)
- [Organización de OUs e Grupos](10_OrganizacionOUGrupos.md)
- [Políticas de Grupo](12_GPO.md)

### Avanzado 🔴
Xa tes experiencia significativa:
- [Integración Linux-AD](09_UnirUbuntuaDominioADWindows.md)
- [Samba4 como DC](24_ServidorDC_LinuxSamba4.md)
- [NAS e Almacenamento Avanzado](22_NAS_con_SMB.md)
- [Perfis Móbiles](17_PerfisMobiles.md)

---

## 🏷️ Por Tema

### 🐧 Linux e Integración

- [Protocolos Linux-AD](08_PASOS-PROTOCOLOS-INTERVEÑEN-UNION-LINUX-AD.md)
- [Ubuntu e AD](09_UnirUbuntuaDominioADWindows.md)
- [Linux e Samba](20_UnirEquioLinux-DOMINIOSAMBA.md)
- [Samba4 DC](24_ServidorDC_LinuxSamba4.md)

### 📁 Almacenamento e Datos

- [Xestión Almacenamento](14_Xestion%20do%20almacenamento.md)
- [DAS e Carpetas](15_DAS_e_Carpetas_Usuarios.md)
- [NAS SMB](22_NAS_con_SMB.md)
- [NAS NFS](23_NAS_con_NFS.md)
- [Redirección Carpetas](19_Redireccion_carpetas.md)

### 👥 Usuarios e Seguridade

- [Organización OUs](10_OrganizacionOUGrupos.md)
- [Políticas de Grupo](12_GPO.md)
- [Perfis Móbiles](17_PerfisMobiles.md)

### ⚙️ Infraestrutura

- [Router NAT](00_CONFIGURAR_ROUTERNAT.md)
- [Rede MV](04_ConfiguracionRedeMV.md)
- [Windows Server](02_VersionsWindowsServer.md)

---

## 🎯 Exercicios Prácticos

Documentos con tarefas e exercicios propostos:

| Tarefa | Solución |
|--------|----------|
| [Xestión Almacenamento](14_1_Exercicio_XestionAlmacenamento.md) | [Solución](14_1_solucion_Exercicio_XestionAlmacenamento.md) |
| [Configurar DAS e Carpetas](16_Tarefa-ConfigurarDAS-CarpetasUsuarios.md) | --- |
| [Aplicar GPO](13_Tarefa-aplicarGPOenAD.md) | --- |
| [Perfis Móbiles](18_Tarefa_Perfis_Mobiles.md) | --- |
| [Redirección Carpetas](20_Tarefa_Redireccion_Carpetas.md) | --- |

---

## 📖 Guía de Lectura

### Para Administrador de Redes Novo
1. Infraestrutura base
2. Windows Server
3. Domain Controller
4. Unión ao dominio
5. Xestión (OUs, grupos)
6. GPO

### Para Administrador que Quere Integrar Linux
1. Coñecementos de AD (seccións 1-5)
2. [Protocolos](08_PASOS-PROTOCOLOS-INTERVEÑEN-UNION-LINUX-AD.md)
3. [Ubuntu e AD](09_UnirUbuntuaDominioADWindows.md)
4. [Linux e Samba](20_UnirEquioLinux-DOMINIOSAMBA.md)

### Para Quem Quer Samba4 como DC
1. [Infraestrutura](01_Escenario_Inicial_A_Configurar.md)
2. [Samba4 DC](24_ServidorDC_LinuxSamba4.md)
3. [Unir Windows a Samba](25_UnirEquipoWindows_DCenSamba4.md)

---

## 🛠️ Recursos

### Imaxes de Referencia
- **images/** - Imaxes xerais do proxecto
- **IMAGESNAS-SMB/** - Imaxes específicas de NAS e SMB

---

## 📝 Información do Proxecto

- **Licencia:** CC0 1.0 Universal
- **Idioma:** Galego
- **Tipo:** Documentación Educativa
- **GitHub Pages:** Este proxecto utiliza GitHub Pages para a visualización web

---

## 🔗 Búsqueda Rápida

**Procuro información sobre...**

- **Instalar servidor DC:** [Aquí](06_Instalar_DomainControler.md)
- **Unir equipos ao dominio:** [Aquí](07_UnirEquiposWindowsaoDomino.md)
- **Linux e Active Directory:** [Aquí](09_UnirUbuntuaDominioADWindows.md)
- **Políticas de grupo:** [Aquí](12_GPO.md)
- **Almacenamento en rede:** [Aquí](22_NAS_con_SMB.md)
- **Samba4 en Linux:** [Aquí](24_ServidorDC_LinuxSamba4.md)

---

**Última actualización:** 6 de maio de 2026

**Voltar ao [README.md](../README.md) principal**
