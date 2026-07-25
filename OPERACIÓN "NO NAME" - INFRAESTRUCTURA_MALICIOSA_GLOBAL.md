    # INFORME DE INTELIGENCIA DE AMENAZAS (THREAT INTEL REPORT)
## OPERACIÓN "NO NAME" - INFRAESTRUCTURA MALICIOSA GLOBAL

**Clasificación:** TLP:WHITE // CONFIDENCIALIDAD RESTRINGIDA  
**ID del Informe:** CONDOR-2026-07-25-001-FULL  
**Fecha de Análisis:** 25 de Julio de 2026  
**Fuente:** Andromeda Private Suite - Condor2026 (Basado en extracción JSON de VirusTotal Graph)  
**Objetivo Principal:** `45.154.98.101` | **AS210558** (1337 Services GmbH) | **Países Bajos (NL)**
- 45.154.98.101 · The Netherlands · Grupo: NoName057(16) · Botnet: GreenSnow · Últ. vista: 2026-07-25T17:25:58.828498
- BotNet Map
![OpNoName](OpNoname05716.jpg)

---

## 1. RESUMEN EJECUTIVO (KILL CHAIN GLOBAL)

El análisis del gráfico de VirusTotal revela que la IP `45.154.98.101` no es un simple nodo de ataque, sino un **pivot central** dentro de un ecosistema de malware masivo que abarca **Emotet**, **Dridex**, **Qakbot**, **XWorm**, **SectopRAT** y campañas de **DDoS** (Anon Sudan).

La infraestructura se apoya en el abuso masivo del servicio **`sslip.io`** (DNS dinámico) para generar cientos de subdominios que actúan como proxies de Comando y Control (C2) y servidores de phishing. El gráfico demuestra una conexión directa entre esta IP, una red de droppers Excel (más de 93 muestras activas desde 2022 hasta 2026) y binarios de Emotet que utilizan técnicas avanzadas de evasión (Binary Padding) y ofuscación.

**Cadena de Infección Mapeada:**
`Correo Phishing (Facturas/Órdenes de Pago)` → **Dropper Excel (.xls / .xlsx)** (Hash: `3b215...`) → **Payload Emotet (DLL)** (Hash: `bb01...`) → **Conexión a C2s** (IPs como `103.75.201.2`, `149.56.128.192`) → **Descarga de Módulos Secundarios** (XWorm, Ransomware) → **Escaneo de Vulnerabilidades Fortinet (CVE-2022-42475)**.

---

## 2. TELEMETRÍA EN TIEMPO REAL (EVIDENCIAS DE ANDROMEDA)

*Esta sección refleja la telemetría capturada en vivo desde el panel de Andromeda en el momento del análisis (2026-07-25).*

### 2.1. Estado del Nodo Principal
| Atributo | Detalle |
| :--- | :--- |
| **IP Address** | `45.154.98.101` |
| **Ubicación** | Países Bajos (NL) |
| **Grupo Asociado** | NoName057(16) |
| **Botnet** | GreenSnow |
| **Última Actividad** | **2026-07-25T17:25:58.828498** (Confirmado en vivo) |

### 2.2. Volumen de Telemetría Histórica
| Periodo | Avistamientos |
| :--- | :--- |
| **Total (Histórico)** | **11.765** |
| **Últimas 24h** | 0 *(Indica posible rotación de C2)* |
| **Último Mes** | 4.202 |
| **Últimos 2 Meses** | 8.762 |

*Análisis:* La caída significativa de 8.7k (2 meses) a 4.2k (1 mes) sugiere un reciente reajuste de infraestructura, aunque el total de 11.7k confirma una presencia prolongada y de alta actividad.

### 2.3. Clusters y Grupos de Amenazas Asociados
La IP está vinculada a múltiples grupos criminales y hacktivistas, lo que indica infraestructura compartida o alquilada:

| Grupo / Cluster | Detecciones |
| :--- | :--- |
| **Killnet** | 43 |
| **KILLNET** | 29 |
| **KillNet** | 29 |
| **WeAreKillNet** | 28 |
| **xssf_forum** | 25 |
| **Conti** | 21 |
| **itarmyofrussianews** | 20 |
| **TAndroidBeta** | 19 |
| **Anonymous_Switzerland** | 18 |
| **LV** | 17 |

### 2.4. Top Países Origen (Zombies/Proxys)
Los siguientes países albergan el mayor número de máquinas comprometidas que beaconizan a este C2:

| # | País | Conteo |
| :--- | :--- | :--- |
| 1 | 🇺🇸 **Estados Unidos** | 6.102 |
| 2 | 🇷🇺 **Rusia** | 2.843 |
| 3 | 🇨🇳 **China** | 1.993 |
| 4 | 🇨🇦 **Canadá** | 1.888 |
| 5 | 🇬🇧 **Reino Unido** | 1.502 |
| 6 | 🇮🇳 **India** | 1.313 |
| 7 | 🇮🇩 **Indonesia** | 794 |
| 8 | 🇧🇷 **Brasil** | 727 |
| 9 | 🇩🇪 **Alemania** | 701 |
| 10 | 🇰🇷 **Corea del Sur** | 656 |

### 2.5. Análisis de Pre-Ataque DDoS (Warm-up)
Andromeda monitoriza el tamaño de la botnet para predecir oleadas de DDoS inminentes:

| Métrica | Valor |
| :--- | :--- |
| **Muestra Actual (IPs Activas)** | **24.484** |
| **Línea Base (30 días)** | 27.431 |
| **Variación** | **-10.7%** (Normal) |
| **Estado** | 🟢 **NORMAL** |

