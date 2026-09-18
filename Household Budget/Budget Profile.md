---
title: Budget Profile
tags: [budget, parameters, night-shift]
---
# Budget Profile

**Illustrative business inputs.** Edit the named table using its **Open in the table editor** control. **View ▸ Edit Table** opens the first table. Save the input document, then run the Jobs on [[Household Budget]]; its refreshed views read these saved rows.

## Budgets

| category | monthly |
| --- | --- |
| Housing | 2950 |
| Groceries | 900 |
| Dining | 450 |
| Transport | 420 |
| Utilities | 320 |
| Health | 350 |
| Subscriptions | 120 |
| Shopping | 400 |
| Kids | 1400 |
| Travel | 300 |
| Giving | 200 |

## Rules

| match | category |
| --- | --- |
| PAYROLL | Income |
| TRANSFER TO SAVINGS | Savings |
| RENT | Housing |
| WHOLE FOODS | Groceries |
| TRADER JOE | Groceries |
| SAFEWAY | Groceries |
| COSTCO | Groceries |
| CHIPOTLE | Dining |
| STARBUCKS | Dining |
| BLUE BOTTLE | Dining |
| SWEETGREEN | Dining |
| DOORDASH | Dining |
| CHEVRON | Transport |
| SHELL OIL | Transport |
| UBER | Transport |
| CLIPPER | Transport |
| PG&E | Utilities |
| COMCAST | Utilities |
| VERIZON | Utilities |
| KAISER | Health |
| CVS | Health |
| 24 HOUR FITNESS | Health |
| NETFLIX | Subscriptions |
| SPOTIFY | Subscriptions |
| APPLE.COM/BILL | Subscriptions |
| AMAZON | Shopping |
| TARGET | Shopping |
| LITTLE OAKS | Kids |
| UNITED AIRLINES | Travel |
| AIRBNB | Travel |
| RED CROSS | Giving |

## Settings

| key | value |
| --- | --- |
| currency | USD |
| income_monthly | 9800 |
| savings_target_pct | 20 |

## About these inputs

The one file you edit. The input tables contain the household's plan: the income you expect each month, the savings rate you are aiming for, a budget per category, and the rules that sort a bank statement's lines into those categories. [[Household Budget]] reads the budgets from here each night, and [[Budget Refresh]] uses the rules to categorize whatever statements you drop in `statements/`.

## What each field means

| Field | What it is | Example |
| --- | --- | --- |
| `income_monthly` | What lands in the account in a normal month, after tax. It supplies the planned savings-transfer target; the cash-flow surplus rate uses recorded income. | `9800` |
| `savings_target_pct` | The share of income you mean to keep. | `20` |
| `budgets` | One line per category with its monthly limit. A category with no line is charted with no limit. | Groceries, monthly limit 900 |
| `rules` | One line per merchant pattern. `match` is compared to the statement's description, case-insensitive; the first rule that matches wins. `Income` and `Savings` are the two names the refresh treats specially. | WHOLE FOODS → Groceries |

## Make it yours

- **Add a category.** Add a row in the **Budgets** table; it is in the morning's table when the bound table refreshes.
- **Teach it a merchant.** The dashboard's *Uncategorized* table lists every line no rule caught. Open **Rules** in the Table editor, add the matching rows in priority order, save and run the refresh.
- **Use your own statements.** Export a month from your bank as CSV, with the headers `Date`, `Description`, `Amount`, ISO dates and signed amounts (outflow negative), and put it in `statements/`. Separate debit/credit exports must first be mapped to this format; this definition does not infer bank layouts. The two example statements are made up; delete them when yours are in.

Nothing in this folder is sent anywhere. The refresh reads the statements on this Mac and writes a summary beside them.
