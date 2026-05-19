# Monte Carlo Portfolio Risk Simulation

Simulacion de Monte Carlo para estimar riesgo financiero de un portafolio de acciones reales. Disenado para correr en Google Colab con GPU.

## Que hace

Genera cientos de miles de escenarios futuros posibles basados en datos historicos reales (via Yahoo Finance) y calcula metricas de riesgo como VaR y CVaR.

## Como usarlo

1. Abre el notebook en Google Colab: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1l2ho1Cb4K6htZMv0CmTWM3teaZ_Fy_or?usp=sharing)
2. Activa la GPU: Entorno de ejecucion > Cambiar tipo de entorno > GPU
3. Corre todas las celdas en orden

## Configuracion

Edita la celda 4 del notebook para cambiar:

| Variable | Por defecto | Descripcion |
|---|---|---|
| TICKERS | AAPL, TSLA, GOOGL, MSFT, AMZN | Acciones a simular |
| WEIGHTS | 30/20/20/15/15% | Pesos del portafolio |
| PORTFOLIO_VALUE | $100,000 | Capital inicial |
| N_SIMULATIONS | 500,000 | Escenarios a generar |
| HORIZON_DAYS | 252 | Dias a proyectar (252 = 1 año bursatil) |
| CONFIDENCE | 0.95 | Nivel de confianza para VaR/CVaR |

## Conceptos clave

**Monte Carlo**: en lugar de resolver el riesgo de forma analitica (imposible para portafolios complejos), se generan miles de escenarios aleatorios y se observa la distribucion resultante.

**Cholesky**: tecnica matematica que permite generar los escenarios aleatorios respetando las correlaciones reales entre activos.

**VaR**: perdida maxima que no se supera en el X% de los escenarios.

**CVaR**: perdida promedio en el peor X% de los casos. Mas conservador que VaR, requerido por Basel III.

## Stack

- `yfinance` — datos historicos de Yahoo Finance
- `cupy` — operaciones numericas en GPU (cae a NumPy si no hay GPU)
- `numpy / pandas` — procesamiento de datos
- `matplotlib / seaborn` — visualizaciones
- `tabulate` — tablas en texto plano

## Estructura

```
monte-carlo-sim/
├── monte_carlo.ipynb   # notebook principal
└── README.md
```