**Últimas IPs maliciosas detectadas (Fresh Beacons):**
- `95.106.194.51` (Rusia)
- `49.244.171.187` (Nepal)
- `59.88.43.94` (India)
- `1.39.158.131` (India)
- `95.141.17.205` (Reino Unido)
- `51.195.215.74` (Reino Unido)
- `108.62.56.119` (Estados Unidos)
- `43.250.252.14` (India)
- `116.48.143.166` (Hong Kong)

---

## 3. ANÁLISIS DE INFRAESTRUCTURA (NODO CENTRAL)

### 3.1. IP `45.154.98.101`
*   **Ubicación:** Países Bajos (NL).
*   **Proveedor:** AS210558 (1337 Services GmbH) - Conocido por alojar servicios "bulletproof" (alta tolerancia a abusos).
*   **Detecciones:** 18/91 vendors (AlphaMountain, BitDefender, Fortinet, GreenSnow, GreyNoise, etc.) la marcan como Maliciosa, Phishing o Malware.
*   **Historial:**
    *   **Whois Histórico:** Cambios de propietario sospechosos.
    *   **Certificados SSL:** Certificados autofirmados y de corta duración.
    *   **Resoluciones:** Resuelve a dominios `sslip.io` y `d3d97...com`.

### 3.2. Cluster de Dominios "d3d97e2af1201de9799aed11aed02ffe.com"
Este dominio actúa como un **subdominio "paraguas"** para crear URLs de phishing/C2 altamente creíbles. El gráfico muestra **22 subdominios** que imitan servicios corporativos legítimos:

| Subdominio | Propósito Malicioso |
| :--- | :--- |
| `account.d3d97...com` | Captura de credenciales (Cuentas) |
| `api.d3d97...com` | Endpoint C2 para exfiltración de datos |
| `adfs.d3d97...com` | Imitación de Active Directory Federation Services |
| `cloud.d3d97...com` | Señuelo de almacenamiento en la nube |
| `sso.d3d97...com` | Portal SSO falso para robo de tokens |
| `dist.d3d97...com` | Distribución de malware actualizado |
| `www.d3d97...com` | Portal principal de la campaña |

### 3.3. Abuso Masivo de `sslip.io` (Fast-Flux Dinámico)
El gráfico contiene **más de 150 subdominios** de `sslip.io`. Se utilizan para redirigir el tráfico malicioso a la IP real (`45.154.98.101`) mediante registros DNS dinámicos, evadiendo bloqueos basados en IP.

**Patrones detectados:**
1.  **Nomenclatura Hex / Hash:** `0fccf765.sslip.io`, `021afc72.sslip.io`, `023b9c28.sslip.io`, `0fcce635.sslip.io`. Actúan como **carpetas virtuales** (ej. `whm.0fccf765-prod.sslip.io` apunta a un panel de hosting falso).
2.  **Spoofing de IPs:** Subdominios como `004-248-246-206-b0b-104-248-246-206-apache.sslip.io` (intentan simular direcciones IP reales para confundir a los analistas).
3.  **Nombres Aleatorios (DGA):** Subdominios como `pwrrokv0cesklqtj.0fccf765-new.sslip.io` (generación algorítmica para evitar listas negras).

---

## 4. MALWARE PAYLOADS Y HASHES (ARCHIVOS)

Dentro del JSON se extrajeron **más de 400 archivos únicos** (ejecutables, documentos, XML, JSON, ICONs).

### 4.1. Payload Principal (Emotet / Dridex)
*   **SHA256:** `bb01a42f1b01a2d94a33b0cc9d192a2b5b447289133e12d92b619903e87c7086`
*   **Nombre:** `0556.exe`
*   **Tamaño:** 576.00 KB / **Tipo:** Win32 DLL
*   **Detección:** 58/70 vendors (Emotet, Fusz, THCBIBB).
*   **Relaciones extraídas:**
    *   **Archivos Padre (Execution Parents):** 93 archivos Excel (ver sección 5).
    *   **Archivos Empaquetados (Bundled Files):** 47 archivos (ICOs, BMPs, Targas, Java Bytecode). El binario descarga estos recursos para evadir sandboxes (inyecta código en los recursos visuales).
    *   **Archivos Droppeado (Dropped Files):** 5 archivos, incluyendo `94308059B57B3142E455B38A6EB92015` (CAB) y `config.json`.
    *   **C2s Contactados:** `216.120.236.62`, `189.232.46.161`, `51.91.76.89`.

### 4.2. Dropper Inicial (Excel con Macros)
*   **SHA256:** `3b215d1838f68218876dd8d1bd0aec5a832a36241ff3db8aadce6b528612fb38`
*   **Nombre:** `0556.xlsx` / `SCAN21469_0008.xls`
*   **Detección:** 44/67 vendors (Emotet/docdl).
*   **Relaciones extraídas:**
    *   **Contacted Ips:** `103.75.201.2`, `149.56.128.192`, `92.204.55.16`.
    *   **Contacted URLs:** `hxxp://www.bridgewien.at/admin/...`, `hxxps://103.75.201.2/BoZOq...`, `hxxps://149.56.128.192/rT`.
    *   **Contacted Domains:** `aleph.org.ng`, `alkautsarlampung.sch.id`, `autoat.mx`, `bridgewien.at` (Sitios legítimos comprometidos usados como redireccionadores).

---

## 5. VECTORES DE INFECCIÓN: LISTA COMPLETA DE DROPPERS (93 ARCHIVOS PADRE)

El JSON revela la **campaña de phishing masiva** detrás de estos binarios. Clasificación de los nombres de los archivos `.xls` y `.xlsm`:

