# QUANTX — Quantitative Financial Intelligence & Strategy Analysis Platform

> **BUILD → BACKTEST → CRASH → EXPLAIN**

QUANTX is an end-to-end quantitative financial intelligence platform designed to help users **analyze assets, build systematic trading strategies, backtest them under realistic execution assumptions, stress-test their robustness, and understand why they succeed or fail**.

Instead of stopping at:

> **"Did this strategy make money?"**

QUANTX asks:

> **"How did the strategy perform, what assumptions drove that performance, and does it survive when those assumptions are challenged?"**

The platform combines quantitative analytics, event-driven backtesting, risk analysis, and systematic stress testing into a unified research workflow.

---

## 🚀 Core Workflow

```text
                    QUANTX
                       │
                       ▼
              ┌─────────────────┐
              │      BUILD      │
              │ Select Asset    │
              │ Select Strategy │
              │ Configure Params│
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │    BACKTEST     │
              │ Event-driven    │
              │ Execution       │
              │ Costs + Slippage│
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │      CRASH      │
              │ Stress Testing  │
              │ Regime Changes  │
              │ Costs / Slippage│
              │ Parameters      │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │     EXPLAIN     │
              │ Strategy        │
              │ Autopsy         │
              │ Attribution     │
              │ Robustness      │
              └─────────────────┘
```

---

# 🎯 Problem

Traditional backtesting can make a strategy look attractive without revealing how fragile that performance may be.

A strategy can appear successful because of:

* favorable market regimes
* unrealistic execution assumptions
* ignored transaction costs
* ignored slippage
* carefully chosen parameters
* favorable starting dates
* a small number of exceptional trading days
* excessive position sizing

QUANTX addresses this by extending traditional backtesting into a broader **strategy robustness analysis workflow**.

---

# 💡 What QUANTX Does

QUANTX provides four major capabilities:

### 1. Market Intelligence

Analyze assets using:

* Price data
* Returns
* Volatility
* Sharpe ratio
* Maximum drawdown
* Rolling performance
* Correlation
* Rolling correlation
* Data health validation

### 2. Strategy Research

Build and evaluate systematic strategies including:

* SMA Crossover
* EMA Trend
* Momentum
* Mean Reversion

### 3. Event-Driven Backtesting

Backtests incorporate realistic execution assumptions including:

* NEXT-OPEN execution
* Transaction costs
* Slippage
* Position sizing
* Buy & Hold benchmark
* Trade-level analysis

### 4. Crash Lab

Instead of only testing the baseline strategy, QUANTX deliberately challenges it through multiple stress scenarios.

---

# 🧠 Crash Lab

Crash Lab is one of the core differentiators of QUANTX.

It evaluates how strategy performance changes when important assumptions are challenged.

## Stress Tests

### 1. Market Regime Stress

Evaluates strategy behavior across different market regimes and conditions.

### 2. Transaction Cost Stress

Measures how sensitive strategy performance is to increasing transaction costs.

### 3. Slippage Stress

Tests whether the strategy remains viable when execution becomes less favorable.

### 4. Parameter Sensitivity

Tests whether small changes to strategy parameters materially change performance.

This helps identify potentially fragile parameter configurations.

### 5. Best-Day Dependency

Measures how much of the strategy's total performance depends on a small number of exceptionally strong days.

### 6. Start-Date Sensitivity

Tests whether the strategy's results depend heavily on a particular historical starting point.

### 7. Position-Size Stress

Evaluates how changing position size affects performance and risk.

---

# 🔬 Strategy Autopsy

After stress testing, QUANTX provides a **Strategy Autopsy** layer to investigate the reasons behind strategy performance.

It examines factors such as:

* Market regime
* Trading costs
* Slippage
* Trade behavior
* Performance attribution
* Robustness
* Risk characteristics

The goal is not simply to produce a performance number, but to provide a clearer explanation of **why the strategy behaved the way it did**.

---

# 📊 Analytics

QUANTX provides a range of quantitative metrics.

## Returns

Measures historical strategy or asset performance.

## Volatility

Measures variability of returns and provides a basic view of risk.

## Sharpe Ratio

Provides a risk-adjusted performance measure.

