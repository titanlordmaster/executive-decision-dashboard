# Executive Decision Support Dashboard (SQL + Python + Dash)

This project builds an **executive decision support dashboard** using:

- An internal relational database (`d211.db`)
- An external CSV dataset (`kaggle_data.csv`)
- A Jupyter Notebook (`D211.ipynb`) that combines **advanced SQL**, **pandas**, and **Plotly/Dash** to create interactive business intelligence views. :contentReference[oaicite:0]{index=0}  

The dashboard surfaces key KPIs (profit, sales, margins, customer/department performance) and lets leaders explore business performance through interactive charts and filters.

---

## Objectives

- Integrate multiple data sources (SQL database + CSV) into a single analytics view  
- Use **advanced SQL queries** and Python to prepare data for executive reporting  
- Deliver an interactive dashboard (via **Plotly/Dash**) that supports:
  - Sales and profit trend analysis
  - Departmental performance comparison
  - High-level KPI monitoring for decision makers :contentReference[oaicite:1]{index=1}  

---

## Repository Structure

```text
.
├── D211.ipynb          # Main Jupyter Notebook (data prep + dashboard code)
├── d211.db             # SQLite database with core business tables
├── kaggle_data.csv     # External data source (supplemental BI data)
├── REPORT.md           # Original report
└── README.md           # This file
````

---

## Key Features

### 1. Data Integration & Preparation

* Connects to `d211.db` via SQLAlchemy / sqlite3 for structured operational data
* Loads `kaggle_data.csv` with pandas to enrich the analysis
* Uses SQL + pandas to:

  * Join tables
  * Aggregate metrics (sales, profit, department contributions)
  * Create clean, analysis-ready data frames 

### 2. Interactive Dashboard (Plotly/Dash)

The notebook defines a Dash app that exposes:

* **Sales Performance (Bar Chart)**
  Compares performance across departments or regions. 

* **Profit vs. Sales (Line Graph)**
  Shows trends in profit vs. sales over time to highlight growth, margin compression, or under-performance. 

* **Department Contribution (Pie Chart)**
  Shows each department’s percentage contribution to overall business performance. 

* **Top-level KPIs**
  Displays metrics like profit margin, sales performance, and customer/department KPIs at the top of the dashboard. 

All charts are interactive: hover tooltips reveal exact values and breakdowns. 

### 3. Filters & Controls

The dashboard supports interactive exploration via:

* **Date range filters**
  Focus on specific time windows to see how performance evolves. 

* **Business performance filters**
  Filter by metrics such as profit, sales, customer satisfaction, or department. 

These controls let executives drill into specific segments without touching SQL or code.

---

## Installation & Setup

You can follow the original instructions in `Instructions.pdf`, or use the summary below. 

### 1. Install Anaconda (Recommended)

1. Download and install **Anaconda** (includes Jupyter Notebook) from the official site. 
2. Open **Anaconda Navigator** and launch **Jupyter Notebook**.

(Optional) Create a fresh environment (e.g., Python 3.9):

```bash
conda create -n d211 python=3.9
conda activate d211
```

### 2. Install Required Libraries

From your environment / terminal:

```bash
conda install pandas plotly dash
```

(Or use `pip install pandas plotly dash` if you prefer pip.) 

### 3. Place Data Files

Make sure the following files are in the same folder as `D211.ipynb` (or adjust the paths in the notebook):

* `d211.db`
* `kaggle_data.csv` 

---

## Running the Notebook & Dashboard

1. Start Jupyter in the project folder:

```bash
jupyter notebook
```

2. Open **`D211.ipynb`**.

3. Update any file paths in the notebook if needed, e.g.:

```python
df = pd.read_csv("kaggle_data.csv")
```

4. Run the cells sequentially to:

   * Connect to `d211.db`
   * Load and transform the data
   * Build the figures and KPIs
   * Launch the Dash app 

5. When you run the Dash app cell (typically something like):

```python
app.run_server(debug=True)
```

Jupyter will print a local URL, e.g.:

```text
http://127.0.0.1:8050/
```

Open that URL in your browser to interact with the dashboard. 

---

## Navigating the Dashboard

Once the app is running:

* Use the **date range** and **metric filters** to slice performance by time and business measure. 
* Review **top-level KPIs** at the top of the dashboard for a quick health check. 
* Interpret the charts:

  * Bar chart – compare sales performance across regions/departments
  * Line chart – track profit vs. sales over time
  * Pie chart – see department contribution to overall results 
* Hover over points for detailed tooltips (exact values, percentages, etc.). 

---

## What This Project Demonstrates

* Integrating **SQL databases** and **CSV datasets** into a unified analytics model
* Using **advanced SQL** queries plus pandas to prepare data for executive reporting
* Building a small but realistic **business intelligence dashboard** with Plotly/Dash
* Presenting KPIs and interactive visualizations that support **executive decision making**
* Packaging the whole thing in a **reproducible Jupyter Notebook** workflow

This project shows that beyond AI/LLM systems, I can also design and implement **practical decision-support dashboards** that sit directly on top of real data sources and answer concrete business questions.
