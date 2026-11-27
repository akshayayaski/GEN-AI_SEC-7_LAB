# Week 5 – Token Economics: Cost and Rate-Limit Budgeting

## Overview
This project focuses on estimating the token consumption, API cost, and rate-limit requirements of an LLM-powered application before development.

It uses Python to calculate expected input tokens, output tokens, daily and monthly costs, and checks whether the expected traffic fits within the configured API limits and budget.

## Objectives
- Understand input tokens and output tokens.
- Calculate daily and monthly token consumption.
- Estimate API costs using configurable token prices.
- Understand Requests Per Minute (RPM) and Tokens Per Minute (TPM).
- Apply safety margins to usage estimates.
- Check daily and monthly budget limits.
- Generate a budget report with a recommendation.

## Technologies Used
- Python
- python-dotenv
- VS Code

## Project Structure
```text
TokenEconomics/
│
├── .env
├── budget.py
├── test_budget.py
└── requirements.txt
```

## Features
- Token usage estimation.
- Daily and monthly API cost calculation.
- RPM and TPM capacity checking.
- Configurable budget limits.
- Safety margin calculation.
- Automated testing using unittest.
- Go/No-Go recommendation.

## How to Run

1. Create and activate a virtual environment.
2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Configure the values in the `.env` file.
4. Run the budget planner:

```bash
python3 budget.py
```

5. Run automated tests:

```bash
python3 -m unittest test_budget.py
```

## Expected Outcome
The program generates a token economics report showing estimated token usage, daily and monthly costs, RPM/TPM checks, and whether the proposed feature is within the configured budget.

## Conclusion
This practical demonstrates how token economics and rate-limit budgeting help developers estimate LLM application expenses and capacity before implementation.