## Maximum Drawdown

Measures the largest peak-to-trough decline.

## Rolling Performance

Allows performance and risk characteristics to be examined through time.

## Correlation

Measures relationships between assets.

QUANTX also supports:

* Static correlation
* Rolling correlation
* Correlation heatmaps

---

# 📈 Backtesting Engine

QUANTX uses an **event-driven backtesting architecture** rather than simply comparing historical prices.

The engine models:

```text
Market Data
     │
     ▼
Signal Generation
     │
     ▼
Execution Decision
     │
     ▼
NEXT-OPEN Execution
     │
     ├── Transaction Cost
     │
     ├── Slippage
     │
     └── Position Sizing
     │
     ▼
Portfolio Update
     │
     ▼
Performance Metrics
     │
     ▼
Trade Log
```

This provides a more realistic framework for evaluating systematic strategies.

---

# 🧪 Supported Strategies

## SMA Crossover

Uses short-term and long-term Simple Moving Averages to generate trend-following signals.

## EMA Trend

Uses Exponential Moving Averages to capture directional trends.

## Momentum

Attempts to capture continuation in asset price movements.

## Mean Reversion

Attempts to capture reversions toward a historical reference level.

Each strategy exposes configurable parameters through the Strategy Builder.

---

# 🖥️ Application Pages

## Overview

The main QUANTX command center.

Provides:

* Market snapshot
* Data health
* Research workflow
* Key metrics
* Recent analysis

---

## Assets

Provides a multi-asset view containing:

* Asset prices
* Returns
* Volatility
* Risk metrics
* Data health
* Latest available data

---

## Asset Intelligence

Provides deeper analysis for an individual asset.

Includes:

* Price behavior
* Returns
* Volatility
* Drawdown
* Rolling metrics
* Correlation analysis

---

## Compare

Allows multiple assets to be evaluated side-by-side.

Includes:

* Performance comparison
* Risk comparison
* Correlation
* Rolling correlation
* Comparative visualizations

---

## Strategy Builder

Allows users to configure:

* Asset
* Strategy
* Strategy parameters
* Initial capital
* Transaction costs
* Slippage
* Position sizing
* Backtesting configuration

and execute a backtest.

---

## Backtest Result

Displays:

* Strategy performance
* Equity curve
* Buy & Hold benchmark
* Drawdown
* Returns
* Sharpe ratio
* Trade count
* Trade log
* Strategy statistics

---

## Crash Lab

Provides systematic stress testing of a selected strategy.

Includes the seven stress tests and Strategy Autopsy.

---

## Market Lab

Provides broader market-level analysis and quantitative exploration.

---

## Research

Provides a research-oriented workspace for examining quantitative results and strategy behavior.

---

# 🏗️ System Architecture

```text
                         QUANTX
                           │
          ┌────────────────┴────────────────┐
          │                                 │
          ▼                                 ▼
     React Frontend                    FastAPI Backend
          │                                 │
          │                                 │
          ▼                                 ▼
     API Client                         Routers
          │                                 │
          │                         ┌───────┴────────┐
          │                         │                │
          │                         ▼                ▼
          │                    Quant Engine       Data Layer
          │                         │                │
          │                         ▼                ▼
          │                    Backtesting       yFinance
          │                         │                │
          │                         ▼                ▼
          │                    Crash Lab        CSV Fallback
          │                         │
          │                         ▼
          │                   SQLite Database
          │
          ▼
      Recharts / UI
```

---

# 🧱 Project Structure

