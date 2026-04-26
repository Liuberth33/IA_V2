# IA_V2 — Sistema de Trading Algorítmico con Inteligencia Artificial

![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)
![XGBoost](https://img.shields.io/badge/XGBoost-ML%20Model-orange?style=flat-square)
![Status](https://img.shields.io/badge/Status-Demo%20Evaluation-yellow?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

Sistema automatizado de generación y ejecución de señales de trading sobre el par **EURUSD** en temporalidad de **5 minutos**, desarrollado de forma independiente como proyecto de Ciencia de Datos aplicada a mercados financieros.

---

## Descripción General

IA_V2 integra un modelo de machine learning (XGBoost) con un motor de ejecución automatizada, filtros de calidad de señal y notificaciones en tiempo real vía Telegram. El sistema opera de forma autónoma, registra cada operación en un log CSV y aplica gestión de riesgo dinámica.

El proyecto se encuentra actualmente en **fase de evaluación en cuenta demo**, acumulando datos reales para validación estadística antes de migrar a cuenta real.

---

## Arquitectura del Sistema

```
IA_V2/
│
├── src/
│   ├── realtime/
│   │   └── run_realtime_for_v2.py    # Generación de señales + Telegram
│   ├── execution/
│   │   └── execution_engine.py       # Motor de ejecución automatizada
│   └── training/
│       └── train_quant_v2.py         # Entrenamiento XGBoost + walk-forward
│
├── data/
│   └── signal_log.csv                # Registro de operaciones
│
└── README.md
```

---

## Tecnologías Utilizadas

| Componente | Tecnología |
|---|---|
| Modelo predictivo | XGBoost |
| Validación | Walk-Forward Validation |
| Lenguaje | Python 3.10+ |
| Notificaciones | Telegram Bot API |
| Par de divisas | EURUSD |
| Temporalidad | M5 (5 minutos) |
| Registro | CSV logging |

---

## Características Principales

- **Modelo XGBoost** entrenado con validación walk-forward para evitar data leakage
- **Filtros de calidad de señal**: spread, ATR y filtro horario
- **Gestión de riesgo dinámica**: RR 1:1.5 con break-even automático a +1.5 pips
- **Ejecución automatizada** vía motor independiente con MetaTrader
- **Notificaciones en tiempo real** por Telegram con detalle de cada señal
- **Logging automático** de operaciones en `signal_log.csv` para análisis posterior

---

## Cómo Ejecutar

```bash
# Clonar el repositorio
git clone https://github.com/liuberth33/IA_V2.git
cd IA_V2

# Instalar dependencias
pip install -r requirements.txt

# Ejecutar el sistema en tiempo real
python -m src.realtime.run_realtime_for_v2 EURUSD
```

---

## Estado Actual del Proyecto

| Métrica | Valor |
|---|---|
| Fase | Evaluación en cuenta demo |
| Operaciones registradas | ~74 (en progreso hacia 250) |
| Winrate aproximado | ~39% |
| Principal variable analizada | Factor de beneficio y comisiones |
| Próximo hito | 250 operaciones → análisis completo |

> **Nota:** No se realizarán cambios al modelo hasta alcanzar 250 operaciones. El objetivo es acumular suficiente muestra estadística antes de optimizar.

---

## Análisis Preliminar

Con ~74 operaciones reales analizadas:
- Winrate cercano al 39%, con profit factor próximo al breakeven
- Las **comisiones** representan el principal drag del sistema
- El filtro ATR bloquea aproximadamente el 68% de las señales de alta confianza — área de mejora identificada para la siguiente iteración

---

## Roadmap

- [x] Modelo XGBoost con walk-forward validation
- [x] Motor de ejecución automatizada
- [x] Filtros de señal (spread, ATR, hora)
- [x] Notificaciones Telegram
- [x] Logging en CSV
- [ ] Alcanzar 250 operaciones en demo
- [ ] Re-análisis completo del modelo
- [ ] Migración a cuenta real (~$100 inicial)
- [ ] Optimización del filtro ATR

---

## Autor

**Liuberth Escalona**
Estudiante de Ciencia de Datos
[LinkedIn](https://www.linkedin.com/in/liuberth-escalona-36a12a37a) | Chile

---

> *Proyecto desarrollado de forma independiente como parte del aprendizaje aplicado en Ciencia de Datos. No constituye asesoría financiera.*

