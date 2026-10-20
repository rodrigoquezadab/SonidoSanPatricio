# SonidoSanPatricio: Guía Técnica y Operacional Integral

Documentación técnica unificada del sistema de audio y refuerzo sonoro del **Templo Parroquial San Patricio de Las Condes** (Santiago, Chile).

* **Integrador Original del Rack:** Novotic S.A. ([www.novotic.cl](https://www.novotic.cl) • Tel: 02-22113310)
* **Fecha de Actualización:** Octubre 2026
* **Sitio Web de Consulta:** [https://rodrigoquezadab.github.io/SonidoSanPatricio](https://rodrigoquezadab.github.io/SonidoSanPatricio)

---

## 📖 Estructura del Ecosistema de Audio

El sistema abarca 4 bloques operativos interconectados:

1. **Captación y Mezcla Digital (Sacristía):**
   * **Consola Behringer X AIR XR12:** Control remoto vía Ethernet IP `192.168.100.254` mediante *X AIR Edit* en Linux Mint (Escena: *"Rodrigo"*).
   * **Receptor PRO WIRELESS MICROPHONE (4 Canales UHF):**
     * Canal A: 661.85 MHz | Canal B: 630.65 MHz | Canal C: 795.85 MHz | Canal D: 770.85 MHz.
     * Conectado a la entrada TRS de línea CH 09 (`09 4 mic`).
     * **Alimentación:** Cada micrófono de mano utiliza **un par de pilas AA (2 pilas AA por micrófono)**. Total 8 pilas AA para el juego completo.
2. **Conversión y Transmisión USB (Sacristía):**
   * **Interfaz PreSonus Studio 24c:** Conexión USB-C a PC. Recibe envíos auxiliares balanceados `Aux 1` y `Aux 2` (Bus 1 y Bus 2) desde la XR12 para streaming litúrgico limpio y grabación en vivo.
3. **Amplificación Principal del Templo (Rack en Sacristía):**
   * **Procesador DSP Biamp Nexia CS:** Matriz 10x6, filtros anti-feedback, ecualización de sala y compensación temporal por retardo (*delay*).
   * **2x Amplificadores Crown XTi 1002 (en modo `DSP OFF`):**
     * **Crown A (Público Nave Central):** Canal A1 (Pilares delanteros) | Canal A2 (Pilares centrales/atrás con delay).
     * **Crown B (Retornos):** Canal B1 (Monitores de Retorno Altar) | Canal B2 (Posible Retorno Coro - sin salida).
4. **Sistema de Refuerzo Independiente (Cajas Activas Laterales):**
   * **Parlante Activo Exterior Sacristía:** Conectado por cable XLR físico a la segunda bifurcación del cable en "Y" que nace en `MAIN L`.
   * **Parlante Activo Lado Opuesto Altar:** Conectado por enlace inalámbrico de radiofrecuencia (RF) alimentado desde la salida `PHONES` de la XR12 (gobernado por la perilla física `LEVEL` de audífonos).

---

## 📂 Archivos del Repositorio

* **[index.html](index.html):** Aplicación web interactiva completa optimizada para pantallas y exportación limpia a PDF/impresión. Incluye:
  * Diagrama de flujo de señal unificado End-to-End.
  * Mapeo de canales 1 a 12 de la Behringer XR12 (físico vs software).
  * Ficha del sistema de 4 micrófonos UHF y guía de gestión de pilas AA.
  * Ficha de la interfaz PreSonus Studio 24c para streaming USB.
  * Panel de controles traseros del parlante activo exterior.
  * Mapeo fotográfico superpuesto interactivo de los altavoces sobre la foto del templo con Canvas descargable.
  * Directorio técnico de Softwares, Manuales Oficiales (PDF) y Páginas Web separados e independientes por equipo.
  * Protocolo estricto de encendido/apagado y tabla de luces LED.
* **[CONTEXT.md](CONTEXT.md):** Manual técnico maestro exhaustivo con especificaciones de red, arquitectura Mermaid y procedimientos.
* **[Guia Audio Templo.txt](Guia%20Audio%20Templo.txt):** Levantamiento técnico y notas operativas en texto plano.
* **[documentacion_sistema_de_audio_san_patricio.txt](documentacion_sistema_de_audio_san_patricio.txt):** Relevamiento de campo detallado.
* **[Parlante Parroquia San Patricio Manual De Usuario.pdf](Parlante%20Parroquia%20San%20Patricio%20Manual%20De%20Usuario.pdf):** Manual del fabricante de la caja acústica activa.
* **Fotografías y Recursos Gráficos en Alta Resolución:**
  * `Equipos de audio input output.jpg`: Fotografía real del rack de sacristía (XR12, PreSonus 24c y receptor UHF).
  * `Configuracion Inferfaz de Audio.jpg`: Captura de pantalla de la consola virtual X AIR Edit en Linux Mint.
  * `Microfonos inalambricos.jpg`: Los 4 micrófonos UHF en su soporte (2 pilas AA c/u).
  * `Parlante Fuera de Sacristia.jpg`: Panel de conexiones traseras de la caja activa exterior.
  * `Rack Templo San Patricio.jpg`: Gabinete técnico principal (Biamp Nexia CS + 2x Crown XTi).
  * `Diagrama Audio Rack Templo.jpg`: Plano arquitectónico de distribución de audio en la nave central.
  * `Parlantes Templo San Patricio.jpg`: Fotografía panorámica del templo para mapeo interactivo.

---

## ⚡ Reglas Operativas Críticas

1. **Pilas de los Micrófonos Inalámbricos:** Cada micrófono requiere **2 pilas AA** (8 en total). Revisar la carga antes de cada misa dominical y mantener siempre un pack de repuesto sellado en la sacristía.
2. **Volumen del Parlante Exterior:** No subir el fader master de la consola digital para darle más volumen a este parlante, ya que también aumentará el volumen en todo el templo; regúlalo directamente en su perilla trasera `LINE LEVEL` o `VOLUME`.
3. **Parlante Inalámbrico del Altar (PHONES):** Su volumen se calibra con la perilla `LEVEL` en la XR12. **Nunca** activar el botón `Solo` en ningún canal en *X AIR Edit*, ya que silenciaría la mezcla general en los audífonos.
4. **Orden de Encendido:** 1. Consola XR12 + Periféricos -> 2. Biamp Nexia -> 3. Parlantes Activos -> 4. Crown XTi A y B (Al final).

---

## 🚀 Visualización Rápida

1. Abre el archivo [index.html](index.html) directamente en tu navegador web.
2. Para exportar la ficha técnica a PDF, haz clic en el botón superior **Imprimir / PDF**.
