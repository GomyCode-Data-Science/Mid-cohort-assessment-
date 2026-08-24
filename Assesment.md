# Section 4 & 5 Assessment: API → Clean → Explore

**Duration:** 2-3 hours  
**Submission:** Jupyter notebook (.ipynb) + brief 1-page findings summary  via github link
**Learning Goals:**
- Fetch real data from an API (Section 4: APIs)
- Handle messy real-world data (Section 5: File Handling, Pandas Cleaning)
- Perform initial EDA (Section 5: Pandas Exploration/EDA)
- Document findings clearly (prepare for visualization)

---

## Task Overview

You will:
1. **Fetch data** from a public API of your choice
2. **Clean** the dataset (handle missing values, data types, outliers)
3. **Explore** the data (distributions, correlations, patterns)
4. **Document** your findings in a 1-page summary

This mimics a real data pipeline: raw → usable → understood.

---

## Part 1: Data Collection (Section 4 - APIs, ~30-45 min)

### What to do
1. Choose a **free public API** from this list (or propose one):
   - **OpenWeather API** (weather data by city)
   - **JSONPlaceholder** (fake social media posts, comments, users)
   - **REST Countries API** (country stats: population, area, languages)
   - **ISS Location API** (International Space Station location history)
   - **PokéAPI** (Pokémon data: types, stats, evolution chains)
   - **Open-Meteo** (historical & current weather, no API key needed)
   - **GitHub API** (repository stars, commit counts, language stats)

2. **Fetch at least 100+ rows** of data using `requests` library
3. Store the data in a **pandas DataFrame**
4. Save to CSV (you'll use this for cleaning)

### Checkpoint questions (answer in notebook markdown)
- What was the API endpoint you used?
- How many records did you fetch? How many columns?
- Did the API have any rate limits or auth requirements?
- What were the column data types initially?

---

## Part 2: Data Cleaning (Section 5 - File Handling & Pandas Cleaning, ~45-60 min)

### What to do
1. **Load** your CSV into a fresh DataFrame
2. **Inspect** the data:
   - Use `.info()`, `.describe()`, `.head()`
   - Identify missing values (count + %)
   - Check for duplicates
3. **Clean**:
   - Handle missing values (drop, fill, or justify keeping them)
   - Fix data types (convert strings to dates/numbers as needed)
   - Remove or flag outliers (document your decision)
   - Check for and remove duplicates if any
4. **Document** each cleaning decision (why you chose that approach)

### Checkpoint questions (answer in notebook markdown)
- How many missing values did you find? In which columns?
- Did you drop rows, fill values, or keep them? Why?
- Were there duplicates? How did you handle them?
- Did any data type conversions surprise you?

---

## Part 3: Exploratory Data Analysis (Section 5 - Pandas EDA, ~45-60 min)

### What to do
1. **Univariate analysis** (one variable at a time):
   - For numeric columns: mean, median, std, min, max
   - For categorical columns: value counts, mode
   - Identify any skewness or unusual distributions
2. **Bivariate analysis** (relationships between variables):
   - Pick 2-3 numeric pairs → calculate correlation
   - Pick 1 numeric + 1 categorical → groupby averages
3. **Document patterns**:
   - What surprised you?
   - What patterns did you spot?
   - Any outliers or anomalies worth flagging?

### Checkpoint questions (answer in notebook markdown)
- Which column has the most missing data?
- What is the correlation between your strongest pair of variables?
- What's the most common value in your categorical column?
- What's one unexpected pattern you found?

---

## Submission Format

### Part A: Jupyter Notebook
**File:** `Section4-5_Assessment_[YourName].ipynb`

Structure:
```
1. Title + Intro (1 cell)
2. Part 1: Data Collection
   - API details + code
   - Initial data shape
3. Part 2: Data Cleaning
   - Missing value inspection
   - Cleaning steps with reasoning
   - Final data shape
4. Part 3: EDA
   - Univariate summaries (code + output)
   - Bivariate analysis (code + output)
   - Patterns & insights (markdown)
5. Conclusion: What's the next step for this data? (visualization? modeling?)
```

**Code style:**
- Comment your cleaning logic
- Use descriptive variable names
- One analysis per cell (easy to read)

### Part B: 1-Page Findings Summary
**File:** `Section4-5_Findings_[YourName].txt` or `.pdf`

Write in plain language:
- **Dataset:** What data did you collect? (source, size, domain)
- **Cleaning:** What issues did you find? How did you fix them?
- **Key Findings:** 3-5 bullet points of patterns/insights you uncovered
- **Next Steps:** If you were to visualize this data, what would be most interesting to show?

Example:
```
DATASET
I collected 250 weather records from OpenWeather API for 5 East African cities.
Data spans July 2026 with daily temperature, humidity, and precipitation.

CLEANING
- Found 12 missing humidity values (4.8%) → filled with daily city average
- Converted temperature from Kelvin to Celsius
- Removed 3 duplicate records (same timestamp + city)

KEY FINDINGS
- Nairobi had the most stable temperatures (std = 2.1°C)
- Strong negative correlation between altitude and average temp (r = -0.82)
- Weekend precipitation 23% higher than weekdays (interesting!)
- One outlier: Mombasa hit 38°C on July 15 (checked—real heatwave)

NEXT STEPS
A heatmap showing daily temps across cities would be powerful.
Or a time series showing humidity trends by location.
```

---

## Grading Rubric

| Criterion | Full (4) | Good (3) | Needs Work (2) | Incomplete (1) |
|-----------|----------|----------|---|---|
| **Data Collection** | 100+ rows, clean API call, documented process | 80+ rows, API call works, some docs | <80 rows or unclear API logic | No valid data collected |
| **Cleaning** | Addresses missing, dupes, types; decisions justified | Handles 2/3 issues; light reasoning | Handles 1 issue; minimal reasoning | Little to no cleaning |
| **EDA** | 3+ univariate, 2+ bivariate, clear insights | 2 univariate, 1 bivariate, some insights | 1 univariate or 1 bivariate only | No analysis attempted |
| **Documentation** | Clear markdown, comments, logical flow | Mostly clear, some comments | Sparse notes, hard to follow | No documentation |
| **Findings Summary** | Concise, insightful, ready for next step | Covers basics, minor gaps | Vague or incomplete | Missing/blank |

**Pass threshold:** 13/20 points (65%)

---

## Tips & Guardrails

**Do:**
- Test your API call **before** submitting (no 404s or auth errors)
- Save intermediate CSVs so you can reload data if needed
- Comment **why** you're cleaning a certain way, not just **what**
- Use `.value_counts()` on categoricals—reveals a lot fast
- Check `.corr()` on all numeric columns—surprises often hide there

**Don't:**
- Drop entire columns with missing data (too aggressive; justify instead)
- Ignore outliers without investigation (they're often real & interesting)
- Overwrite your raw CSV (keep original + cleaned separate)
- Skip the reasoning—a cleaning choice without explanation is worth 0 points

---

## Deliverables Checklist

- [ ] Notebook file submitted (named correctly)
- [ ] All cells run without errors
- [ ] API source clearly documented
- [ ] At least 3 cleaning steps shown
- [ ] Univariate + bivariate analysis included
- [ ] Markdown cells explain your thinking
- [ ] 1-page findings summary attached
- [ ] Code is commented & readable

---

## Support & Questions

**During:** Post questions in cohort chat with your API + error (if any)  
**After submission:** I'll review within 48 hours; feedback on findings + code quality

**Good luck!**
