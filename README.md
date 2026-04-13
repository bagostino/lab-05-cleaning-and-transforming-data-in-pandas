# Lab 5 — Cleaning and Transforming Data in Pandas

**Course:** Python for AI & Data  
**Unit:** 2 — Cleaning and Transforming Data with Python Tools  
**Lab Time:** 60 minutes

---

## The PaperLane Scenario

**PaperLane** is a small stationery and office supplies shop operating across four regions — East, West, Midwest, and South — through two channels: Online and In-Store.

Their sales team has been logging orders manually across spreadsheets for several months. Different staff members have entered data in slightly different ways, and the result is a dataset that has never been cleaned. Before any analysis can happen, the data needs to be fixed.

You've been brought in as their first data analyst. Your first task: take the raw order export and produce a clean, analysis-ready dataset that the business can actually trust.

This scenario continues across all Unit 2 labs. By the end of the unit you'll have cleaned, transformed, statistically analysed, and visualised PaperLane's sales data.

---

## Learning Objectives

By the end of this lab, you'll be able to:

- Load a CSV into a Pandas DataFrame using `pd.read_csv()`
- Perform a structured data quality inspection using `info()`, `describe()`, `isna()`, and `value_counts()`
- Remove duplicate rows using `drop_duplicates()`
- Handle missing values with justified strategies
- Standardise text columns using Pandas string methods
- Convert date columns using `pd.to_datetime()`
- Create derived columns using vectorised operations
- Filter rows using boolean conditions
- Save a cleaned DataFrame to `data/processed/`

---

## Getting Started

### Step 1: Fork the Lab Repo

Go to the course GitHub organisation and find **lab-5-cleaning-and-transforming-data-in-pandas**.  
Click **Fork** to create your personal copy.

### Step 2: Clone Your Fork

```bash
git clone git@github.com:YOUR-USERNAME/lab-5-cleaning-and-transforming-data-in-pandas.git
cd lab-5-cleaning-and-transforming-data-in-pandas
```

### Step 3: Activate Your Environment and Launch JupyterLab

```bash
source venv/bin/activate        # Mac/Linux
# source venv/Scripts/activate  # Windows
jupyter lab
```

Open `notebooks/lab5_starter.ipynb`.

---

## Project Structure

```text
lab-5-cleaning-and-transforming-data-in-pandas/
│
├── data/
│   ├── raw/
│   │   └── paperlane_orders.csv     ← provided — do not modify
│   └── processed/                   ← your outputs go here
│
├── notebooks/
│   └── lab5_starter.ipynb
│
├── requirements.txt
│
└── README.md
```

---

## What's in the Raw Data?

The file `data/raw/paperlane_orders.csv` contains 21 rows of PaperLane order records with the following columns:

| Column | Description |
|--------|-------------|
| `order_id` | Unique order identifier |
| `order_date` | Date of order (inconsistently formatted) |
| `customer` | Customer first name |
| `region` | Sales region (East, West, Midwest, South) |
| `product` | Product name |
| `quantity` | Units ordered |
| `unit_price` | Price per unit |
| `channel` | Sales channel (Online / In-Store) |
| `status` | Order status (Complete / Returned) |

The data has several quality issues that you will identify and fix during this lab.

---

## Lab Exercises

Work through the starter notebook from top to bottom.

### Task 1 — Load and First Look
Load the raw data and inspect the first few rows. Confirm the shape and column names.

### Task 2 — Structured Inspection
Use `info()`, `isna().sum()`, `duplicated().sum()`, and `value_counts()` to build a complete picture of the data quality issues. Document every issue you find in a markdown cell before making any changes.

### Task 3 — Remove Duplicates
Identify and remove duplicate rows. Print row counts before and after to confirm.

### Task 4 — Handle Missing Values
Address missing values in all affected columns. Justify each decision in a markdown cell.

### Task 5 — Standardise Text Columns
Fix inconsistent casing and whitespace in `status`, `region`, and `channel`. Verify with `value_counts()` after each fix.

### Task 6 — Convert the Date Column
Convert `order_date` to a proper datetime type. Confirm the dtype has changed.

### Task 7 — Create Derived Columns
Calculate `revenue` for each order. Extract `order_month` from the date column.

### Task 8 — Filter and Sort
Create a filtered DataFrame containing only `Complete` orders. Sort it by `revenue` descending.

### Task 9 — Save Cleaned Data
Save the full cleaned DataFrame and the complete-orders DataFrame to `data/processed/`.

---

## Optional Advanced Tasks

1. **Revenue by region:** Group the complete orders by region and calculate total revenue, number of orders, and average order value per region. Display as a sorted DataFrame.

2. **Revenue by channel:** Do the same grouping but by `channel`. Does Online or In-Store drive more revenue?

3. **Pivot table:** Build a pivot table showing total revenue by `region` (rows) and `product` (columns). Fill missing combinations with 0.

---

## Submitting Your Work

```bash
git add .
git commit -m "Complete lab 5"
git push
```

Make sure:
- All notebook cells show output (run top to bottom before pushing)
- `data/processed/` contains at least two CSV files
- Task 2 has a markdown cell documenting all data quality issues found

---

## Tips for Success

- **Inspect before you modify** — document every issue before writing a single line of cleaning code
- **Verify after every fix** — run `isna().sum()` and `value_counts()` after each cleaning step
- **Justify your decisions** — every choice (drop vs fill, what to fill with) needs a markdown explanation
- **Raw data is sacred** — never modify `data/raw/paperlane_orders.csv`

---

## Resources

- **Pandas documentation:** https://pandas.pydata.org/docs/
- **Pandas user guide — missing data:** https://pandas.pydata.org/docs/user_guide/missing_data.html
- **Pandas string methods:** https://pandas.pydata.org/docs/user_guide/text.html
- **Real Python — cleaning data:** https://realpython.com/python-data-cleaning-numpy-pandas/
