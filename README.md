
🤖 Inclusive Microtrading Bot: Backtesting and Strategies Based on Periodic Contributions
This is a consolidated Python script, presented as a Jupyter Notebook (Bot_de_Microtrading.ipynb), designed to perform the backtesting of a trading bot focused on the concept of micro-investments or micro-savings (Dollar-Cost Averaging or DCA) combined with technical analysis signals.

Its core objective is to simulate the accumulation of an investment portfolio over time by making periodic, low-amount contributions and executing fractional share transactions based on a defined trading strategy.

🌟 Key Features
Micro-investment Focus: The bot is optimized to simulate purchases of fractional quantities of an asset, making it ideal for inclusive savings and investment programs with small, consistent contributions.

Time-based Backtesting: It allows you to simulate portfolio performance over a specific duration in months with a user-defined monthly contribution (Defaults: $1.0 USD monthly contribution over 12 months).

Multiple Strategies: Offers the flexibility to select between different technical trading strategies to generate the buy/sell signals.

Real Historical Data: Utilizes the popular yfinance library to download genuine historical data for any ticker available on Yahoo Finance (Default: SPY).

Logging and Visualization: Generates a detailed transaction log in a CSV file and visualizes the Portfolio Evolution against the Total Capital Contributed using a chart.

Simulated Dividend Reinvestment (DRIP): Automatically simulates the reinvestment of a small dividend yield (0.1% by default), purchasing more fractional shares.

🛠️ Bot Components (Modular Structure)
The script consolidates three essential modules of any trading system:

1. Portfolio (Portfolio Management)
Function: The main class responsible for tracking the financial status and execution.

Capabilities: Manages cash (cash), fractional holdings (holdings), accepts deposits, executes fractional quantity buy and sell orders, and records the complete transaction history. It also calculates final metrics like Total Return and CAGR.

2. DataLoader (Data Loading)
Function: Handles the connection and retrieval of market data.

Mechanism: Uses the yfinance library to fetch the historical closing prices (Close) within the required date range for the backtest.

3. Strategy (Trading Strategies)
Function: Generates buy or sell signals based on technical analysis indicators.

Configuration: Uses configurable windows for indicators like the fast Moving Average (MA), slow MA, and Relative Strength Index (RSI).

📊 Implemented Strategies
The bot currently supports two popular technical analysis strategies for signal generation:

Name	Parameter	Signal Logic (Buy/Sell)	Explanation
Dual Moving Average (MA Crossover)	--strategy ma	BUY (1): When the fast MA (e.g., 10 days) crosses above the slow MA (e.g., 30 days).	All available cash is invested upon the generation of a buy signal (bullish crossover), indicating a potential uptrend.
Relative Strength Index (RSI)	--strategy rsi	BUY (1): When the RSI (e.g., 14 days) falls below 30 (oversold). SELL (-1): When the RSI rises above 70 (overbought).	The buy signal triggers investment of all cash. The sell signal triggers the liquidation of all asset holdings to realize profits/avoid losses.

Exportar a Hojas de cálculo
🚀 How to Run the Backtest
The backtest is designed to run on a monthly basis, applying the periodic contribution and the corresponding trading signal at the end of each month (resample('ME').last()).

Requirements
You need Python installed along with the following libraries: pandas, matplotlib, yfinance, and numpy.

Command Line Usage
The bot uses argparse for easy configuration. You can modify the simulation parameters via the command line:

Argument	Type	Description	Default
--ticker	str	The asset symbol to analyze (e.g., AAPL, TSLA, BTC-USD).	SPY
--strategy	str	The strategy to use: ma (Dual MA) or rsi (RSI).	ma
--duration	int	The total duration of the backtest in months.	12
--contribution	float	The amount in USD of the fixed monthly contribution.	1.0

Exportar a Hojas de cálculo
Example Execution (using the code as a Python script):

Bash

python single_file_bot.py --ticker MSFT --strategy rsi --duration 24 --contribution 10.0
📈 Output Metrics and Results
Upon completion of the backtest, the bot provides comprehensive results:

Final Metrics printed to console:

Total Capital Contributed: The sum of all monthly contributions.

Final Portfolio Value: The total value at the end of the period (Cash + Value of Holdings).

Total Return: The net financial gain or loss ($).

Transaction Log (CSV File):

A CSV file named trading_log_*.csv containing detailed records for every event: Date, Event (Contribution, Buy, Sell, Reinvestment), Quantity, Price, Portfolio Value, and an Explanation of the signal.

Performance Chart:

A visualization showing the Portfolio Evolution (how its value grew) compared to the Total Capital Contributed (a benchmark of simple savings).

⚠️ Important Note (Disclaimer)
This bot is designed strictly for backtesting and educational/simulation purposes. It is not intended for, and should never be used for, real-time trading.

Simulation results are based on historical data and do not guarantee future returns.

______________________________________________________
🤖 Bot de Microtrading Inclusivo: Backtesting y Estrategias Basadas en Aportaciones Periódicas
Este es un script de Python consolidado, presentado como un Jupyter Notebook (Bot_de_Microtrading.ipynb), diseñado para realizar el backtesting de un bot de trading enfocado en el concepto de micro-inversiones o micro-ahorros (Dollar-Cost Averaging o DCA) combinados con señales de análisis técnico.