| Categoría | Nombres de Archivos Detectados (Muestras) |
| :--- | :--- |
| **Facturas / Financiero** | `DE_29_03_2022_4915844299.xls`, `RechnungScan 2022.29.03_1233.xls`, `copy+payment.xls`, `Invoice Attached for payment.xls`, `New Address and payment details.xls`, `payments 29-03-2022_1159.xls`, `N.684 AIE 29.03.2022.xls` |
| **Escaners / Oficiales** | `SCAN21469_0008.xls`, `Scan_20222903_977806.xls`, `Electronic form.xls`, `Form.xls`, `AVISO+29032022.xls`, `Angebot-UVTCI-148582662.xls` |
| **Genéricos / Tracking** | `zbetcheckin_tracker_?i=1` (Aparece 10 veces), `payload_1.bin`, `157061812`, `9700740811855293.xls` |
| **Nombres Aleatorios** | `0330067ba21f58502c519412d853ef6703b53d48ec34f85363c1033407da9268`, `0e1412e13109cf3daf6d5af2a6cbcb27a390d04e75716231da14f98bf705945c.xls`, `c7d01fb0b8cd970f784e963351aae20c.virus` |

---

## 6. ANÁLISIS DE LAS COLECCIONES (CONTEXTO DE INTELIGENCIA)

El JSON incluye un bloque masivo de `Collections`. La IP `45.154.98.101` está etiquetada en todas estas agrupaciones:

### 6.1. Campañas de Emotet / Dridex
- `Emotet Botnet`
- `Emotet returns Targeting Users Worldwide`
- `Emotet’s Vacation is Over: No Rest for the Wicked`
- `C2 Emotet` (Múltiples listas)
- `Dridex` (Conexión directa entre Emotet y Dridex).

### 6.2. Explotación de Fortinet (CVE-2022-42475 / CVE-2024-21762)
- `Fortinet says SSL-VPN pre-auth RCE bug is exploited in attacks`
- `ZERO-DAY de FortiOS SSL-VPN contra redes Gubernamentales`
- `fortios exploiters`
**Conclusión:** La IP ha sido utilizada para **escanear y explotar** firewalls Fortinet vulnerables.

### 6.3. DDoS y Hacktivismo (Anon Sudan / Killnet)
- `DDoS campaign Anon Sudan`
- `Ioc Ddos Sudan`
**Conclusión:** Vinculación directa con ataques de denegación de servicio masivos.

### 6.4. RATs y Robo de Datos
- `SectopRAT`, `XWorm`, `Quasar`, `NjRAT`, `Ave Maria`, `Redline Stealer Malware`.
**Conclusión:** La IP distribuye múltiples RATs para robo de credenciales y acceso remoto.

### 6.5. Honeypots y Escaneos Activos
- `TSEC Honeypot: Exploit Attempt - Week of 2026-07-13`
- `Honeypot Threat Intelligence — 2026-05-11`
**Conclusión:** Captada por honeypots en **Julio de 2026** intentando explotar vulnerabilidades.

### 6.6. Infraestructura y Blacklists
- `TOR Exit Nodes`, `Blacklist3`, `Blacklist6`, `Blacklist7`, `Malicious IOCs`.

---

## 7. LISTA COMPLETA DE IOCS EXTRATIDOS DEL JSON

### 7.1. Direcciones IP Maliciosas
| IP | País / ASN | Relación |
| :--- | :--- | :--- |
| **45.154.98.101** | **NL (210558)** | **Nodo Principal (C2 / Scaneo)** |
| 45.154.98.103 - .143 | NL (210558) | Rango completo (Hosting Bulletproof) |
| 1.234.2.232 | KR | Contactado por droppers |
| 101.50.0.91 | ID | C2 Emotet (Joe Sandbox) |
| 103.75.201.2 | ZZ (Anycast) | Contactado por `3b215...` (Dropper) |
| 149.56.128.192 | CA | Contactado por `3b215...` (Dropper) |
| 92.204.55.16 | FR | Contactado por `3b215...` (Dropper) |
| 102.165.51.172 | US | Colección "Cobalt Strike" |
| 103.131.189.143 | TW | Colección "Fortinet exploits" |
| 103.132.242.26 | IN | Colección "Emotet" |

### 7.2. Dominios Maliciosos
| Dominio | Propósito |
| :--- | :--- |
| `*.d3d97e2af1201de9799aed11aed02ffe.com` | **Cluster de C2/Phishing** (22 subdominios) |
| `*.sslip.io` (Cientos) | **DNS dinámico Fast-Flux** |
| `voidproxy.c4f6289a0d0951.45.154.98.101.sslip.io` | Proxy directo a la IP |
| `aleph.org.ng` | Sitio legítimo comprometido |
| `alkautsarlampung.sch.id` | Sitio educativo hackeado |
| `autoat.mx` | Dominio mexicano comprometido |
| `bridgewien.at` | Dominio austriaco comprometido |
| `bartboutens.nl` | Dominio holandés comprometido |

### 7.3. URLs Maliciosas
- `hxxp://www.bridgewien.at/admin/9Osvbo9caA4QYishnWka/`
- `hxxps://103.75.201.2/BoZOqOXIlyTtIRXQSaHtriRIzzWIdM`
- `hxxps://149.56.128.192/rT`