```text
C:\Q MARK
│
├── backend/
│   │
│   ├── main.py
│   │
│   ├── requirements.txt
│   ├── quantx.db
│   │
│   ├── data/
│   │   └── Static/fallback market datasets
│   │
│   ├── db/
│   │   └── Database configuration and initialization
│   │
│   ├── engine/
│   │   ├── indicators.py
│   │   ├── backtesting/
│   │   ├── strategies/
│   │   └── stress testing logic
│   │
│   ├── models/
│   │   └── Data models / schemas
│   │
│   └── routers/
│       ├── assets.py
│       ├── analytics.py
│       ├── strategies.py
│       ├── backtests.py
│       └── stress_tests.py
│
│
└── frontend/
    │
    ├── package.json
    ├── vite.config.ts
    ├── tsconfig.json
    │
    └── src/
        │
        ├── api/
        │   └── client.ts
        │
        ├── components/
        │   ├── charts/
        │   ├── cards/
        │   ├── tables/
        │   └── UI components
        │
        ├── pages/
        │   ├── OverviewPage.tsx
        │   ├── AssetsPage.tsx
        │   ├── AssetIntelligencePage.tsx
        │   ├── ComparePage.tsx
        │   ├── StrategyBuilderPage.tsx
        │   ├── BacktestResultPage.tsx
        │   ├── CrashLabPage.tsx
        │   ├── MarketLabPage.tsx
        │   └── ResearchPage.tsx
        │
        ├── stores/
        │   └── Zustand state
        │
        ├── hooks/
        │   └── React hooks
        │
        ├── App.tsx
        └── main.tsx
```

> The exact internal structure may evolve as the application is refactored; the architecture above represents the major responsibilities of the system.

---

# 🛠️ Technology Stack

## Frontend

* **React** — Component-based UI
* **TypeScript** — Type-safe frontend development
* **Vite** — Frontend development and build tooling
* **Tailwind CSS** — Styling and responsive layouts
* **Recharts** — Quantitative data visualization
* **Framer Motion** — UI transitions and interaction
* **TanStack React Query** — Server-state and API data management
* **Zustand** — Client-side state management
* **Lucide React** — Interface icons

## Backend

* **Python**
* **FastAPI**
* **Pandas**
* **NumPy**
* **yFinance**

## Database

* **SQLite**

The database schema is designed with portability toward PostgreSQL.

## Data

QUANTX uses:

1. **yFinance** for market data when available
2. **Static CSV fallback data** for reliable demonstration / DEMO MODE

---

# 🔌 API

The FastAPI backend exposes endpoints for:

```text
/api/assets
/api/assets/{symbol}
/api/assets/{symbol}/metrics
/api/analytics/correlation
/api/strategies
/api/backtests
/api/stress-tests
```

The API documentation is automatically available through FastAPI Swagger.

Open:

```text
http://127.0.0.1:8000/docs
```

---

# ⚙️ Installation & Setup

## Prerequisites

Make sure the following are installed:

* Python 3.x
* Node.js
* npm

---

# 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd "Q MARK"
```

---

# 2. Backend Setup

Navigate to the backend:

```powershell
cd backend
```

Create the virtual environment:

```powershell
py -m venv .venv
```

Install dependencies:

```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

Start the FastAPI server:

```powershell
.\.venv\Scripts\python.exe -m uvicorn main:app --reload
```

Backend:

```text
http://127.0.0.1:8000
```

API documentation:

```text
http://127.0.0.1:8000/docs
```

---

# 3. Frontend Setup

Open a second terminal:

```powershell
cd frontend
```

Install dependencies:

```powershell
npm install
```

Start the development server:

```powershell
npm run dev
```

Frontend:

```text
http://localhost:5173
```

---

# ▶️ Running QUANTX

Two terminals are required during development.

### Terminal 1 — Backend

```powershell
cd "C:\Q MARK\backend"
.\.venv\Scripts\python.exe -m uvicorn main:app --reload
```

### Terminal 2 — Frontend

```powershell
cd "C:\Q MARK\frontend"
npm run dev
```

Then open:

```text
http://localhost:5173
```

---

# 🔄 Development Architecture

During development, the frontend communicates with the FastAPI backend through the Vite API proxy.

```text
Browser
   │
   ▼
React + Vite
localhost:5173
   │
   │ /api/*
   ▼
Vite Proxy
   │
   ▼
FastAPI
127.0.0.1:8000
   │
   ├── Quant Engine
   ├── Backtesting
   ├── Crash Lab
   ├── Analytics
   └── Database
```

This keeps frontend API calls consistent during local development.

---

# 🧮 Quantitative Research Pipeline

A typical QUANTX research workflow looks like:

