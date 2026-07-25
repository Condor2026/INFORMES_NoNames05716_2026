

# INFORME DE INTELIGENCIA DE AMENAZAS (THREAT INTEL REPORT)

## OPERACIÓN "NO NAME" - INFRAESTRUCTURA MALICIOSA GLOBAL

**Clasificación:** TLP:WHITE // CONFIDENCIALIDAD RESTRINGIDA  
**ID del Informe:** CONDOR-2026-07-25-001-FULL  
**Fecha de Análisis:** 25 de Julio de 2026  
**Fuente:** Andromeda Private Suite - Condor2026 (Basado en extracción JSON de VirusTotal Graph)  
**Objetivo Principal:** `45.154.98.101` | **AS210558** (1337 Services GmbH) | **Países Bajos (NL)**
- 45.154.98.101 · The Netherlands · Grupo: NoName057(16) · Botnet: GreenSnow · Últ. vista: 2026-07-25T17:25:58.828498


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