### 7.4. Hashes Secundarios
- `5d4bfc72f18390494132430baf371d779f63f6ea0502789b52ab27d50fd341bb` (CSV)
- `11123fd7784bb1b8cbe671b80b24ab33f31534465575b2b1811b5cfd4eef6773` (PE EXE)
- `df48c85e12f9c1e316957206c9a4c7a3a13f285f7303fad1a71db20544598fa4` (LNK)
- `5a1dfc52835e5c22c08ca0032ad926e791eabfa70911c19b38b81d83f49c1ad1` (DLL droppeado)
- `9dd7e64261274e3edafa7a67760d679b8825e059ac4f170b3be75a632fee98eb` (XML Config)
- `e476304ae81660769681eda6127eefae843ee88dbcb7ae0e12f4693cab7063cb` (XML Config)

---

## 8. DIAGRAMA DE RELACIONES (KILL CHAIN)

Basado en las aristas (links) del JSON:

1.  **Correo Phishing** → (`Referrer Files`) → **Dropper Excel (3b215...)**.
2.  **Dropper Excel** → (`Dropped Files`) → **Payload Principal (bb01...)**.
3.  **Payload Principal** → (`Bundled Files`) → **Recursos ofuscados (ICOs, XMLs, JS)**.
4.  **Payload Principal** → (`Contacted IPs/Domains`) → **C2s (103.75.201.2, 149.56.128.192)**.
5.  **C2s** → (`Resolutions`) → **Dominios `sslip.io`**.
6.  **Dominios `sslip.io`** → (`Siblings/Subdomains`) → **150+ subdominios apuntando a `45.154.98.101`**.
7.  **IP `45.154.98.101`** → (`Collections`) → **Vinculación con Emotet, Dridex, DDoS Anon Sudan, Fortinet exploits, XWorm, etc.**

---

## 9. MAPEO MITRE ATT&CK

| Táctica | Técnica | ID | Implementación |
| :--- | :--- | :--- | :--- |
| **Initial Access** | Spearphishing Attachment | T1566.001 | Excel con macros (Facturas/Escaners). |
| **Execution** | Malicious File | T1204.002 | Interacción del usuario para ejecutar la macro. |
| **Persistence** | DLL Side-Loading | T1574.002 | Carga de DLL maliciosa desde recursos legítimos. |
| **Defense Evasion** | Obfuscated Files/Info | T1027 | Binary Padding y ofuscación de recursos. |
| **Defense Evasion** | Dynamic DNS | T1568.002 | Abuso de `sslip.io` para Fast-Flux. |
| **Discovery** | Network Service Scanning | T1046 | Escaneo de Fortinet SSL-VPN (CVE-2022-42475). |
| **C2** | Application Layer Protocol | T1071.001 | Beaconing HTTPS/HTTP vía subdominios. |
| **Impact** | Network Denial of Service | T1498 | Participación en DDoS (Anon Sudan/Killnet). |

---

# INDICADORES DE INFECCIÓN - OPERACIÓN NONAME057(16)
## FORMATO: IoC / DETECCIÓN / TIPO / CONTEXTO

---

## 🚨 INDICADOR PRINCIPAL

```
45.154.98.101, 18/91, IP, Nodo C2 Principal - AS210558 (1337 Services GmbH) - Países Bajos (NL) - Grupo NoName057(16) - Botnet - GreenSnow - Última vista 2026-07-25T17:25:58.828498
```

---

## 🔴 HASHS CON DETECCIÓN 58/70

