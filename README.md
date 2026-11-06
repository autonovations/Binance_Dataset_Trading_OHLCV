# README: Binance — Dataset de Trading (OHLCV)

Este notebook unificado está diseñado para **construir, revisar, exportar y visualizar un conjunto de datos de velas (klines)** como base sólida para estrategias y modelos de Machine Learning aplicados al trading.

El script utiliza exclusivamente los endpoints públicos de datos de mercado de Binance, por lo que **no requiere una API Key** y se encuentra totalmente optimizado para ejecutarse en Google Colab.

---

## Estructura y Contenido del Notebook

El flujo de trabajo del notebook se organiza en las siguientes secciones:

1. **Dependencias**: Instalación e importación de librerías esenciales (como `pandas`, `requests`, `plotly`, `mplfinance` y `tqdm`).
2. **Parámetros**: Celda central de configuración donde se define el símbolo (ej. `BTCUSDT`), el intervalo de tiempo, las fechas de inicio/fin, los ajustes de exportación y las preferencias visuales.
3. **Funciones de API**: Gestión de peticiones HTTP con manejo de reintentos ante límites de tasa (*rate limits*), selección automática de URLs funcionales y descarga paginada de datos.
4. **Descarga**: Proceso de obtención del histórico completo de velas desde la API.
5. **DataFrame y limpieza**: Asignación de tipos de datos numéricos y de fecha (`datetime` en UTC), eliminación de registros duplicados y filtrado de la última vela en caso de estar incompleta.
6. **Control de calidad**: Validación de la integridad de los datos (detección de huecos temporales, valores nulos, precios menores o iguales a cero, inconsistencias en OHLC y volumen nulo).
7. **Vista del DataFrame**: Inspección general mediante `info()`, `head()`, `tail()` y estadísticas descriptivas.
8. **Exportar**: Generación y descarga automatizada de archivos en formato CSV y Excel (incluyendo metadatos detallados en una hoja independiente).
9. **Gráficos básicos**: Visualizaciones interactivas mediante Plotly del precio de cierre y de velas japonesas con volumen.
10. **Features, Indicadores y Split Temporal**: Cálculo de indicadores técnicos (medias móviles, RSI, MACD, bandas de Bollinger, ATR, etc.), establecimiento del target predictivo, división cronológica de los datos (train/val/test) y exportación del dataset analítico final.
11. **Apéndice (opcional)**: Exploración complementaria de los servicios públicos de la API de Binance (`ping`, hora del servidor, `exchangeInfo`, libro de órdenes, etc.).

---

## Requisitos de Ejecución

El notebook está preparado para gestionar sus propias dependencias. En su primera celda de código se ejecuta la instalación automática de los paquetes necesarios en el entorno de Google Colab:

```bash
pip install -q mplfinance openpyxl plotly tqdm
```