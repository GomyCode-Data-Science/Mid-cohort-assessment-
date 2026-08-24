# Section 4 & 5 Assessment: API → Clean → Explore

**Duration:** 2-3 hours  
**Submission:** Fork repo, commit notebook + findings summary
**Learning Goals:**
- Fetch real data from an API (Section 4: APIs)
- Handle messy real-world data (Section 5: File Handling, Pandas Cleaning)
- Perform initial EDA (Section 5: Pandas Exploration/EDA)
- Use Git/GitHub workflow to submit work (Section 1: Version Control)

---

## Setup: Fork the Repository

Before you start, you'll submit your work via GitHub using the fork workflow:

### Step 1: Fork the Assessment Repo
1. Go to: **[assessment-repo-link-TBD]** (I'll share this)
2. Click the **Fork** button (top-right corner)
3. This creates your own copy of the repo under your GitHub account
4. You'll see it as `your-username/section4-5-assessment`

### Step 2: Clone Your Fork Locally
```bash
git clone https://github.com/YOUR-USERNAME/section4-5-assessment.git
cd section4-5-assessment
```

### Step 3: Create a Branch for Your Work
```bash
git checkout -b solution/your-name
```
(Replace `your-name` with your actual name, e.g., `solution/jane-doe`)

### Step 4: Add Your Work
- Create your Jupyter notebook: `Section4-5_Assessment_[YourName].ipynb`
- Create your findings summary: `Section4-5_Findings_[YourName].txt`
- Save both files in the repo root

### Step 5: Commit & Push
```bash
git add Section4-5_Assessment_[YourName].ipynb Section4-5_Findings_[YourName].txt
git commit -m "feat: Section 4-5 assessment - [YourName]"
git push origin solution/your-name
```

### Step 6: Submit a Pull Request (PR)
1. Go to **your forked repo** on GitHub
2. You'll see a banner suggesting "Compare & pull request"
3. Click it → review your changes → click "Create Pull Request"
4. Add a comment: "Ready for review"
5. **That's your submission!**

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
   - **OpenWeather API** (weather data by city) — works in Colab/local Jupyter
   - **JSONPlaceholder** (fake social media posts, comments, users) — no auth needed
   - **REST Countries API** (country stats: population, area, languages) — no auth needed
   - **ISS Location API** (International Space Station location history) — no auth needed
   - **PokéAPI** (Pokémon data: types, stats, evolution chains) — no auth needed
   - **Open-Meteo** (historical & current weather, no API key needed) — recommended
   - **GitHub API** (repository stars, commit counts, language stats) — no auth for public repos

   **Note:** All APIs work from your local machine or Google Colab. If you're using Claude's built-in code environment, test your API call locally first.

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

### Via GitHub (Required)

1. **Fork the repo** (see Setup section above)
2. **Create a branch** named `solution/your-name`
3. **Add two files** to your branch:
   - `Section4-5_Assessment_[YourName].ipynb`
   - `Section4-5_Findings_[YourName].txt`
4. **Commit** with a clear message: `"feat: Section 4-5 assessment - [YourName]"`
5. **Push** to your fork: `git push origin solution/your-name`
6. **Create a Pull Request** on GitHub and comment "Ready for review"

**Your PR is your submission.** I'll review it there and leave feedback as comments.

### Jupyter Notebook Structure
**File:** `Section4-5_Assessment_[YourName].ipynb`

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

### Findings Summary (1 Page)
**File:** `Section4-5_Findings_[YourName].txt`

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

### Git/GitHub
- [ ] Forked the repo to your account
- [ ] Created a branch: `solution/your-name`
- [ ] Committed changes with clear message
- [ ] Pushed to your fork
- [ ] Created a Pull Request with "Ready for review" comment

### Notebook File
- [ ] Notebook file named correctly: `Section4-5_Assessment_[YourName].ipynb`
- [ ] All cells run without errors
- [ ] API source clearly documented
- [ ] At least 3 cleaning steps shown
- [ ] Univariate + bivariate analysis included
- [ ] Markdown cells explain your thinking
- [ ] Code is commented & readable

### Findings Summary
- [ ] File named correctly: `Section4-5_Findings_[YourName].txt`
- [ ] 1 page max (concise)
- [ ] Covers: dataset, cleaning, key findings, next steps

---

## Troubleshooting

**"API returned 403 Forbidden"**
- This is a network restriction in Claude.ai. Run your code in **Google Colab** or **local Jupyter** instead.
- All APIs in the list work perfectly outside Claude's environment.

**"Connection timeout"**
- Check your internet connection.
- Try a different API from the list (some are faster than others).
- Open-Meteo tends to be the most reliable.

**"Empty JSON or 0 records"**
- Check your API parameters (URLs, query strings).
- Some APIs require specific parameter formats. Read their docs briefly.
- JSONPlaceholder always returns data; if it fails, you have a connection issue.

**"I'm not sure if I fetched enough data"**
- The task requires 100+ rows minimum. Most APIs can return this easily.
- For PokéAPI: use `/pokemon?limit=150` to fetch 150 Pokémon records in one call.
- For JSONPlaceholder: fetch `/posts`, `/comments`, or `/users` (each has 100+).
- For REST Countries: `/all` returns 195 countries—plenty.

## Support & Questions

**During:** Post questions in cohort chat with your API + error (if any)  
**After submission:** I'll review within 48 hours; feedback on findings + code quality

**Good luck!**