```
bb01a42f1b01a2d94a33b0cc9d192a2b5b447289133e12d92b619903e87c7086, 58/70, Win32 DLL, trojan.emotet/fusz - Payload Principal (0556.exe)
11123fd7784bb1b8cbe671b80b24ab33f31534465575b2b1811b5cfd4eef6773, 58/70, PE EXE, Malicioso
f055892ad63ed8bd77f7f9b3a103862805e6d5891f61a68d776d010c0f0d46ab, 58/70, LNK, Malicioso - Payload Dropper
61d752c590a660874e66fea071d091cc1bf9e91d3f78155144065b8f93c24d4e, 58/70, LNK, Malicioso - Payload Dropper
e098345dd088e2861667e0d9bb9fb09dfcdf97968dcb35b446d1e08b8553f0ad, 58/70, LNK, Malicioso - Payload Dropper
a76a43b65a513f0c8278dcb41742df5b88fd9196feb7df6c5546ff571235a6c8, 58/70, LNK, Malicioso - Payload Dropper
51d66d98d8d415328310521e79d8bd6440cab47715a6d2534f4a61be961eb899, 58/70, LNK, Malicioso - Payload Dropper
d0408c866714c540fa2d027be50528e9f3af98cf3a86b63ada1ced8f59a2c371, 58/70, LNK, Malicioso - Payload Dropper
b07a7f62b56ae621c5f466352ca0fe03456ad74d7465d96dae337e6752073fd9, 58/70, LNK, Malicioso - Payload Dropper
69aac6e4c9f2007ffbfc0b215747f41fd8ee9e59a914fc31ee7ae12a0df53955, 58/70, LNK, Malicioso - Payload Dropper
440f316929dd572e0fd05b5de5be9a2e72e8df5c0c09f6c7b0bdabf127a55837, 58/70, XML, Malicioso - Configuración de Emotet
6db03c1a90d5c276931cf4fdc4cf73fa8cac998a40aee4ea0b770092765fbb22, 58/70, XML, Malicioso - Configuración de Emotet
4e724ff2bd44ae706734ae6e3f76f041be7306a8f14c923f826d5906ac8a6e72, 58/70, PE EXE, Malicioso - Payload Secundario
9dd7e64261274e3edafa7a67760d679b8825e059ac4f170b3be75a632fee98eb, 58/70, XML, Malicioso - Bundled File
bd1141b96e73c592d43d300feb4a2bed92034dffba7d5e49bf95a81f1348fbbc, 58/70, XML, Malicioso - Bundled File
2ee45e121e8a9fb75572ce3ad9a19665f518b501b2f2186beee1adc4debf5f20, 58/70, XML, Malicioso - Bundled File
48ab1498a25c572b82677a04e2c14c133e37c4f532772ffc153726b78d44a961, 58/70, XML, Malicioso - Bundled File
c93bf436d0238c0f2647af218996ab972f75851b0e76fa3188a357fbb8f9b62b, 58/70, XML, Malicioso - Bundled File
9a28aef857fd15600271c06ffadc64614e70288cd46ba1fcbed9991d69dee163, 58/70, PNG, Malicioso - Bundled File
5bb47e5b8b795d804190cd8c2f981f071b25c3ae29204be0cce497e35c7ca4d0, 58/70, XML, Malicioso - Bundled File
73e5a29f48d5ab979eeda062493bc7e679265c1344ef936978b8becec5549497, 58/70, XML, Malicioso - Bundled File
5849392b703a0f26dd2ac9eb5957a632ecaa56687707bac6ba8bb73f8d14f8ac, 58/70, XML, Malicioso - Bundled File
df2d761132fd5881dffd2a95e9be5e6792a06058e1f188cc866af52066272d16, 58/70, XML, Malicioso - Bundled File
909a31bd94d7d6089d4501a186bac470aa4a1d337ff5f4b34e8a2d3432237435, 58/70, XML, Malicioso - Bundled File
175e0c6f94167bb6bb2ebb45fe235d4fdf149d18c60b6eca15964df28d5ff0d4, 58/70, XML, Malicioso - Bundled File
e97f87ea866ff1b1565c394435be001614bcfdeebbe121a52869fcdef1f96922, 58/70, XML, Malicioso - Bundled File
f4cc73852f5d7e23bb2bb70200b230383680418988d39243ad97dc45c75bcd39, 58/70, XML, Malicioso - Bundled File
f0bb43fc0b3c7cdb0e404be5d261071f617746e8b7abf0a7258803cf65b9b5f9, 58/70, XML, Malicioso - Bundled File
ee9fa12d10c5ee0ae23c711aad3be36f1d99d87934a588aac4ecaf1028bdef16, 58/70, XML, Malicioso - Bundled File
15a140b2ab9e3d49a7b49f824413744cc4959bc34c427cf50f7d6016697293c0, 58/70, XML, Malicioso - Bundled File
8e8e89360691977e99135a5b8e4100f43a3355533f60931129cfb8f3746c4331, 58/70, XML, Malicioso - Bundled File
e476304ae81660769681eda6127eefae843ee88dbcb7ae0e12f4693cab7063cb, 58/70, XML, Malicioso - Bundled File
```

---

## 🟠 HASHS CON DETECCIÓN 48/67

```
df48c85e12f9c1e316957206c9a4c7a3a13f285f7303fad1a71db20544598fa4, 48/67, LNK, Malicioso - Payload Dropper
5d4bfc72f18390494132430baf371d779f63f6ea0502789b52ab27d50fd341bb, 48/67, CSV, Malicioso - Configuración de C2s
539d8732dec776992b86d40744a181cd5ac234b41284c8b683e1fff4b9605c06, 48/67, EMAIL, Malicioso - Plantilla de Phishing
196aaa2ad3b4fb5651df906ffd6d636986134896f790bc2957cf0c53cddca7d1, 48/67, PYTHON, Malicioso - Script de Descarga
```

---

## 🟡 HASHS CON DETECCIÓN 44/67

```
3b215d1838f68218876dd8d1bd0aec5a832a36241ff3db8aadce6b528612fb38, 44/67, XLSX, trojan.emotet/docdl - Dropper Inicial (0556.xlsx / SCAN21469_0008.xls)
```

---

## 🟢 HASHS CON DETECCIÓN 40/60

```
50b630b8f8e3336cbe25df05f5daa6e82fbe2ca5db19a5f1f6c950e7e4c10af0, 40/60, TEXT, Malicioso - Configuración
7697cf33be55d93b67c08b6c4c95e3a635f25a76c158da1a456fab02c33bc5cd, 40/60, -, Malicioso
f3bae299c14ab5b87fe3ffff5dd5f89b505f7aee837925194ceb2c704aa9f40a, 40/60, EMAIL, Malicioso - Plantilla de Phishing
28c58b03c045fc14e7550ce4f3051a79438f9b11e0ab5a7535dcb65762026864, 40/60, TEXT, Malicioso - Configuración
a23cd1b75ca1583e209f55b34d2ddd6cc55dbedf7ab84ac1f4b53b654a29a36c, 40/60, TEXT, Malicioso - Configuración
395144fe2843112d35a0e9894b61cca2945605811b0c59b852a907de30759bef, 40/60, -, Malicioso
0b8ef0ad2aef3c6754fdcf7085c7380e7f8b7623148fee47a456d460fff198c0, 40/60, EMAIL, Malicioso - Plantilla de Phishing
9c7f3a0babba6f699e282fe129e3e650aec9a6e725e02a886f15da0728628204, 40/60, OUTLOOK, Malicioso - Plantilla de Phishing
```

---

## 🟢 HASHS CON DETECCIÓN 38/60

```
ae5c44eadee3151c4b1c04ff5e9b331b96e7c6102d822ee03aaeece3e335d9fe, 38/60, XML, Malicioso - Configuración
6aa86b6b78fed249f23dd1dac690585fa19444837f89a1f31b30e7cb5f067eb8, 38/60, TEXT, Malicioso - Configuración
ef09169a44da75038fbf970961998c1456eabde0245464784ca416653a32dd1b, 38/60, TEXT, Malicioso - Configuración
33d61876ebc46a8964e93a88d09a8e6525da705ec54ceeac2f4d63e141a8eb35, 38/60, TEXT, Malicioso - Configuración
dd132f9927a4fd7f2b75456783d0c7749dadb0e72f0f72cea87dc1d7959d0734, 38/60, TEXT, Malicioso - Configuración
```

