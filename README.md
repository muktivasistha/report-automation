# 📊 Automated Weekly Business Report

An end-to-end Python pipeline that queries business data, computes performance metrics, and automatically emails a styled HTML report to stakeholders every week.

## What it does

- Pulls daily stats from **PostgreSQL** databases using SQLAlchemy
- Computes **Week-over-Week (WoW)** performance by buy source, sell source, and traffic route
- Computes **Year-over-Year (YoY)** monthly profit trends across 8 years
- Applies business logic (partner profit share adjustments, estimated month-end projections)
- Generates **styled HTML tables** with conditional color highlights
- Sends the report via **Gmail SMTP** with a dynamic subject line

## Tech Stack

`Python` · `pandas` · `SQLAlchemy` · `psycopg2` · `premailer` · `smtplib` · `Jupyter`

## Run it locally (no DB needed)

```bash
git clone <repo>
cd <repo>
pip install -r requirements.txt
jupyter notebook report_automation_portfolio.ipynb
```

The notebook runs in **mock data mode** by default — no database or email credentials required.

## Connect real data

1. Copy `.env.example` → `.env`
2. Fill in your PostgreSQL and Gmail credentials
3. In the first cell, set:
   ```python
   USE_MOCK_DATA = False   # use real DB
   SEND_EMAIL    = True    # send real email
   ```

## Environment Variables

| Variable | Description |
|---|---|
| `DB_HOST` | PostgreSQL host |
| `DB_PORT` | PostgreSQL port (default 5432) |
| `DB_NAME_ANALYTICS` | Analytics database name |
| `DB_NAME_MAIN` | Main database name |
| `DB_USER` | Database username |
| `DB_PASSWORD` | Database password |
| `SENDER_EMAIL` | Gmail address to send from |
| `GMAIL_APP_PASSWORD` | Gmail App Password (not your main password) |
| `RECIPIENT_EMAILS` | Comma-separated list of recipients |

> **Note:** Never commit `.env` to git. It's listed in `.gitignore`.

## Output

The notebook saves `email_preview.html` — open it in a browser to see exactly what the email looks like before sending.
