# IPL Data Analysis using Apache Spark

This project performs advanced data analysis on IPL datasets using **Apache Spark**. The analysis includes player performance, team performance, and key match insights from historical IPL data. It leverages PySpark for data processing and SQL for querying.

---

## 🚀 Features

- **Data Loading and Schema Definition**:
  - Define schemas for various datasets such as Ball-by-Ball, Matches, Players, Teams, and Player-Match details.
  - Load CSV data into Spark DataFrames.

- **Data Transformation**:
  - Clean and filter data to exclude invalid entries (e.g., extras, no balls).
  - Create calculated columns like `running_total_runs` and flags for high-impact deliveries.

- **Key Insights**:
  - **Top Scorers**: Identify top-scoring batsmen for each IPL season.
  - **Economical Bowlers**: Analyze the most economical bowlers during powerplay overs.
  - **Toss Analysis**: Assess the impact of winning the toss on match outcomes.
  - **Player Impact**: Determine players' average runs in winning matches and categorize players based on batting styles and veteran status.

- **Data Enrichment**:
  - Add time-based features like year, month, and day for matches.
  - Categorize win margins into "High", "Medium", and "Low".

---

## 🗂️ Datasets

This project uses the following datasets stored in an S3 bucket:

1. **Ball-By-Ball Data**: Details about every ball bowled in IPL matches.
2. **Match Data**: Match details including teams, venues, and outcomes.
3. **Player Data**: Player information such as batting style, bowling skills, and country.
4. **Player-Match Data**: Player statistics for each match.
5. **Team Data**: IPL team details.

---

## 🔧 Technology Stack

- **Apache Spark** (v3.3.2)
- **PySpark**
- **AWS S3** for data storage
- **Databricks** for development and execution
- **SQL** for querying data

---

## 📈 Example Insights

### Top Scorers by Season
A list of batsmen with the highest total runs scored in each IPL season.

### Economical Bowlers in Powerplay
The most economical bowlers during the first six overs, ranked by average runs conceded per ball.

### Toss Impact
Evaluate how often winning the toss correlates with winning the match.

---

## 🛠️ Getting Started

### Prerequisites
1. **Apache Spark** installed or access to a Databricks environment.
2. Python environment with the following packages:
   - `pyspark`
   - `pandas` (optional for additional analysis)

### Setup
1. Clone the repository:
   ```bash
   git clone <repository_url>

2. Load the datasets into an accessible path (e.g., AWS S3 or local storage).
3. Update paths in the notebook (`sprk_ipl_analysis`) to point to your dataset locations:
   ```python
   # Example paths for loading datasets
   Ball_By_Ball_df = spark.read.schema(Ball_By_Ball_schema).format("csv").option("header", "true").load("s3://spark-ipl-analysis/Ball_By_Ball.csv")
   Match_df = spark.read.schema(match_schema).format("csv").option("header", "true").load("s3://spark-ipl-analysis/Match.csv")
   Player_df = spark.read.schema(player_schema).format("csv").option("header", "true").load("s3://spark-ipl-analysis/Player.csv")
   Player_match_df = spark.read.schema(player_match_schema).format("csv").option("header", "true").load("s3://spark-ipl-analysis/Player_match.csv")
   Team_df = spark.read.schema(team_schema).format("csv").option("header", "true").load("s3://spark-ipl-analysis/Team.csv")

4. Run the notebook in your Databricks or local Spark environment.

## Running the Analysis

1. Start a Spark session in the notebook:
   ```python
   spark = SparkSession.builder.appName("IPL Data Analysis").getOrCreate()

2. Load datasets into Spark DataFrames and execute the notebook cells sequentially to generate insights.

## 📊 SQL Queries

Several SQL queries are used in this project to extract insights:
- **Top batsmen and their scores per season.**
- **Toss winner vs. match winner analysis.**
- **Most economical bowlers in powerplay.**

## 📂 Repository Structure

```plaintext
.
├── README.md            # Project documentation
├── sprk_ipl_analysis    # Databricks notebook for analysis
├── datasets/            # Folder for datasets (add locally or link to S3)
└── results/             # Folder to save results and plots

## 📝 Future Work

- Integrate real-time IPL match data using APIs.
- Extend analysis to predict match outcomes using ML models.
- Create visualizations using tools like Matplotlib or Tableau.