```text
Select Asset
     │
     ▼
Inspect Market Data
     │
     ▼
Analyze Risk & Correlation
     │
     ▼
Select Strategy
     │
     ▼
Configure Parameters
     │
     ▼
Run Backtest
     │
     ▼
Analyze Equity Curve
     │
     ▼
Inspect Drawdown & Trade Log
     │
     ▼
Run Crash Lab
     │
     ▼
Perform Strategy Autopsy
     │
     ▼
Evaluate Robustness
```

---

# 🛡️ Realistic Backtesting Considerations

QUANTX explicitly models several factors that can materially affect strategy results:

### Execution Timing

Trades use **NEXT-OPEN execution** rather than assuming that a signal can be executed at the same price that generated it.

### Transaction Costs

Trading costs are incorporated into the simulation.

### Slippage

Execution prices can be adjusted to model imperfect fills.

### Position Sizing

Strategy exposure can be varied to examine how risk changes with position size.

### Benchmarking

Strategy results can be compared against a **Buy & Hold benchmark**.

These assumptions are intended to make strategy evaluation more realistic than a simple historical signal comparison.

---

# 📊 Visualizations

QUANTX provides interactive quantitative visualizations including:

* Equity Curve
* Drawdown Chart
* Price Chart
* Correlation Heatmap
* Rolling Correlation
* Parameter Sensitivity Heatmap
* Strategy DNA Radar
* Monthly Returns Heatmap
* Stress Test Bar Charts
* Trade Logs

---

# 📈 Example Research Questions

QUANTX can be used to investigate questions such as:

* How does a momentum strategy behave across different assets?
* How sensitive is strategy performance to transaction costs?
* Does a strategy depend heavily on a small number of exceptional days?
* How stable are the chosen parameters?
* Does the strategy remain effective under increased slippage?
* How does changing position size affect drawdown?
* Does performance depend heavily on the selected historical start date?
* How does strategy performance compare with Buy & Hold?
* Which market conditions are associated with strategy performance?

---

# ⚠️ Limitations

QUANTX is a **research and educational platform**, not a financial advisory system.

Backtested performance does not guarantee future results.

Important limitations include:

* Historical data may not represent future market behavior.
* Market data availability depends on the underlying provider.
* Static fallback datasets may be used in DEMO MODE.
* Backtests cannot fully reproduce real-world market microstructure.
* Slippage and transaction-cost assumptions are approximations.
* Stress tests reveal sensitivity but cannot predict future market events.

QUANTX should therefore be used as a **research and strategy-analysis tool**, not as a guarantee of trading performance.

---

# 🔮 Future Improvements

Potential future extensions include:

* PostgreSQL production deployment
* Additional asset classes
* Portfolio-level optimization
* More technical indicators
* Additional strategy families
* Walk-forward validation
* Monte Carlo simulations
* Portfolio optimization
* Advanced regime detection
* Paper trading integration
* Broker/API integration
* Authentication and multi-user workspaces
* Cloud deployment
* Experiment tracking
* Strategy versioning

---

# 👥 Project Philosophy

QUANTX is built around a simple principle:

> **A strategy should not only be tested when conditions are favorable. It should be challenged when its assumptions are under pressure.**

That is why the platform goes beyond:

```text
BACKTEST
```

and extends into:

```text
BACKTEST → CRASH → EXPLAIN
```

---

# 📌 Project Status

**Status: Complete / Functional Prototype**

Core functionality implemented:

* [x] Multi-asset analytics
* [x] Market data layer
* [x] Data health validation
* [x] Quantitative indicators
* [x] Strategy engine
* [x] Event-driven backtesting
* [x] Transaction costs
* [x] Slippage
* [x] Buy & Hold benchmark
* [x] Strategy Builder
* [x] Backtest Results
* [x] Crash Lab
* [x] Seven stress tests
* [x] Strategy Autopsy
* [x] Correlation analysis
* [x] Rolling analytics
* [x] Interactive charts
* [x] React frontend
* [x] FastAPI backend
* [x] SQLite database
* [x] CSV fallback / DEMO MODE
* [x] Responsive interface

---

# 📄 License

Add the appropriate license for your repository.

---

## QUANTX

**BUILD → BACKTEST → CRASH → EXPLAIN**

A quantitative research platform for understanding not only **how a strategy performs**, but also **how robust that performance is when its assumptions are challenged**.
