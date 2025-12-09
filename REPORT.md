# Executive Decision Support Dashboard  
_SQL + Python + Dash_

## 1. Purpose and Business Context

This project delivers an executive decision support dashboard that combines data from an internal operational database and an external dataset into a single, interactive view.

The goal is to help business leaders quickly answer questions like:

- Are we on track with sales and profit over time?
- Which departments or segments are driving performance?
- Where are margins strong or weak?
- How do different business factors correlate with results?

Instead of static reports, the dashboard provides an interactive interface where leaders can adjust filters, explore trends, and drill into segments without writing SQL or touching code.

---

## 2. Data Sources

The solution integrates two main data sources:

### 2.1 Internal Operational Database (`d211.db`)

A SQLite database with structured business tables, such as:

- **Sales or transactions data** – revenue, costs, dates, and associated keys
- **Departments or categories** – mapping transactions to business units
- **Customers or accounts** – basic identifiers for grouping and analysis
- **Time-related fields** – dates, periods, or fiscal groupings

This database represents the organization’s internal operational view.

### 2.2 External Dataset (`kaggle_data.csv`)

An external CSV file providing supplemental data, such as:

- Additional metrics or attributes not present in the internal DB  
- Enrichment fields that allow comparison, benchmarking, or segmentation  

This file is loaded with pandas and joined or aligned as needed with the internal data to create a richer analytical model.

---

## 3. Methodology

The overall workflow is implemented in a single Jupyter Notebook (`D211.ipynb`) using Python, SQL, and Dash.

### 3.1 Data Extraction

1. **Connect to SQLite database**  
   Python uses `sqlite3` or SQLAlchemy to connect to `d211.db` and execute SQL queries.

2. **Run advanced SQL queries**  
   SQL is used to:
   - Join related tables  
   - Aggregate data (e.g., total sales, total cost, counts per department or period)  
   - Compute intermediate metrics suitable for reporting

3. **Load CSV data**  
   `kaggle_data.csv` is read into a pandas DataFrame and merged or aligned with the aggregated SQL results when necessary.

### 3.2 Data Preparation

After extraction, pandas handles:

- Cleaning and type conversion (dates, numeric fields)
- Calculating **KPIs**, such as:
  - Total sales  
  - Total profit  
  - Profit margin  
  - Department/segment contributions  
- Structuring DataFrames in a way that maps cleanly into Plotly figures and Dash callbacks.

### 3.3 Visualization & Dashboard Construction

Using Plotly and Dash:

- **Figures** (bar charts, line charts, pie charts, KPIs) are constructed from the prepared DataFrames.
- **Dash layout** defines the structure of the web app:
  - KPI summary row
  - Chart panels
  - Filter controls (dropdowns, sliders, date pickers)
- **Callbacks** link filters to the charts and KPIs so the view updates dynamically based on user selections.

---

## 4. Dashboard Design

The dashboard is organized around a few core views and metrics that support executive decision-making.

### 4.1 KPI Summary

A top section presents key performance indicators, for example:

- Total sales over the selected period
- Total profit
- Average profit margin
- Number of transactions or customers

These KPIs give a quick health check before deeper exploration.

### 4.2 Sales and Profit Trends

A line or combined chart tracks sales and/or profit over time (e.g., by month or quarter):

- Identifies **growth trends** or **declines**
- Highlights **seasonality** or unusual spikes/drops
- Helps answer: “Are we moving in the right direction overall?”

### 4.3 Department or Segment Comparison

A bar chart compares performance across departments, regions, or other business units:

- Shows which segments contribute most to revenue and profit
- Highlights underperforming areas
- Supports resource allocation and strategic focus decisions

### 4.4 Contribution Breakdown

A pie or stacked bar chart shows the proportion of total results attributable to each department/segment:

- Visualizes the **share of business** for each unit
- Helps executives see whether performance is concentrated or diversified

---

## 5. Interactivity and Filters

To avoid static, one-size-fits-all reports, the dashboard includes interactive controls:

- **Date range filter** – limits analysis to a specific time window.
- **Metric filters** – e.g., choose between viewing sales, profit, or margin.
- **Categorical filters** – select departments, regions, or product lines.

These filters are wired into Dash callbacks so that all charts and KPIs update in sync. This allows leadership to ask “what if” questions directly in the dashboard without needing technical support.

---

## 6. Key Insights (Example Use Cases)

While the specific insights depend on the underlying data, the dashboard is built to surface patterns like:

1. **Trend Awareness**  
   Identify whether sales and profit are increasing, plateauing, or declining, and whether margins are improving or being squeezed.

2. **Top and Bottom Performers**  
   Quickly see which departments or segments are consistently strong and which are lagging.

3. **Concentration Risk**  
   Determine whether revenue and profit are overly dependent on a small number of segments.

4. **Impact of Time Windows**  
   Compare performance across different periods (e.g., pre- vs. post-campaign, different seasons, or fiscal years).

These insights give leaders a clearer picture of business performance and where to act.

---

## 7. Recommendations

From a process and tooling perspective, this project supports several recommendations:

1. **Adopt the dashboard as a regular review tool**  
   Use the dashboard in recurring leadership meetings to monitor performance and align decisions with data.

2. **Iterate on KPIs**  
   As leadership questions evolve, adjust the KPIs and visuals to reflect what truly matters (e.g., customer lifetime value, churn, per-segment profitability).

3. **Expand Data Coverage**  
   Integrate more external or internal data sources over time (marketing data, customer satisfaction scores, operational metrics) to deepen the analysis.

4. **Automate Refresh**  
   Move toward automated data refresh and scheduled ETL so that the dashboard always reflects current data without manual intervention.

---

## 8. Limitations and Future Work

### 8.1 Limitations

- The analysis is constrained by the structure and quality of the existing datasets.
- The current dashboard focuses on a core set of metrics; deeper, domain-specific KPIs might still live in separate systems.
- Running the dashboard from a Jupyter Notebook is suitable for development and demonstration, but not yet a full production deployment.

### 8.2 Future Enhancements

- Containerize the Dash app (e.g., with Docker) for easier deployment to servers or cloud platforms.
- Add authentication and role-based access for sensitive business metrics.
- Introduce drill-down pages for specific departments, customers, or products.
- Integrate alerting or anomaly detection to proactively flag unusual changes in key metrics.

---

## 9. Conclusion

This project demonstrates how to:

- Combine **SQL** and **pandas** to pull together data from an internal database and external CSV.
- Transform that data into meaningful **KPIs and visualizations**.
- Deliver an interactive **Dash dashboard** that supports executive decision-making.

By moving beyond static reports to a live, filterable view of the business, leadership gains a clearer, more flexible way to understand performance and make better-informed decisions.