Su objetivo es simular la acumulación de un portafolio de inversión a lo largo del tiempo, haciendo aportaciones periódicas de bajo monto y ejecutando transacciones de acciones fraccionarias según una estrategia definida.

🌟 Características Principales
Enfoque en Micro-inversiones: Está optimizado para simular compras de cantidades fraccionarias de un activo, ideal para programas de ahorro e inversión inclusivos.

Backtesting Temporal: Permite simular el desempeño del portafolio durante una duración específica en meses y con una aportación mensual definida por el usuario (por defecto: $1.0 USD de aportación mensual durante 12 meses).

Múltiples Estrategias: Ofrece la flexibilidad de seleccionar entre diferentes estrategias de trading para generar las señales de compra/venta.

Datos Históricos Reales: Utiliza la biblioteca yfinance para descargar datos históricos de cualquier ticker disponible en Yahoo Finance (por defecto: SPY).

Log y Visualización: Genera un registro detallado de todas las transacciones en un archivo CSV y visualiza la Evolución del Portafolio frente al Capital Contribuido mediante un gráfico.

Reinversión de Dividendos (DRIP simulado): Simula automáticamente la reinversión de un pequeño rendimiento de dividendo (0.1% por defecto), comprando más acciones fraccionarias.

🛠️ Componentes del Bot (Estructura Modular)
El script consolida tres módulos clave de un sistema de trading:

1. Portfolio (Gestión de Portafolio)
Función: Clase principal para rastrear el estado financiero.

Capacidades:

Gestiona el efectivo (cash) y las tenencias fraccionarias (holdings).

Permite depositar efectivo (deposit_cash).

Ejecuta órdenes de compra y venta de cantidades fraccionarias.

Registra el historial de transacciones y el valor del portafolio.

Calcula métricas como el Retorno Total y el CAGR (Tasa de Crecimiento Anual Compuesta).

2. DataLoader (Carga de Datos)
Función: Se encarga de la conexión con fuentes de datos de mercado.

Mecanismo: Utiliza la librería yfinance para obtener los datos históricos de precios de cierre (Close) en el rango de fechas requerido para el backtest.

3. Strategy (Estrategias de Trading)
Función: Genera señales de compra o venta basándose en el análisis técnico.

Ventanas: Utiliza parámetros configurables como la ventana de la Media Móvil (MA) rápida (10 días), MA lenta (30 días) y la ventana del RSI (14 días).

📊 Estrategias Implementadas
El bot soporta actualmente dos estrategias:

Nombre	Parámetro	Lógica de la Señal (Compra/Venta)	Explicación
Doble Media Móvil (MA)	--strategy ma	COMPRA (1): Cuando la MA rápida (10 días) cruza por encima de la MA lenta (30 días).	Se invierte todo el efectivo disponible al generarse una señal de compra (cruce alcista).
Índice de Fuerza Relativa (RSI)	--strategy rsi	COMPRA (1): Cuando el RSI (14 días) cae por debajo de 30 (sobreventa). VENTA (-1): Cuando el RSI supera 70 (sobrecompra).	La señal de compra resulta en la inversión de todo el efectivo. La señal de venta resulta en la liquidación de todas las tenencias del activo.

Exportar a Hojas de cálculo
🚀 Cómo Ejecutar el Backtest
El backtest se ejecuta a nivel mensual, aplicando la aportación y la señal de trading al final de cada mes (resample('ME').last()).

Requisitos
Necesitas tener Python instalado junto con las siguientes librerías: pandas, matplotlib, yfinance, numpy.

Uso por Línea de Comandos (o en un entorno interactivo como Jupyter/Colab)
El bot utiliza argparse para la configuración. Puedes modificar los parámetros de la simulación:

Argumento	Tipo	Descripción	Por Defecto
--ticker	str	Símbolo del activo a analizar (e.g., AAPL, TSLA, BTC-USD).	SPY
--strategy	str	Estrategia a utilizar: ma (Doble MA) o rsi (RSI).	ma
--duration	int	Duración total del backtest en meses.	12
--contribution	float	Cantidad en USD de la aportación mensual.	1.0

Exportar a Hojas de cálculo
Ejemplo de ejecución (usando el código como script de Python):

Bash

python single_file_bot.py --ticker MSFT --strategy rsi --duration 24 --contribution 10.0
📈 Métricas de Salida y Resultados
Al finalizar el backtest, el bot proporciona las siguientes métricas y artefactos:

Métricas Finales impresas en consola:

Capital Aportado Total: Suma de todas las aportaciones mensuales.

Valor Final del Portafolio: Valor total al final del período (Efectivo + Valor de Tenencias).

Retorno Total: Ganancia o pérdida neta ($).

Registro de Transacciones (Log File):

Un archivo CSV con el nombre trading_log_*.csv que detalla cada evento: Fecha, Evento (Aportación, Compra, Venta, Reinversión), Cantidad, Precio, Valor del Portafolio y una Explicación de la señal.

Gráfico de Rendimiento:

Una visualización de la Evolución del Portafolio (línea de Valor del Portafolio) comparada con el Capital Contribuido (línea de Capital Contribuido).

⚠️ Nota Importante (Disclaimer)
El bot está diseñado únicamente para backtesting y fines educativos/simulación. No está diseñado ni debe utilizarse para trading real.

Los resultados de la simulación están basados en datos históricos y no garantizan rendimientos futuros.
