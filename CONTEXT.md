# Contexto del Proyecto: SonidoSanPatricio

Documento maestro de especificación técnica, arquitectura, inventario y protocolos operativos del sistema de amplificación del templo parroquial **San Patricio de Las Condes**.

---

## 1. Información General y Alcance

* **Proyecto:** SonidoSanPatricio
* **Institución:** Templo Parroquial San Patricio de Las Condes (Santiago, Chile)
* **Integrador Original de Audio:** Novotic ([www.novotic.cl](https://www.novotic.cl) • Tel: 02-22113310)
* **Fecha de Levantamiento Técnico:** Octubre 2026
* **Propósito del Repositorio:** Centralizar la documentación técnica, mapeo de zonas acústicas, esquemas de conexión, procedimientos de software y guías operativas para sacerdotes, sacristanes, sonidistas y técnicos encargados del mantenimiento.
* **Componente Visual Principal:** `index.html` — Una aplicación web de lectura técnica e interactiva con diagramas vectoriales SVG, optimizada para visualización en pantalla y exportación limpia a PDF/impresión.

---

## 2. Estructura del Repositorio

```plaintext
SonidoSanPatricio/
├── .git/                               # Control de versiones Git
├── index.html                          # Guía interactiva web (Tailwind CSS + SVG + Modo Impresión)
├── README.md                           # Resumen general y accesos rápidos
├── CONTEXT.md                          # Especificación técnica y contexto profundo (este archivo)
├── Guia Audio Templo.txt               # Levantamiento y apuntes técnicos en texto plano
├── Diagrama Audio Rack Templo.jpg      # Fotografía / Esquema del rack físico
├── Parlantes Templo San Patricio.jpg   # Fotografía de instalación de altavoces
└── parlantes templo.jpg                # Registro fotográfico complementario
```

### Tecnologías Implementadas en la Web (`index.html`)
* **HTML5 Semántico:** Estructura organizada por secciones modulares (`#inventario`, `#mapeo`, `#software`, `#operacion`, `#descargas`).
* **Tailwind CSS (CDN):** Estilizado moderno modo oscuro (`slate-950` / `slate-900`) con soporte para `@media print` que cambia automáticamente a fondo blanco y oculta navegación para generar reportes en PDF limpios.
* **SVG Vectorial Integrado:** Diagrama de conexionado entre el rack de audio y la planta arquitectónica del templo (nave central, altar, pilares, bancas y coro).

---

## 3. Arquitectura del Sistema de Audio y Flujo de Señal

### Diagrama de Bloques (Flujo de Señal)

```mermaid
graph TD
    subgraph Captacion ["1. Captación (Presbiterio y Nave)"]
        M1[Micrófono Altar]
        M2[Micrófono Ambón / Lecturas]
        M3[Micrófonos Auxiliares / Sede]
    end

    subgraph Procesamiento ["2. Procesador Central (Rack)"]
        DSP[Biamp Nexia CS<br/>DSP 10x6 Matrix<br/>Filtros anti-feedback, EQ, Delay, Compresión]
    end

    subgraph Potencia ["3. Etapas de Potencia (Crown XTi 1002 - DSP OFF)"]
        AmpA[Amplificador 'A' - Crown XTi 1002<br/>Canal A1 & Canal A2]
        AmpB[Amplificador 'B' - Crown XTi 1002<br/>Canal B1 & Canal B2]
    end

    subgraph Altavoces ["4. Refuerzo Acústico en el Templo"]
        SpkA1[Zona A1: Parlantes Pilares Delanteros -> Hacia la Asamblea]
        SpkA2[Zona A2: Parlantes Pilares Centrales -> Hacia Asamblea Trasera]
        SpkB1[Zona B1: Retorno Altar -> Orientados al Presbiterio]
        SpkB2[Zona B2: Línea Altillo Coro / Entrada -> Actualmente sin salida]
    end

    M1 -->|Euroblock / Balanceado| DSP
    M2 -->|Euroblock / Balanceado| DSP
    M3 -->|Euroblock / Balanceado| DSP

    DSP -->|Salida 1 & 2 L/R| AmpA
    DSP -->|Salida 3 & 4 Aux/Ret| AmpB

    AmpA -->|Canal A1| SpkA1
    AmpA -->|Canal A2 (con Delay compensatorio)| SpkA2
    AmpB -->|Canal B1| SpkB1
    AmpB -->|Canal B2| SpkB2
```

---

## 4. Inventario de Hardware en el Rack

El rack está ubicado en el área técnica del templo. La disposición física de arriba hacia abajo es:

| Posición | Dispositivo | Tipo / Función | Conectividad | Estado y Ajuste |
| :--- | :--- | :--- | :--- | :--- |
| **Unidad Superior** | **Biamp Nexia CS** | Procesador Digital de Señales (DSP) y Matriz 10x6 | Ethernet (TCP/IP RJ-45), Serial RS-232, Euroblock balanceado | `I/O`, `COM`, `STATUS` activos. Actúa como cerebro acústico: aplica filtros paramétricos, supresión de feedback y alineación temporal (delay). |
| **Bandeja Intermedia** | Placa Novotic | Placa de identificación del integrador | N/A | Servicio y soporte original ([novotic.cl](https://www.novotic.cl) - Tel: 02-22113310). |
| **Unidad Media** | **Crown XTi 1002 (Unidad 1 - "A")** | Amplificador de potencia estéreo (2 canales) | Entradas XLR, Salidas Speakon / Bornes, USB Tipo B | Modo `DSP OFF`. Perilla 1 (Izq) = A1; Perilla 2 (Der) = A2. Alimenta la Nave Central. |
| **Unidad Inferior** | **Crown XTi 1002 (Unidad 2 - "B")** | Amplificador de potencia estéreo (2 canales) | Entradas XLR, Salidas Speakon / Bornes, USB Tipo B | Modo `DSP OFF`. Perilla 1 (Izq) = B1 (Retorno Altar); Perilla 2 (Der) = B2 (Altillo Coro). |

---

## 5. Distribución Acústica y Mapeo de Canales

| Canal | Amplificador | Control Físico | Ubicación en el Templo | Cobertura Acústica | Estado Operativo |
| :---: | :---: | :---: | :--- | :--- | :---: |
| **A1** | Crown A | Perilla Izq. (1) | Pilares delanteros de la nave | Asambleas / Bancas delanteras | **Operativo** |
| **A2** | Crown A | Perilla Der. (2) | Pilares centrales de la nave | Bancas intermedias y traseras (con delay compensatorio) | **Operativo** |
| **B1** | Crown B | Perilla Izq. (1) | Pilares delanteros (detrás de A1) | Apuntando hacia el Altar / Retorno de Sacerdotes | **Operativo** |
| **B2** | Crown B | Perilla Der. (2) | Línea hacia altillo del coro (acceso principal) | Retorno del coro | **Sin Salida Acústica** *(Requiere verificación)* |

---

## 6. Estructura de Ganancia y Preguntas Técnicas Clave

### ¿Por qué las perillas físicas de los amplificadores Crown controlan el volumen si el DSP Biamp está encendido?
Es **100% normal y correcto**. El orden del circuito de audio es:
$$\text{[Micrófonos]} \longrightarrow \text{[Biamp Nexia CS]} \longrightarrow \text{[Perillas Crown XTi]} \longrightarrow \text{[Parlantes]}$$

1. **Atenuadores físicos de entrada:** Las perillas de los Crown están situadas al final de la cadena de entrada a la etapa de potencia. Regulan cuánta de la señal preamplificada y procesada por el Biamp entra al transformador de potencia final.
2. **El modo `DSP OFF`:** Desactiva los filtros internos de software del Crown (crossover, EQ interna y delay del amplificador) para no duplicar procesos ni provocar desfases con el Biamp, pero **no deshabilita las perillas analógicas**.

### Recomendación Operativa para la Estructura de Ganancia
* **No manipular diariamente:** Las perillas deben calibrarse en un punto óptimo de presión acústica y mantenerse fijas.
* **Riesgo en A1/A2:** Si se descompensa A1 respecto a A2, se rompe la cobertura uniforme de la nave central.
* **Riesgo en B1 (Retorno Altar):** Si se sube en exceso B1, el sonido de retorno entra a los micrófonos cuello de ganso del altar y desata acoples (retroalimentación / feedback / pitidos).
* **Marcaje:** Se recomienda marcar con una pequeña cinta adhesiva o plumón la posición calibrada de las 4 perillas.

---

## 7. Procedimientos de Conexión y Gestión de Software

### A. Procesador Biamp Nexia CS
* **Software requerido:** *Biamp Nexia Software v3.3* (ejecutable en Windows 10 / 11).
* **Conexión física:** Cable Ethernet Cat5e/Cat6 directo desde el puerto Ethernet del Biamp a la tarjeta de red del computador (o a través de switch local).
* **Parámetros de Red por Defecto:**
  * IP por defecto de fábrica del Nexia: `192.168.1.101`
  * IP estática a configurar en el computador Windows: `192.168.1.105` (o cualquiera entre `.102` y `.254`)
  * Máscara de subred: `255.255.255.0`
  * Puerta de enlace: `192.168.1.1` (o en blanco)
* **Procedimiento para descubrir y respaldar:**
  1. Abrir *Nexia Software*.
  2. Ir a `Tools > Options > Network`, seleccionar la interfaz Ethernet activa y el protocolo **UDP** (permite descubrir el equipo aunque su IP haya sido alterada).
  3. Ir a `File > Network > Connect to Network` y seleccionar el sistema del templo.
  4. Presionar **Connect to System** para volcar la configuración de la memoria flash a la pantalla.
  5. **Obligatorio:** Guardar un respaldo inmediato en formato `.nex` (`File > Save As...`) antes de modificar ningún parámetro.

### B. Amplificadores Crown XTi 1002
* **Software compatible:** *HiQnet Band Manager 2* o *Harman Audio Architect* vía cable USB Tipo A a Tipo B (trasero).
* **Condición de configuración crítica (`DSP OFF`):**
  * Los amplificadores Crown disponen de ecualización y crossover internos, pero **deben permanecer en `DSP OFF`** porque el filtraje, limitación y retardos son procesados íntegramente por el Biamp Nexia CS.
* **Bloqueo / Desbloqueo del Panel Frontal:**
  * Mantener presionados simultáneamente los botones `Prev / Up` + `Next / Down` durante 3 segundos.
* **Restauración a `DSP OFF` manual:**
  * Presionar `Sel/Enter` (destella PRESET) $\rightarrow$ presionar `Sel/Enter` $\rightarrow$ navegar con flechas hasta `DSP OFF` $\rightarrow$ confirmar con `Sel/Enter`.

---

## 8. Protocolos Operativos y Mantenimiento

### Protocolo de Encendido y Apagado
Para evitar picos de corriente transitorios ("pop" o golpes acústicos que dañan conos y diafragmas de agudos):

1. **Secuencia de ENCENDIDO:**
   1. Procesador **Biamp Nexia CS** primero (verificar LEDs verdes `I/O`, `COM`, `STATUS` encendidos).
   2. Amplificador **Crown A** (Público).
   3. Amplificador **Crown B** (Retorno).

2. **Secuencia de APAGADO:**
   1. Apagar **Crown A** y **Crown B** primero.
   2. Apagar fuentes de señal / Biamp Nexia (si se desconecta el rack).

### Códigos de Luces LED Frontales (Crown XTi 1002)
* **Power (Azul):** Alimentación eléctrica 220V conectada.
* **Ready (Verde):** Etapa de salida armada y lista.
* **Signal (Verde intermitente):** Presencia de audio detectable (> -40 dBu).
* **-20 / -10 (Verde / Ámbar):** Nivel de señal nominal a alto.
* **Clip (Rojo):** Saturación / distorsión armónica dañina. Reducir perilla del canal inmediatamente.
* **Thermal (Rojo):** Protección por temperatura alta. Comprobar ventilación forzada y limpieza de filtros antipolvo.

### Diagnóstico del Canal B2 (Coro)
* Hablar por un micrófono del altar y observar el LED `Signal` del Canal 2 en el Amplificador B:
  * Si parpadea en verde: La señal llega al rack; revisar bornes de salida, conector Speakon o cable físico hacia el altillo.
  * Si no parpadea: El canal está deshabilitado o silenciado (*Mute*) dentro de la matriz del software Biamp Nexia.

---

## 9. Enlaces de Descarga y Recursos Oficiales

* **Biamp Nexia Software & Firmware:** [Portal Biamp Cornerstone](https://support.biamp.com/Audia-Nexia/Software-Firmware)
* **Guía Oficial de Conexión Biamp:** [Getting Started with Nexia](https://support.biamp.com/Audia-Nexia/Getting_Started_with_Nexia)
* **Página Oficial Crown XTi 1002:** [Crown Audio XTi 1002 Product Page](https://www.crownaudio.com/en/products/xti-1002)
* **Manual de Usuario Serie XTi en Español (PDF):** [Descargar Manual en Audiovias](https://audiovias.com/descarga/267/crown-manuales/7102/crown-xti-series-manual-de-usuario.pdf)
* **Manual Técnico Serie XTi 2 en Inglés (PDF):** [Crown XTi 2 Series Technical Manual](https://www.bhphotovideo.com/lit_files/85046.pdf)
