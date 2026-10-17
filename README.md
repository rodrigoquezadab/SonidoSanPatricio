# SonidoSanPatricio

Guía Técnica y Documentación Integral del Sistema de Audio y Refuerzo Sonoro del **Templo Parroquial San Patricio de Las Condes** (Santiago, Chile).

* **Integrador Original del Rack:** Novotic S.A. ([www.novotic.cl](https://www.novotic.cl) • Tel: 02-22113310)
* **Fecha de Documentación:** Octubre 2026

---

## 📖 Contenido y Estructura del Repositorio

* **[index.html](index.html):** Aplicación web interactiva e imprimible en PDF con:
  * Inventario detallado de hardware (Biamp Nexia CS y Crown XTi 1002 A/B).
  * Visor conmutable entre el **Diagrama de Cableado Oficial en HD** y el **Esquema Vectorial SVG**.
  * Galería fotográfica con selector entre la **Foto Marcada de Terreno** (ubicación de zonas A1 y A2 en pilares) y la **Foto Panorámica Limpia**.
  * Visor Lightbox en pantalla completa para inspección detallada de imágenes.
  * Análisis de la estructura de ganancia y respuesta a por qué las perillas controlan el volumen en modo `DSP OFF`.
  * Guía paso a paso de conexión en Windows para Biamp Nexia Software v3.3 y Crown HiQnet Band Manager 2.
  * Protocolo seguro de encendido/apagado y código de luces LED.
* **[CONTEXT.md](CONTEXT.md):** Especificación técnica profunda, arquitectura de hardware, parámetros de red IP estática, tablas de mapeo y diagnóstico del Canal B2.
* **[Guia Audio Templo.txt](Guia%20Audio%20Templo.txt):** Apuntes y levantamiento técnico original en texto plano.
* **Archivos Multimedia e Infografías:**
  * `Diagrama Audio Rack Templo.jpg`: Infografía arquitectónica oficial de conexión entre el rack y la planta de la nave central.
  * `parlantes templo.jpg`: Fotografía tomada desde el altillo del coro con marcaciones de los altavoces de columna en los pilares (A1 y A2).
  * `Parlantes Templo San Patricio.jpg`: Fotografía panorámica del templo durante ceremonia.

---

## 🛠️ Equipamiento Principal del Rack

| Dispositivo | Unidad | Función Principal | Configuración / Canales |
| :--- | :--- | :--- | :--- |
| **Biamp Nexia CS** | Superior | Matriz DSP 10x6, filtros anti-acople, EQ paramétrica, delays | Conexión Ethernet TCP/IP (IP fábrica: `192.168.1.101`) |
| **Crown XTi 1002 (A)** | Central | Potencia para la asamblea (Nave Central) | Modo `DSP OFF` • Canal A1 (Delantero) / Canal A2 (Centro/Atrás) |
| **Crown XTi 1002 (B)** | Inferior | Potencia para monitoreo y auxiliares | Modo `DSP OFF` • Canal B1 (Retorno Altar) / Canal B2 (Coro) |

---

## 🚀 Visualización Rápida

1. Abre el archivo [index.html](index.html) directamente en tu navegador web.
2. Para generar el dossier técnico en PDF para impresión, presiona el botón **Imprimir / PDF** en la esquina superior derecha.