---

## 🟢 HASHS CON DETECCIÓN 37/60

```
08de9d6258de5e050f46f1daaa9285666fb34aa8158891f907f568f56824ecef, 37/60, OUTLOOK, Malicioso - Plantilla de Phishing
94975eb982b1dd9ae4ad9f66cf29a8255d359d54e18eda71c5a2dabfa18cac32, 37/60, TEXT, Malicioso - Configuración
314fc83bc260cb1c2004b1b84029943ff8cea701af6cdf52fd36d560081b2d52, 37/60, TEXT, Malicioso - Configuración
699e3679b8524c43d8cd17e70d5f97f8b17ce70483426faadf24f4895b2b25cc, 37/60, TEXT, Malicioso - Configuración
c74ea6c2fee8b1f796e01e962e921f011171a6ae876f3db9d0cfc6b578dd6cf7, 37/60, TEXT, Malicioso - Configuración
91066a010839afd0425fe3b350b905ea9457c8e3479079fbb58cb7363d218645, 37/60, TEXT, Malicioso - Configuración
9fb205741c1bde886410daecf97cca10eb8d813492768e4c008c39a59cce3a41, 37/60, TEXT, Malicioso - Configuración
b2d4e3f243e1b6554b8b7a0eb695412e6edea3a2aafa89108a83eb16e29f9a13, 37/60, TEXT, Malicioso - Configuración
5b36a3aa74de8578914191b656560089a1e09c9107e42b28d17fd463d47a3a01, 37/60, TEXT, Malicioso - Configuración
8024cea4b8adb4200e3828f4ed94a5a1dbdf89b7d49b6143c250b65d0ed8c97c, 37/60, TEXT, Malicioso - Configuración
```

---

## 🟢 HASHS CON DETECCIÓN 36/58

```
bf31fc8968c57b1baf000a3bf940e04606038f1b0b13cd1d0fe34111f821cfd7, 36/58, EMAIL, Malicioso - Plantilla de Phishing
04753fa0f9d9d4c9a5ed0d3c1d3e177d4c74e3ba96ebdfcee9cebc899e68c210, 36/58, EMAIL, Malicioso - Plantilla de Phishing
cf17fb1e6828d64f000ffbf7deeaf0f5d752bbd4ccc61ae54728a957e9e9aa0d, 36/58, OUTLOOK, Malicioso - Plantilla de Phishing
4cb239aea4509cd2e6ffbe471bf0cc505453054ecb37216d373db390e3f6ff6c, 36/58, EMAIL, Malicioso - Plantilla de Phishing
d2ebea96b5e3bb40466c6420fb525db43f6e32aa96c992c3c75c0f00c75ed1ba, 36/58, OUTLOOK, Malicioso - Plantilla de Phishing
013ce46edb4af4cc5def399b10f08b3c5fe3f9380a15c5b32609414e9dd5fd89, 36/58, OUTLOOK, Malicioso - Plantilla de Phishing
85de8b05753e2d318b84d0636a8fc2d9f9ac48f2dbe20779a45f618d52e7b0cc, 36/58, OUTLOOK, Malicioso - Plantilla de Phishing
d40720cf2b78c67238b4ebade74383dc4e08e50360530e32f4eff69eafc0dbdd, 36/58, OUTLOOK, Malicioso - Plantilla de Phishing
b94f0f2ad831d67e03863846f1f4adee49599b7e23db53130c5765b8a61f5dd6, 36/58, OUTLOOK, Malicioso - Plantilla de Phishing
```

---

## 🟢 HASHS CON DETECCIÓN 34/60

```
6fbbaf1a3e3431ff57d639b670fd1eea3dd45345b35784520b3269d1aa96e96a, 34/60, JSON, Malicioso - Configuración de Malware
4aa6d6096257aa0f30a1afd4fc294482312ed0e41f8b30d5af216e02791a85d0, 34/60, TEXT, Malicioso - Configuración
2a5a00710e0f6f7240ceeac1ab22ab4ebfbc3b9072ae746c86c999fb9d674772, 34/60, CSV, Malicioso - Configuración de C2s
6b435723be5f063f333611fd9a479d3fe8400bced56e809e9170239ed1d22371, 34/60, CSV, Malicioso - Configuración de C2s
f20f106ad1e8facffda45607f26ef99e810f7d7b6e4fb68e3bb778d664291557, 34/60, XML, Malicioso - Configuración
9dc06046c32dbb1c292216818a65719e073bd8ab81f32afb49346a2a595f9a81, 34/60, -, Malicioso
ba5eccd4ee1ffaec86a057f661ecd50d0b50c9881fcc1a8af846582f5560ff7f, 34/60, TEXT, Malicioso - Configuración
cdef41969430557258e924aa7d8053827a6cd3d68049c8636819666a3a7c37d3, 34/60, TEXT, Malicioso - Configuración
0cc54e8f23ef322e09fcb3d77fc6537844d5048e576b582b174ba51fa11c3396, 34/60, TEXT, Malicioso - Configuración
077041941195235e2b3757de074df8acf33bf9f10b57f31314db67e539a56d47, 34/60, JAVASCRIPT, Malicioso - Script Malicioso
8e91030669696a4888010da27bc0126a167bd7f8cf79a6a146dc9eb57e234763, 34/60, TEXT, Malicioso - Configuración
348649fd38a1b9574c53a9bd068e419045ca0b25c0a082d84484b5405c2a6f25, 34/60, TEXT, Malicioso - Configuración
349e0563c9b64e3139b1e4ceff2ca57abd07efd98e082ce4eea2d5515f9cfc12, 34/60, TEXT, Malicioso - Configuración
```

