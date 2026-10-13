# Paper Research Notes

## Citation

Hadian, S., Rebmann, A., Korkmaz, A., Berg, G., and Brackmann, U. “ERP Event Logs: A Canonical Form for KPI Time-Series Extraction and Characterization.” arXiv:2610.09903, 2026. The arXiv record states that the paper was accepted in D2AI at IEEE ICDM 2026.

Paper link: https://arxiv.org/abs/2610.09903

## One-sentence summary

The paper converts complicated ERP transaction records into a common event-log format so that business KPIs can be extracted, compared, and forecast using reusable operations.

## Problem

ERP systems store one business process across many normalized relational tables. For example, an order may leave records in order, delivery, billing, and accounting tables. Calculating each KPI therefore requires a different set of joins and timestamp rules.

This creates three practical problems:

1. KPI extraction is expensive to engineer.
2. Queries are difficult to reuse across customers and processes.
3. Comparing business processes becomes difficult when each process is represented differently.

## Proposed representation

The authors use a canonical event log with:

- A case, such as a sales order or purchase order
- An activity, such as creating an order, delivering goods, or clearing an invoice
- A timestamp for each activity
- Optional case-level and event-level attributes

The event log provides a shared vocabulary and structure across customers. After the source-specific mapping is completed once, later KPI calculations can use reusable operations over the event log.

## Business processes

The paper studies two end-to-end processes:

### Order-to-cash

The sales-side process from creating a sales order through delivery, invoicing, and payment clearing.

### Procure-to-pay

The procurement-side process from creating a purchase order through goods receipt, invoice receipt, and payment clearing.

## KPI families

### Volumes

Counts of activities or cases over a period. Examples include order arrivals and completed orders.

### Durations

Time differences between two activities in the same case. Examples include order-to-delivery lead time and purchase-order-to-goods-receipt time.

### Rates

Event counts normalized by an active-case population. Examples include cancellation, price-change, and reversal rates.

## Data and scope

The study uses standardized event logs from hundreds of SAP S/4HANA customers across multiple industries. The observation window is 2017–2026. The original customer transactions are not publicly released because they are proprietary.

The paper reports that the analyzed logs include hundreds of tenants, thousands of cases per tenant, and tens of thousands of events per tenant. KPI series are screened for sufficient coverage before forecasting.

## Forecasting comparison

The paper compares:

- Seasonal-naive forecasting
- ETS with additive trend
- ARIMA
- ARIMA with Fourier terms
- Chronos, a pretrained time-series foundation model

The evaluation uses rolling-origin testing. Models forecast twelve weeks ahead from historical weekly KPI series.

## Evaluation metrics and tests

- MASE: mean absolute scaled error, where lower values are better
- Fraction of series where a model beats the naive baseline
- Cross-correlation for comparing sales and procurement signals
- Wilcoxon tests for selected comparisons
- Holm correction for multiple statistical tests

## Main findings

1. The canonical event-log representation makes KPI extraction reusable across customers and processes.
2. Volumes are generally the easiest KPI family to forecast.
3. Forecastability generally decreases from volumes to durations to rates.
4. Classical models retain an advantage on many volume series.
5. Chronos is competitive on duration and rate series.
6. Procurement lead times are longer than sales-side lead times in the reported comparison.
7. The strength of the relationship between sales and procurement arrivals varies across customers and industries.

## Limitations

- The customer transaction data cannot be released publicly.
- The study does not provide a public benchmark for exact reproduction.
- Some rate families contain relatively few usable series.
- Customized customer fields or codes may not be captured by the shared mapping rules.
- The material-group comparison is only a coarse proxy for shared demand exposure.
- The paper does not perform a sensitivity analysis of all screening thresholds.

## Simple explanation for the presentation

Imagine that every company stores the same business story in a different set of filing cabinets. The paper creates one common timeline for each order: what happened, when it happened, and which order it belonged to. Once every order is represented in that common timeline, questions such as “How many orders arrived?”, “How long did delivery take?”, and “How often were orders cancelled?” can be answered in a consistent way.

## Important visual ideas

1. Many ERP tables converging into one event log.
2. A sample event-log row: case, activity, timestamp.
3. The two business processes: order-to-cash and procure-to-pay.
4. KPI family cards: volume, duration, rate.
5. Forecasting model comparison.
6. A simple chart showing forecastability decreasing from volumes to durations to rates.

## Sources to consult next

- The selected paper: https://arxiv.org/abs/2610.09903
- Process Mining Manifesto: cited as reference 1 in the paper
- Process Mining Handbook: cited as reference 2 in the paper
- IEEE XES event-log standard: cited as reference 4 in the paper
- Chronos time-series foundation model: cited as reference 10 in the paper
