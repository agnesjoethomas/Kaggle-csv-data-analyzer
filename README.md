# CSV Data Analyzer (n8n Workflow)

An automated, low-code data analysis tool built using **n8n**. This workflow allows users to upload any CSV dataset through a web form and instantly generates a summary report containing key statistical metrics, missing value counts, and structural insights.

---

## Features

- **Form Trigger Upload**: Simple interface for uploading CSV files directly.
- **Data Parsing**: Automatically extracts and handles CSV contents.
- **Data Quality Assessment**:
  - Total row and column counts.
  - Missing value counts per column.
  - Duplicate row detection.
- **Comprehensive Numerical Statistics**:
  - **Count** & **Unique Values** count
  - **Central Tendency**: Mean, Median, Mode
  - **Dispersion & Range**: Minimum, Maximum, Interquartile Range (IQR)
  - **Quartiles**: First Quartile (Q1 / 25th percentile), Third Quartile (Q3 / 75th percentile)

---

## Workflow Architecture
[ Upload CSV ] ──► [ Read CSV ] ──► [ Analyze Data (JS Node) ] ──► [ Show Report ]

1. **Upload CSV (n8n Form Trigger)**: Prompts the user to select and upload a CSV file.
2. **Read CSV (Extract From File)**: Parses binary file data into JSON rows.
3. **Analyze Data (Code Node)**: Runs custom JavaScript to compute statistical summaries and formatting.
4. **Show Report (n8n Form)**: Displays the structured text report to the user upon completion.

---

## Getting Started

### Prerequisites

- An active instance of **n8n** (Self-hosted, Desktop, or Cloud).

### How to Import and Run

1. Download or copy the `workflow.json` file from this repository.
2. Open your n8n dashboard.
3. Click **Workflows** > **Import from File** (or paste the JSON directly via **Import from URL/JSON**).
4. Save and activate the workflow.
5. Open the **Upload CSV** node to get the public Form URL and submit a CSV file to test.

---

## Sample Report Output

```text
CSV DATA ANALYSIS REPORT

Total Rows: 1000
Total Columns: 5

COLUMNS:
id, age, income, category, score

MISSING VALUES:
id: 0
age: 12
income: 45
category: 0
score: 3

DUPLICATE ROWS: 0

NUMERICAL STATISTICS:

--- age ---
Count: 988
Unique Values: 62
Mean: 38.45
Mode: 34
Minimum: 18
Q1 (25%): 28.00
Median (50%): 37.00
Q3 (75%): 49.00
IQR: 21.00
Maximum: 75