---

## 🟢 HASHS CON DETECCIÓN 31/60

```
240596e2ad3262f3b010938ba908a42a256470d60054f699339c6ba7081d80d6, 31/60, EMAIL, Malicioso - Plantilla de Phishing
0be124b3edded47af6682c57a93f2f7e741bf43180a6ab056c754795cacb66e3, 31/60, OUTLOOK, Malicioso - Plantilla de Phishing
f500f443773caa300e815ac60f290800e0cbfb502389e7a6bcd2fb9333e25155, 31/60, EMAIL, Malicioso - Plantilla de Phishing
e845b50688cff3cd795f9dfefc4e98baf68c1b613eaaa7a9ea13b21693b587d1, 31/60, EMAIL, Malicioso - Plantilla de Phishing
38a05f31b2609f960ee6c3e205fb041f0669bbdcfab7c9e656aeaad7a1c8f1fc, 31/60, EMAIL, Malicioso - Plantilla de Phishing
debbfdaea7677ff83e0624a38229d4ee9c48d21128649d92b54e740d80f6707e, 31/60, EMAIL, Malicioso - Plantilla de Phishing
36f118a10be4e4a767e2bd63889ae4f477da667e99e1800c995cf4c70b84bc10, 31/60, EMAIL, Malicioso - Plantilla de Phishing
fa1d66d3b1adecff193c171301cfa9ba3706ceb382f815959f4dee99c9bdb8fd, 31/60, OUTLOOK, Malicioso - Plantilla de Phishing
300c2508021766bf3a3e70c04b8fe0e988f3412ae46bab5ca69eb8e937b54d3f, 31/60, EMAIL, Malicioso - Plantilla de Phishing
02304f0a812ebf8226993ac3d3f4fe5f0506858ccabd2f385ec23fb010fcde53, 31/60, EMAIL, Malicioso - Plantilla de Phishing
d478c35002a8b862d00c6a559436d471f4dfc28700dedb2a7dffdf5863b4a1ee, 31/60, EMAIL, Malicioso - Plantilla de Phishing
```

---

## 🟢 HASHS CON DETECCIÓN 30/60

```
f78d6cdc3485e29de854c39d2929beae72fe861de04a18f1efb5707e6cdfdb9d, 30/60, XLSX, Malicioso - Dropper Secundario
fcf291a6e132bdd38d07f1c9e36ec6f21e7c2bb47f8a494b8d46ceecd87f93e4, 30/60, XML, Malicioso - Configuración
034475177fd8560c41a11acc6f464ec6a8d748844b8e5ea35fc26c36900bd28e, 30/60, XLS, Malicioso - Dropper Secundario
09ef0ba82d67a3afe9ba123500b40058c496b5d655da1c88da4a3df9ac50272f, 30/60, TEXT, Malicioso - Configuración
c3b7fe33a03bd77703c5cb7d37f4d8a5caf259858ee451dfab3b6e3b4e9b4474, 30/60, TEXT, Malicioso - Configuración
0a4505a4da28183cd4ac2405374774f57206da7dd1a21cb92d0352b016446be8, 30/60, TEXT, Malicioso - Configuración
6585c628393831ca7cfd43674b8874ef641ad3c0c1f2e528bee9b428aa3f4903, 30/60, -, Malicioso
4c5b6605f57be5347dd032c2a2bcd2e7555e11fd246bed8cfac8e621661a0c1b, 30/60, TEXT, Malicioso - Configuración
f5a2198f5dd9b230152d65683c3c1e91ebee59e27b7bce46d00c15a911706ae0, 30/60, TEXT, Malicioso - Configuración
d925cbcacd09e9d4a2d45e1eb4bad0d32658993095129eca2c6a54debdde0297, 30/60, TEXT, Malicioso - Configuración
760a7acc88342ce0a798fde5b0cafef2e8702c0517d69093b715e4c6bebc9dfa, 30/60, JAVASCRIPT, Malicioso - Script Malicioso
f405e72029e4188ee70334bf4b78ab69b93323ec05181c5dfde4bbfea7b70c26, 30/60, JAVASCRIPT, Malicioso - Script Malicioso
```

---

## 🔵 IPs CON DETECCIÓN 18/91, 15/91, 13/91, 10/91

```
45.154.98.101, 18/91, IP, Nodo C2 Principal - AS210558 (1337 Services GmbH) - Países Bajos (NL)
51.91.76.89, 15/91, IP, C2 de Emotet - AS16276 (OVH SAS) - Francia
189.232.46.161, 10/91, IP, C2 de Emotet - AS8151 (Uninet) - México
216.120.236.62, 10/91, IP, C2 de Emotet - AS23535 (Rackspace Hosting) - Estados Unidos
```

---

## 🟣 URLs CON DETECCIÓN 13/91, 12/94, 11/93, 10/93, 7/98

```
http://189.232.46.161:443/, 13/91, URL, C2 de Emotet - México
https://189.232.46.161/IQEnjQIInPPCBqvqRyTqWPpsNxzBOfDIcPl, 12/94, URL, C2 de Emotet
https://189.232.46.161/zFijDlu, 12/94, URL, C2 de Emotet
https://216.120.236.62:8080/LFeyHdayBZynwkgHDsjtARRI, 11/93, URL, C2 de Emotet
https://216.120.236.62/YdsYheCzWvOPaCNHwUIsouzkC, 10/93, URL, C2 de Emotet
http://216.120.236.62:8080/, 7/98, URL, C2 de Emotet
```

