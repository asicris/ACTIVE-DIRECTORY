---
title: Guía de Creación de infraestrutura Active Directory - VERSIÓNS DE WINDOWS SERVER 2022
author: Cristina Puga Barreiros
date: 2026-05-06
description: Revisión das versións de Windows Server que hai no mercado.
tags:
  - ActiveDirectory
  - management
  - windows
status: published
nav_order: 4

---

# Edicións de Windows Server 2022

Windows Server 2022 preséntase en tres edicións principais, cada unha deseñada para satisfacer diferentes necesidades de escala e virtualización.

## 1. Versións Principais de Windows Server 2022

| Edición | Escenario de Uso Ideal | Licenciamento e Virtualización 
| :--- | :--- | :--- | 
| **Datacenter** | Grandes empresas, centros de datos, entornos de nube híbrida. | Licénciase por núcleo (modelo de licenciamento que vincula o custo do software coa capacidade de procesamento físico real do servidor, mínimo 16 núcleos.). **Virtualización ilimitada** (máquinas virtuais). 
| **Standard** | Empresas medianas, lixeiramente virtualizadas ou con servidores físicos. | Licénciase por núcleo (modelo de licenciamento que vincula o custo do software coa capacidade de procesamento físico real do servidor, mínimo 16 núcleos.). Permite **dúas instancias** de sistema operativo virtualizado (VMs) por licenza. 
| **Essentials** | **Pequenas empresas** e oficinas con necesidades básicas. | Licénciase por servidor (mércase unha única licenza por servidor, independentemente do número de núcleos). As licenzas de cliente están incluídas, xeralmente un número máximo de 25.

## 2. Exemplos de licenza por tipo de empresa

| Edición Recomendada | Exemplo de Empresa (Escenario) | Requisitos Clave | Razoamento da Elección |
| :--- | :--- | :--- | :--- |
| **Essentials** | **PME de 20 Usuarios** (Consultoría Local) | Servidor único, Dominio de Active Directory (AD), Servidor de Ficheiros e Impresión. Sen necesidade de virtualización avanzada. | **Máxima Aforro.** O modelo Essentials inclúe as CALs para os 20 usuarios. Se elixisen Standard, terían un custo adicional moi alto por licenza CAL. |
| **Standard** | **Empresa de 100 Usuarios** (Fábrica/Produción) | Necesita Alta Dispoñibilidade, executa 2 Máquinas Virtuais (VM) por servidor físico (p. ex., un controlador de dominio e un servidor de aplicacións ERP). | **Límite de 25 usuarios superado.** Essentials queda descartado. Standard permite virtualizar dúas VMs, o que xestiona o servizo de aplicacións e o AD de forma illada no mesmo hardware. |
| **Datacenter** | **Provedor de Servizos Xestionados (MSP) ou Gran Corporación** (100+ Usuarios, Alto uso da Nube) | Requiren executar 10-20 Máquinas Virtuais por servidor físico para illar servizos, probar contornas, e xestionar a rede definida por software (SDN). | **Necesidade de Virtualización Ilimitada.** A licenza de Datacenter cobre un número ilimitado de VMs, facéndoa moito máis rendible cando o número de VMs supera as 10-12 por servidor. |