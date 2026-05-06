# SOLUCIÓN - Exercicio comparativa de DISCOS DUROS ACTUAIS

## 1. Comparativa de precios de discos duros físicos

Busca precios dos seguintes compoñentes tendo en conta que son **discos para servidores**:

|Compoñente|Características|Prezo|Imaxen|
|----|----|----|----|
|Disco duro NVME U.2 3TB||||
|Disco duro SATA SSD 3TB||||
|Disco duro SAS SSD 3TB||||
|Disco duro SATA SSD 3TB||||
|Disco duro SATA HDD 3TB||||

---

## SOLUCIÓN:  1. Comparativa de precios de discos duros físicos

Aquí tes a táboa ampliada para o teu exercicio, engadindo as métricas de rendemento máis importantes en servidores: a **Velocidade de transferencia** e os **IOPS** (Operacións de Entrada/Saída por Segundo), que miden a capacidade de traballo real baixo carga.

## 1. Comparativa Técnica e de Prezos: Discos de Servidor (3.84 TB)

| Compoñente | Velocidade (Lectura) | IOPS (Lectura Aleatoria) | Prezo (Est.) | Vantaxe Empresarial |
| --- | --- | --- | --- | --- |
| **NVMe U.2 SSD** | **7.000 MB/s** | **+800.000** | **450 € - 850 €** | **Rendemento crítico.** Conexión directa á CPU sen intermediarios. |
| **SAS SSD (24G) 24Gbps** | **2.400 MB/s** | **~400.000** | **650 € - 1.300 €** | **Alta Dispoñibilidade.** Porto dual (redundancia física). |
| **SATA SSD (Ent.)** | **560 MB/s** | **~95.000** | **380 € - 550 €** | **Compatibilidade.** Mellora económica para servidores vellos. |
| **SAS HDD (12G) 12Gbps** | **250 MB/s** | **~250** | **150 € - 250 €** | **Fiabilidade.** O estándar clásico para datos en quente. |
| **SATA HDD (Ent.)** | **220 MB/s** | **~80** | **120 € - 180 €** | **Capacidade.** Mellor prezo por GB para backups e arquivo. |

**A importancia do Porto Dual en SAS, o único REDUNDANTE NATIVO**

Aínda que o NVMe é máis rápido, un **SAS SSD** permite que dous controladores (servidores) se conecten ao mesmo disco á vez. Se un servidor morre, o outro segue lendo o disco. Isto o NVMe estándar non o fai.
En NVME, podería facerse algo similar, pero a redundancia ten que facela a cabina de discos.

### Resumo para a conclusión do teu exercicio:

* **Para velocidade pura:** NVMe U.2.
* **Para redundancia máxima:** SAS SSD.
* **Para equilibrio custo/velocidade:** SATA SSD.
* **Para gardar moitos datos (copias):** SATA HDD.

---

## 2. Compatibilidade cabinas de discos

Busca información sobre cabinas de discos para servidores de datos:

1. Unha cabina de discos tipo SATA:
   1. pode incluír discos de tipo SAS?
   2. pode incluír discos SATA de tipo SSD e de tipo HDD?
   3. poden funcionar xuntos SATA SSD cun SATA HDD?
   4. Custos aproximados dunha cabina SATA.
2. Unha cabina de discos tipo SAS:
   1. pode incluír discos de tipo SATA?
   2. pode incluír discos de tipo SAS SSD e HDD?
   3. Custos aproximados dunha cabina SAS
3. Funcinamento, nunha cabina compatible, poden funcionar os discos SATA e SAS xuntos?
4. Hai algunha cabina que permita utilizar nvme u.2 ou u.3 xunto con SAS? Canto custaría?

---
## Solución:  2. Compatibilidade cabinas de discos
### 1. Unha cabina de discos tipo SATA:

1. **Pode incluír discos de tipo SAS?** **NON.** O protocolo SATA non entende o set de comandos SCSI nin o conector físico permite o seu axuste.
2. **Pode incluír discos SATA de tipo SSD e de tipo HDD?** **SI.** Podes combinar ambos formatos (2.5" e 3.5") se a cabina ten os adaptadores físicos necesarios.
3. **Poden funcionar xuntos SATA SSD cun SATA HDD?** **SI.** Funcionan sen problema, pero recoméndase separalos en volumes distintos para que o HDD non faga de "pescozo de botella" para o SSD.
4. **Custos aproximados (básica/semi-pro):** Unha cabina externa (JBOD) ou NAS de 4-8 bahías custa entre **250 € e 700 €** (sen discos).

### 2. Unha cabina de discos tipo SAS:

1. **Pode incluír discos de tipo SATA?** **SI.** O estándar SAS é compatible cara atrás co SATA.
2. **Pode incluír discos de tipo SAS SSD e HDD?** **SI.** É o seu uso natural en servidores.
3. **Custos aproximados (profesional):** Unha cabina SAS empresarial (JBOD de 12-24 bahías) comeza nos **1.500 €** e pode superar os **4.000 €** se inclúe controladoras duais de alta dispoñibilidade.

### 3. Funcionamento mixto (SATA e SAS xuntos)

**SI**, nunha cabina SAS poden funcionar ambos ao mesmo tempo. Porén, para un funcionamento óptimo:

* **Nunca os mestures nun mesmo grupo RAID.** Un grupo RAID debe ser ou todo SAS ou todo SATA.
* Usa o **SAS para o rendemento** (Sistema Operativo/Bases de datos) e o **SATA para a capacidade** (Backups/Almacenamento masivo).

### 4. Cabinas para NVMe U.2/U.3 + SAS

**SI**, existen e chámanse cabinas **Tri-Mode**.

* Utilizan un *backplane* universal (U.3) que detecta automaticamente que tipo de disco conectas.
* **Custo:** Son as máis caras. Un servidor ou cabina con soporte total Tri-Mode de última xeración (PCIe 5.0) adoita empezar nos **5.000 € - 8.000 €** para configuracións básicas, xa que requiren controladoras RAID moi avanzadas e cables de alta densidade.

---

### Resumo Final de Compatibilidade

| Tipo de Cabina | Admite SATA? | Admite SAS? | Admite NVMe U.2/U.3? | Perfil de Uso |
| --- | --- | --- | --- | --- |
| **SATA** | ✅ SI | ❌ NON | ❌ NON | Doméstico / PEME barata |
| **SAS** | ✅ SI | ✅ SI | ❌ NON | Servidor Empresarial estándar |
| **Tri-Mode (U.3)** | ✅ SI | ✅ SI | ✅ SI | Alto Rendemento / IA / Big Data |