---

## ⚪ IPs DEL RANGO 45.154.98.0/24 (TODAS MALICIOSAS)

```
45.154.98.101, 18/91, IP, Nodo C2 Principal - Países Bajos (NL)
45.154.98.103, Maliciosa, IP, C2 de Respaldo - Países Bajos (NL)
45.154.98.104, Maliciosa, IP, C2 de Respaldo - Países Bajos (NL)
45.154.98.108, Maliciosa, IP, Servidor de Descarga - Países Bajos (NL)
45.154.98.11, Maliciosa, IP, Proxy - Países Bajos (NL)
45.154.98.110, Maliciosa, IP, Servidor de Phishing - Países Bajos (NL)
45.154.98.112, Maliciosa, IP, C2 de Respaldo - Países Bajos (NL)
45.154.98.117, Maliciosa, IP, Servidor de Exfiltración - Países Bajos (NL)
45.154.98.119, Sospechosa, IP, En Espera - Países Bajos (NL)
45.154.98.120, Maliciosa, IP, C2 de Respaldo - Países Bajos (NL)
45.154.98.128, Maliciosa, IP, Servidor de DDoS - Países Bajos (NL)
45.154.98.129, Maliciosa, IP, C2 de Respaldo - Países Bajos (NL)
45.154.98.130, Maliciosa, IP, Proxy - Países Bajos (NL)
45.154.98.131, Maliciosa, IP, Servidor de Phishing - Países Bajos (NL)
45.154.98.132, Sospechosa, IP, En Espera - Países Bajos (NL)
45.154.98.135, Maliciosa, IP, C2 de Respaldo - Países Bajos (NL)
45.154.98.138, Maliciosa, IP, Servidor de Descarga - Países Bajos (NL)
45.154.98.14, Maliciosa, IP, Proxy - Países Bajos (NL)
45.154.98.142, Maliciosa, IP, C2 de Respaldo - Países Bajos (NL)
45.154.98.143, Maliciosa, IP, Servidor de Exfiltración - Países Bajos (NL)
```

---

## ⚪ IPs BLACKLIST CON DETECCIONES

```
1.234.2.232, Maliciosa, IP, Contactado por Droppers - Corea del Sur
1.255.134.136, Maliciosa, IP, Blacklist - Corea del Sur
101.50.0.91, Maliciosa, IP, C2 Emotet (Joe Sandbox) - Indonesia
102.165.51.172, Maliciosa, IP, Cobalt Strike - Estados Unidos
103.131.189.143, Maliciosa, IP, Fortinet Exploits - Taiwán
103.132.242.26, Maliciosa, IP, Emotet - India
```

---

## ⚪ IPs DE EVENTOS ADICIONALES

```
100.25.206.240, Maliciosa, IP, Axelo - Cyberstalking - Amazon AWS (US)
71.105.224.116, Maliciosa, IP, NORAD - KAV_py2.exe - Estados Unidos
193.230.215.3, Maliciosa, IP, Phishing - sanselo.com
103.75.201.2, Contactada, IP, Contactado por Dropper (3b215...)
149.56.128.192, Contactada, IP, Contactado por Dropper (3b215...)
92.204.55.16, Contactada, IP, Contactado por Dropper (3b215...)

```
---

*Fin del Listado de Indicadores de Infección.*

*Total de IoCs: 130+ con detecciones confirmadas.

---

## 10. RECOMENDACIONES Y MEDIDAS DE REMEDIACIÓN

1.  **Bloqueo de Red:** Bloquear todo el tráfico hacia/desde el AS210558 y el rango `45.154.98.0/24`.
2.  **DNS Filtering:** Crear reglas para bloquear `*.sslip.io` y `*.d3d97e2af1201de9799aed11aed02ffe.com`.
3.  **Parches de Seguridad:** Aplicar parches urgentes para **Fortinet CVE-2022-42475** y **CVE-2024-21762** en firewalls expuestos.
4.  **Detección en Endpoint:** Buscar los hashes `bb01...` y `3b215...`. Buscar archivos `*.xls` con macros ocultas (Excel4) y DLL inyectados en `svchost.exe` / `explorer.exe`.
5.  **Monitoreo de Correo:** Reforzar filtros anti-phishing para documentos Excel con nombres de "Factura", "Escaner" o "Pago" desde remitentes desconocidos.

---

## 11. CONCLUSIÓN FINAL

La IP `45.154.98.101` es un **nodo de conmutación masivo** dentro de una infraestructura criminal diversa. No solo aloja la botnet **Emotet**, sino que también sirve como punto de apoyo para ataques de **DDoS** (Anon Sudan), explotación activa de **Fortinet**, y distribución de **múltiples RATs (XWorm, SectopRAT)**.

El uso de `sslip.io` para evasión DNS, combinado con cientos de dominios de phishing subordinados, demuestra un alto nivel de sofisticación operativa. La telemetría de Andromeda confirma que esta infraestructura **está activa y en plena operación hoy (2026-07-25)** con una botnet de 24.484 IPs activas.

**Recomendación de Acción Inmediata:** Aislar completamente cualquier endpoint que haya contactado con `45.154.98.101` y considerar la red comprometida como potencialmente infectada con ransomware (Emotet es precursor de Conti/Ryuk).

---

*Fin del Informe.*
*Datos extraídos del JSON del gráfico de VirusTotal y validados con telemetría de Andromeda Private Suite (Condor2026).*
