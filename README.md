# FZ4038 – Tarea Clase 6 – 2.1: Procesos estocásticos estacionarios y no estacionarios

**Ruido blanco y caminata aleatoria: simulación y aplicación a acciones**

   - **Curso:** Econometría Financiera (FZ4038) · EGADE Business School, Tecnológico de Monterrey
   - **Profesor:** Dr. Raymundo Díaz Robles
   - **Alumno:** Daniel Mondragón Monroy (A01452205)
   - **Fecha:** 8 de Noviembre de 2026

## Objetivo

Reconocer procesos estocásticos estacionarios y no estacionarios a partir del **ruido blanco** y la **caminata aleatoria**, y comprobar si los precios y rendimientos de acciones reales se comportan como esos procesos.

## Contenido del repositorio

| Archivo | Descripción |
|:--|:--|
| `Tarea_Clase_6-2.1_A01452205_FZ4038.html` | Documento final con código, resultados, gráficas e interpretaciones. Se abre en cualquier navegador. |
| `Tarea_Clase_6-2.1_A01452205_FZ4038.ipynb` | Notebook de Python (Google Colab) con los resultados de la corrida. |
| `Tarea_Clase_6-2.1_A01452205_EjercicioClase.xlsx` | Ejercicio de Excel de la guía: ruido blanco con `=ALEATORIO()` y caminata aleatoria acumulada, con sus gráficas. |

## Estructura del análisis

1. **Introducción y objetivo**
2. **Marco conceptual y notación:** proceso estocástico, ruido blanco, caminata aleatoria y sus propiedades.
3. **Parte 1: Ruido blanco y caminata aleatoria simulados**
   - Ejercicio en Excel (captura e interpretación).
   - Réplica en Python y 20 realizaciones (el equivalente a presionar F9).
   - Simulación de Monte Carlo con 10,000 realizaciones para verificar las propiedades: E[Sₜ] = 0, E[Sₜ | Sₜ₋₁] = Sₜ₋₁, Var(Sₜ) = tσ² y Cov(Sₜ, Sₛ) = min(t, s)σ².
4. **Parte 2: Ruido blanco y caminata aleatoria en las acciones seleccionadas**
   - Datos diarios de Yahoo Finance (2 de enero de 2015 al 6 de noviembre de 2026) de 10 acciones del portafolio de HowTheMarketWorks y el ETF USO: AAPL, MSFT, NVDA, GOOGL, JPM, GS, BAC, XOM, CVX, COP y USO.
   - Pruebas de raíz unitaria (ADF y KPSS) sobre el log-precio y el rendimiento.
   - Pruebas de ruido blanco: ACF, Ljung-Box, Ljung-Box sobre rendimientos al cuadrado, ARCH-LM y una prueba de autocorrelación robusta a heteroscedasticidad.
   - Razón de varianzas de Lo y MacKinlay (1988) con estadístico robusto.
   - Comparación visual de una acción real con caminatas aleatorias simuladas.
5. **Conclusiones**
6. **Referencias**

## Principales resultados

- En los 11 activos el **log-precio es no estacionario, I(1)**, y el **rendimiento es estacionario**, igual que la caminata aleatoria y su ruido blanco.
- Al corregir por heteroscedasticidad, **ningún activo muestra autocorrelación significativa en conjunto** en sus rendimientos; solo MSFT y NVDA presentan una ligera reversión de un día, económicamente pequeña.
- Los rendimientos **no son independientes**: los 11 activos tienen efectos ARCH (volatilidad agrupada), con los días extremos concentrados en marzo de 2020.
- Los precios son consistentes con una caminata aleatoria con incrementos no correlacionados pero heteroscedásticos, lo que justifica usar modelos ARIMA con d = 1 y modelos GARCH para la volatilidad en el proyecto final.

## Cómo reproducir

1. Abrir el archivo `.ipynb` en [Google Colab](https://colab.research.google.com) (**File → Upload notebook**).
2. Ejecutar **Runtime → Run all**. El notebook instala `yfinance` y descarga los datos automáticamente; la fecha final está fija para que los resultados sean reproducibles.

## Uso de inteligencia artificial

Para elaborar el código en Python y apoyar la redacción se utilizó Claude (Anthropic) como asistente. Los cálculos se ejecutaron en Google Colab y los resultados e interpretaciones fueron revisados por el alumno.
