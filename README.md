# SpendDNA: Automated Financial Behavioral Intelligence Pipeline

A robust, constraint-driven Python data engineering pipeline that ingests raw, unstructured, multi-format personal banking/UPI text logs, parses irregular transaction streams, isolates extreme financial anomalies, and generates structured behavioral intelligence reports with multi-period predictive budgeting.

---

## The Problem Statement

Modern consumer transaction histories—especially retail UPI and personal banking exports—are notoriously messy, highly transactional, and completely unstructured. 

Standard analytical problems encountered with this data include:
*   **Irregular Formats:** Mixed currency signs (`₹`, `Rs.`), inconsistent commas, missing entries, and chaotic multi-format strings.
*   **Warped Timelines:** Mixed date structures (e.g., matching `2024-01-02` with `02/01/24`) that throw off standard string grouping filters or cause day/month swapping errors.
*   **Semantic Ambiguity:** Descriptions filled with chaotic transaction codes (e.g., `ZOMATO-ORDER-128X`, `SWIGGY-BANGALORE`, `ZERODHA-SIP-MUTUAL`) that require unified contextual extraction.

---

## The Chosen Solution

Instead of taking shortcuts by using heavy external black-box NLP frameworks or highly restricted regular expressions (`re`), this pipeline solves the extraction problem from first principles. 

By building **native data cleaning layers, strict datetime normalization trees, and standard matrix loop aggregations**, the project establishes 100% processing reliability while maintaining a near-zero dependency footprint.

---

## System Architecture: What It Does

The application executes through a multi-stage sequential layout inside a Jupyter Notebook environment:

### 1. Hardened Ingestion & Normalization Layer
*   Safely strips multi-currency layout artifacts without using regex filters.
*   Uses explicit date normalization parsing (`dayfirst=True` / `format='mixed'`) to correctly bridge disparate timeline formats without dropping entries into ghost periods.

### 2. High-Coverage Rule-Based Categorization
*   Implements string-matching lookup sequences to isolate unstructured merchant descriptors.
*   Maps raw streams into clean consumer buckets (`Food Delivery`, `Quick Commerce`, `Investments`, etc.) with **less than 1% transaction slippage** (under 5 unmapped unique vendors).

### 3. Outlier & Statistical Anomaly Isolation
*   Dynamically profiles running baseline category standard deviations.
*   Isolates extreme transaction spikes using customized mathematical Z-score thresholds ($Z \ge 3.0$) to call out severe overhead leaks.

### 4. Behavioral Archetype Classification
*   Calculates relative distribution shares across various spend limits.
*   Programmatically assigns personality profiles (e.g., *The Foodie*, *The YOLO Spender*, *The Investor*) based on logical threshold triggers.

### 5. Multi-Period Predictive Budgeting Engine
*   Extracts chronological historical baseline blocks using pure NumPy array arrays.
*   Applies a rolling 3-month moving average arithmetic model (`np.mean`) to project future spending trends—complying perfectly with strict mathematical dependency constraints.

---

##  Core Reports Generated

###  Target SpendDNA Executive Dashboard
Renders a structured, clean horizontal ASCII metric summary outlining credits, debits, burn velocity, top category shares, vendor order frequencies, and key behavioral insights inside the terminal workspace.

###  Day-of-Week Distribution Profile
Maps absolute spending volume across days of the week, validating baseline variations and computing whether weekend consumer behaviors drastically differ from weekday structures.
