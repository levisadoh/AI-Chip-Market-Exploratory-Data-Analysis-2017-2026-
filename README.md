# AI-Chip-Market-Exploratory-Data-Analysis-2017-2026-
An Excel-first exploratory data analysis of the AI accelerator market, covering 30 chips from 11 vendors across a decade of shipments, pricing, and compute specifications. Built entirely in Excel using live formulas no static, hardcoded outputs.

Overview

This project analyzes the competitive landscape of AI/ML accelerator chips (GPUs, TPUs, NPUs, and custom silicon) from 2017 through 2026, tracking shipment volumes, pricing, revenue, and compute efficiency across vendors including NVIDIA, Google, AMD, Huawei, AWS, Apple, and others.

The workbook is structured as a full analytical pipeline: raw data → feature engineering → distribution diagnostics → pivot-table analysis → correlation analysis, with every number traceable back to a live formula rather than a pasted-in result.

Dataset: 120 chip-year records · 30 unique chips · 11 vendors · 2017–2026

Objectives


Quantify shipment and revenue growth across the AI chip market over time
Identify which vendors and chips have driven that growth
Examine relationships between compute performance, power draw, price, and shipment volume
Diagnose and correct skewed distributions in key financial/volume columns
Surface honest, data-backed observations including where the data falls short


Workbook Structure

SheetPurposeai_chip_marketSource dataset with engineered columns: years_since_launch, log-transforms, skewness diagnostics, and a compute-efficiency metric (TFLOPS/watt)skewnessPaired histograms (raw vs. log-transformed) for shipments, ASP, and revenueshipment revenuePivot table: shipment volume by chip × yearTime-Based TrendsYear-over-year revenue growth and vendor-level revenue breakdownTotal shipment by chipChips ranked by lifetime shipment volume alongside launch dateCompute efficiencyFP16 TFLOPS vs. average TDP (watts) across chipscorrelation matrixPearson correlations across memory, compute, power, price, shipments, and revenuelifecyclePivot view of shipments by chip across years-since-launch

Key Findings

Market growth. Total estimated market revenue grew from roughly $600M in 2020 to a peak of $112.5B in 2025, before easing to $70.7B in 2026. The sharpest inflection was 2023→2024  revenue jumped from $23.6B to $109.8B, a ~4.6x increase in a single year, driven almost entirely by the NVIDIA H100 ramp.

Vendor concentration. NVIDIA accounts for roughly $254.1B in cumulative revenue across the dataset  more than 10x its closest competitor, Google ($23.4B). AMD ($19.2B), Huawei ($11.7B), and AWS ($8.0B) form a distant second tier; Apple, Cambricon, Tenstorrent, and SambaNova each contribute under $1B combined.

Shipment leadership. The NVIDIA H100 alone shipped over 6.05M units across its lifetime more than 60% of total shipments in the tracked subset. Total market shipments rose from 38,182 units in 2020 to a peak of ~3.43M in 2025.

Distribution correction. Shipments, ASP, and revenue are all heavily right-skewed in raw form. A log transform normalized shipments (skew: 5.12 → -0.34) and revenue (5.81 → 0.29) effectively. ASP improved but did not fully normalize (6.08 → -2.86, still left-skewed)  likely due to a cluster of chips priced near $15,000 alongside a few extreme outliers (wafer-scale systems priced over $2M) that a single log transform can't fully smooth out.

Correlation findings. TDP and ASP correlate at 0.995  near-perfect, but likely an artifact of a few extreme high-power, high-price chips rather than a genuine market-wide relationship, since both columns are heavily skewed. Shipments and revenue correlate at 0.974, which is largely definitional (revenue = shipments × price). More notably, raw compute performance (FP16 TFLOPS) is a weak predictor of price (r = 0.11), and memory capacity shows weak correlation (<0.22) with every other variable tested.

Efficiency gains. Compute efficiency (TFLOPS/watt) varies from under 1 on older, high-power chips to over 2 on newer, leaner designs  consistent with real generational efficiency improvements industry-wide.
Honest Limitations


2026 is a partial year. The revenue and shipment dip in 2026 may reflect genuine market cooling or simply an incomplete data year  the workbook does not resolve which.
ASP skew was not fully corrected by a single log transform (see above); a Box-Cox or two-step transform would likely perform better if pursued further.
The shipment revenue pivot reflects a filtered subset (~15 chips, ~10.0M units) rather than the full 30-chip, ~14.1M-unit dataset  noted directly in the sheet so the discrepancy isn't mistaken for an error.
The TDP–ASP correlation (0.995) should not be read causally  it's most plausibly driven by a small number of extreme-value chips rather than a structural market relationship.
Shipment and revenue figures are estimates, not vendor-reported actuals; treat absolute values as directional rather than precise.


Tools


Excel — SUMIFS, AVERAGEIFS, INDEX/MATCH, SUMPRODUCT, pivot tables, and native charting for all analysis; no static/pasted values
Feature engineering and skewness diagnostics computed live within the workbook


Repository Contents

├── ai_chip_market.xlsx    # Full analysis workbook (9 sheets)
└── README.md

Author

Levi Sadoh
Data Analyst | Electrical Engineer
📧 levisadoh@gmail.com
