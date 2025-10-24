# Quantum Portfolio Optimization

This project demonstrates a **quantum-inspired approach to portfolio optimization** using Qiskit, a quantum computing framework. The program selects an optimal set of stocks that maximizes return and minimizes risk, leveraging **QAOA (Quantum Approximate Optimization Algorithm)**, with a classical fallback option if the quantum simulation is unavailable.

---

## Table of Contents

* [Overview](#overview)
* [Features](#features)
* [Installation](#installation)
* [Usage](#usage)
* [Configuration](#configuration)
* [How It Works](#how-it-works)
* [Visualizations](#visualizations)
* [Dependencies](#dependencies)
* [License](#license)

---

## Overview

Portfolio optimization is the process of selecting the best mix of assets to **maximize returns while minimizing risk**. This project uses **quantum algorithms** (QAOA) to solve the **Quadratic Unconstrained Binary Optimization (QUBO)** representation of the problem.

The tool can:

* Fetch historical stock data.
* Compute expected returns and covariances.
* Formulate and solve the portfolio optimization problem.
* Display results and generate interactive visualizations.

---

## Features

* Quantum-based portfolio optimization using QAOA.
* Fallback to classical solvers if quantum simulation fails.
* Automatic download of historical stock prices via Yahoo Finance.
* Visualization of:

  * Portfolio allocation
  * Risk-return profile
  * Individual asset returns
  * Correlation matrix
* Flexible configuration for stock symbols, investment budget, and risk aversion.

---

## Installation

Make sure you have Python 3.9+ installed. Then, install the required packages:

```bash
pip install qiskit qiskit-aer qiskit-algorithms qiskit-optimization yfinance matplotlib pandas numpy
```

---

## Usage

1. Clone the repository or download the script.
2. Modify the configuration section in the script (Step 3) with your stocks, budget, and risk preferences.
3. Run the script:

```bash
python quantum_portfolio_optimization.py
```

4. Review the output for optimal portfolio and metrics.
5. Check the generated visualizations for allocation, risk-return profile, and correlations.

---

## Configuration

You can adjust the following parameters in the script:

| Parameter     | Description                                       | Example                          |
| ------------- | ------------------------------------------------- | -------------------------------- |
| `stocks`      | List of stock symbols to include                  | `['AAPL','MSFT','GOOGL','AMZN']` |
| `start_date`  | Start date for historical data                    | `'2022-01-01'`                   |
| `end_date`    | End date for historical data                      | `'2023-01-01'`                   |
| `budget`      | Number of assets to select                        | `2`                              |
| `lambda_risk` | Risk aversion parameter (0 = ignore risk)         | `0.5`                            |
| `qaoa_reps`   | Number of QAOA repetitions for the quantum solver | `3`                              |

---

## How It Works

1. **Download Stock Data:** Historical adjusted closing prices are fetched using Yahoo Finance.

2. **Compute Returns and Covariance:** Daily percentage changes are calculated and annualized.

3. **Formulate Optimization Problem:**
   The problem is formulated as a **Quadratic Program (QP)**:

   * **Objective function:** Maximize returns and minimize risk.
   * **Constraint:** Select exactly `budget` number of assets.

4. **Convert to QUBO:** QP is converted to QUBO suitable for QAOA.

5. **Solve with QAOA:** The quantum algorithm finds the optimal binary selection of assets.

6. **Fallback:** If QAOA fails, a classical NumPy-based solver is used.

7. **Output & Visualization:** Results include selected assets, expected return, volatility, Sharpe ratio, and multiple plots.

---

## Visualizations

The project generates:

* **Portfolio Allocation:** Bar chart of selected assets.
* **Risk-Return Profile:** Scatter plot showing expected return vs. volatility.
* **Individual Asset Returns:** Horizontal bar chart of returns.
* **Correlation Matrix:** Heatmap of correlations among selected assets.

---

## Dependencies

* Python 3.9+
* [Qiskit](https://qiskit.org/)
* numpy
* pandas
* yfinance
* matplotlib

---

## License

This project is licensed under the MIT License.

---

