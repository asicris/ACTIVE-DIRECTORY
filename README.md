# Active Directory - Documentación de Infraestrutura de Rede

## 📋 Descripción do Proxecto

Este repositorio contén a documentación completa sobre a configuración e xestión de **Active Directory** en entornos empresariais, incluyendo integración con sistemas Linux mediante Samba4. É un recurso educativo que cobre desde a instalación inicial ata a xestión avanzada de dominios, usuarios e recursos compartidos.

## 🎯 Obxetivos

- Entender a arquitectura de Active Directory en Windows Server
- Configurar e instalar Domain Controllers
- Xestionar unidades organizativas (OUs) e grupos
- Aplicar políticas de grupo (GPO)
- Integrar equipos Windows e Linux no dominio
- Xestionar almacenamento en rede (NAS) con SMB e NFS
- Configurar perfis móbiles e redirección de carpetas

## 📚 Estructura de Contidos

### 1. **Infraestrutura Base**
- [00_CONFIGURAR_ROUTERNAT.md](docs/00_CONFIGURAR_ROUTERNAT.md) - Configuración do Router NAT
- [01_Escenario_Inicial_A_Configurar.md](docs/01_Escenario_Inicial_A_Configurar.md) - Escenario inicial
- [01_OUTRO_ESCENARIO_MAIO-PROXECTO-RECUPERACION.md](docs/01_OUTRO_ESCENARIO_MAIO-PROXECTO-RECUPERACION.md) - Proxecto de recuperación

### 2. **Windows Server**
- [02_VersionsWindowsServer.md](docs/02_VersionsWindowsServer.md) - Versións de Windows Server
- [03_InstalacionWindowsServer.md](docs/03_InstalacionWindowsServer.md) - Instalación de Windows Server
- [04_ConfiguracionRedeMV.md](docs/04_ConfiguracionRedeMV.md) - Configuración de rede nas máquinas virtuais

### 3. **Domain Controller**
- [05_OControladorDedominio.md](docs/05_OControladorDedominio.md) - Concepto de controlador de dominio
- [06_Instalar_DomainControler.md](docs/06_Instalar_DomainControler.md) - Instalación do Domain Controller

### 4. **Unión ao Dominio**
- [07_UnirEquiposWindowsaoDomino.md](docs/07_UnirEquiposWindowsaoDomino.md) - Unir equipos Windows ao dominio
- [08_PASOS-PROTOCOLOS-INTERVEÑEN-UNION-LINUX-AD.md](docs/08_PASOS-PROTOCOLOS-INTERVEÑEN-UNION-LINUX-AD.md) - Protocolos implicados
- [09_UnirUbuntuaDominioADWindows.md](docs/09_UnirUbuntuaDominioADWindows.md) - Integración de Ubuntu con AD
- [20_UnirEquioLinux-DOMINIOSAMBA.md](docs/20_UnirEquioLinux-DOMINIOSAMBA.md) - Unir Linux a dominio Samba

### 5. **Xestión do Dominio**
- [10_OrganizacionOUGrupos.md](docs/10_OrganizacionOUGrupos.md) - Organización de unidades organizativas e grupos
- [11_BoasPracticasUnirDominio.md](docs/11_BoasPracticasUnirDominio.md) - Boas prácticas

### 6. **Políticas de Grupo (GPO)**
- [12_GPO.md](docs/12_GPO.md) - Conceptos de Políticas de Grupo
- [13_Tarefa-aplicarGPOenAD.md](docs/13_Tarefa-aplicarGPOenAD.md) - Aplicación práctica de GPO

### 7. **Xestión de Almacenamento**
- [14_Xestion do almacenamento.md](docs/14_Xestion%20do%20almacenamento.md) - Conceptos de almacenamento
- [14_1_Exercicio_XestionAlmacenamento.md](docs/14_1_Exercicio_XestionAlmacenamento.md) - Exercicio práctico
- [14_1_solucion_Exercicio_XestionAlmacenamento.md](docs/14_1_solucion_Exercicio_XestionAlmacenamento.md) - Solución do exercicio
- [15_DAS_e_Carpetas_Usuarios.md](docs/15_DAS_e_Carpetas_Usuarios.md) - DAS e carpetas de usuarios
- [16_Tarefa-ConfigurarDAS-CarpetasUsuarios.md](docs/16_Tarefa-ConfigurarDAS-CarpetasUsuarios.md) - Configuración práctica
- [21_NAS_almacenamento.md](docs/21_NAS_almacenamento.md) - NAS almacenamiento

### 8. **Perfis Móbiles e Redirección**
- [17_PerfisMobiles.md](docs/17_PerfisMobiles.md) - Perfis móbiles
- [18_Tarefa_Perfis_Mobiles.md](docs/18_Tarefa_Perfis_Mobiles.md) - Tarefa de configuración
- [19_Redireccion_carpetas.md](docs/19_Redireccion_carpetas.md) - Redirección de carpetas
- [20_Tarefa_Redireccion_Carpetas.md](docs/20_Tarefa_Redireccion_Carpetas.md) - Tarefa de redirección

### 9. **NAS (Network Attached Storage)**
- [22_NAS_con_SMB.md](docs/22_NAS_con_SMB.md) - NAS con protocolo SMB
- [23_NAS_con_NFS.md](docs/23_NAS_con_NFS.md) - NAS con protocolo NFS

### 10. **Samba4 como Domain Controller**
- [24_ServidorDC_LinuxSamba4.md](docs/24_ServidorDC_LinuxSamba4.md) - Servidor Domain Controller con Samba4
- [25_UnirEquipoWindows_DCenSamba4.md](docs/25_UnirEquipoWindows_DCenSamba4.md) - Unir Windows a DC Samba4
- [27_ConfigurarRSATenWindows.md](docs/27_ConfigurarRSATenWindows.md) - Configuración de ferramentas RSAT
- [21_unirequipolinuxdominosamba-chatgpt.md](docs/21_unirequipolinuxdominosamba-chatgpt.md) - Unir Linux a dominio Samba

## 🔑 Conceptos Principais

### Active Directory (AD)
Servicio de directorio de Microsoft que xestiona usuarios, equipos e recursos en redes corporativas.

### Domain Controller (DC)
Servidor que autentica usuarios e xestiona políticas de seguridade no dominio.

### Unidades Organizativas (OUs)
Contenedores lóxicos para organizar usuarios, grupos e equipos.

### Políticas de Grupo (GPO)
Mecanismo para aplicar configuracións e restriccións nos equipos do dominio.

### Samba4
Implementación Linux de Active Directory que permite interoperabilidade con Windows.

## 📁 Recursos Adicionais

- **images/** - Imaxes de referencia
- **IMAGESNAS-SMB/** - Imaxes específicas de configuración NAS/SMB

## 📖 Como Usar Este Repositorio

1. Comeza polas guías de **infraestrutura base** para entender o escenario inicial
2. Segue coa **instalación de Windows Server** e **Domain Controller**
3. Aprende a **xestionar o dominio** (OUs, grupos, GPO)
4. Integra **equipos Windows e Linux** no dominio
5. Configura **almacenamento compartido** (DAS, NAS, SMB, NFS)
6. Implementa **perfis móbiles** e **redirección de carpetas**
7. Explora a **alternativa con Samba4** para Linux

## ⚖️ Licencia

Este proxecto está licenciado baixo Creative Commons (CC0 1.0 Universal). Consulta o ficheiro [LICENSE](LICENSE) para máis detalles.

## 👤 Autor/Colaboradores

Documentación de titoriais para sistemas de información en galego.