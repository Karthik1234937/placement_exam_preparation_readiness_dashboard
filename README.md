# 📊 Placement Exam Preparation & Readiness Simulator

An interactive, client-side data visualization dashboard engineered to model and optimize an **8-week campus placement assessment preparation strategy** across **Quantitative Aptitude, Logical Reasoning, Verbal Ability, and Core Technical subjects**.

Rather than relying on vanity metrics (like raw question counts or unanalyzed study hours), this simulator models preparation through three orthogonal behavioral levers—**Input Volume**, **Learning Efficiency**, and **Exam Calibration**—to project progress toward an **80.0 Preparation-Readiness Benchmark**.

---

## 🎯 Problem Statement & Modeling Philosophy

Students preparing for campus placements often fall into the **"Linear Grind Trap"**—assuming that studying 6 hours a day or taking daily mock tests automatically guarantees an 80%+ score. In reality, exam readiness is governed by **non-linear diminishing returns**, **cognitive fatigue**, and **feedback quality**.

### Epistemic Integrity: Readiness Index vs. Predicted Exam Score
Because baseline diagnostic test scores vary widely from student to student, inventing a raw predicted exam percentage without historical performance data would be misleading. Instead, this dashboard computes a transparent **Preparation-Readiness Index (`0–100`)**, clearly separating **effort metrics** (total hours, analysis time, tests taken) from **projected readiness**.

---

## ✨ Key Features

### 1. Three Orthogonal Interactive Levers
* **Effective Practice Hours / Day (`0.0 – 6.0 hrs/day`):** Models active, distraction-free problem-solving volume rather than passive reading or video watching.
* **Post-Practice Analysis Ratio (`0% – 60%`):** Captures the percentage of study time dedicated to dissecting mistakes, logging recurring error patterns, and re-solving missed problems.
* **Weekly Mock + Sectional Test Frequency (`0.0 – 5.0 tests/wk`):** Models timed exam calibration, sectional pacing, stamina, and negative-marking discipline.

### 2. Live Interactive Visualizations & Controls
* **8-Week Readiness Trajectory Chart (Chart.js):** Real-time multi-series line chart plotting your active strategy against **Low**, **Moderate (Recommended Balanced)**, and **Intensive** preparation benchmarks, anchored against the `80.0` target line.
* **Weekly Study Budget Allocation Doughnut:** Dynamically splits your weekly hours into *New Active Practice*, *Post-Practice Error Analysis*, and *Timed Mocks & Sectionals*.
* **One-Click Scenario Benchmarking & Zero-Baseline Reset:** Instantly toggle between **Initial (3h)**, **Low Prep**, **Moderate (Balanced)**, and **Intensive** presets, or click **Reset to 0** to clear all inputs to a zero baseline.
* **Interactive 8-Week Milestone Table & Section Filter:** Click any week (`W1–W8`) to inspect phase-specific action checklists, or filter guidance across **All Sections**, **Aptitude**, **Logical Reasoning**, and **Technical**.

---

## 🧮 Transparent Mathematical Model

All metrics update deterministically in real time using a three-pillar weighted composite model:

| Pillar | Weight | Mathematical Behavior & Domain Rationale |
| :--- | :---: | :--- |
| **1. Input Volume Score** | **35%** | Follows a saturating exponential curve $100 \times (1 - e^{-0.48 \times \text{Hours}})$ with a cognitive burnout penalty above `4.5 hrs/day`. |
| **2. Learning Efficiency Score** | **40%** | Bell-curved retention multiplier peaking in the `35%–45%` error-analysis sweet spot. Penalizes low review (`<20%`) and over-indexing (`>50%`) that crowds out new practice. |
| **3. Exam Calibration Score** | **25%** | Optimal pacing around `2.0–3.0 tests/week`. Zero testing leaves speed uncalibrated; `4–5 tests/week` introduces test fatigue and reduces concept-repair time. |
| **Illusion-of-Competence Drag** | *Penalty* | Applies an interaction penalty when high daily hours (`≥3.5h`) are paired with low mistake review (`<20%`), preventing false linear score inflation. |

### Scenario Comparison Summary

| Strategy Preset | Daily Hours | Error Analysis | Weekly Mocks | 8-Week Readiness | Takeaway |
| :--- | :---: | :---: | :---: | :---: | :--- |
| **Low Preparation** | `1.5 hrs` | `15%` | `0.5 / wk` | **44.2 / 100** | Insufficient volume and minimal error review lead to early plateauing. |
| **Initial Plan** | `3.0 hrs` | `30%` | `2.0 / wk` | **78.4 / 100** | Strong foundation; nudging analysis to `35%` crosses the `80.0` goal. |
| **Moderate (Recommended)** | `3.0 hrs` | `35%` | `2.5 / wk` | **83.6 / 100** | **Best ROI:** Fits a realistic 3-hour daily schedule without burnout. |
| **Intensive Preparation** | `5.5 hrs` | `20%` | `4.5 / wk` | **84.9 / 100** | Requires `+83%` more study hours for only `+1.3` extra points due to fatigue. |

---

## 🛠️ Tech Stack & Architecture

This project is built as a **zero-dependency, single-file web application** for effortless deployment and portability:

* **Structure:** Semantic HTML5
* **Styling:** Tailwind CSS (via CDN) + Custom CSS range-slider tracks (`Inter` & `JetBrains Mono` typography)
* **Data Visualization:** Chart.js `v4.4.1`
* **Simulation Engine:** Vanilla ES6+ JavaScript (`calculateModel()` deterministic engine)

```text
placement-prep-dashboard/
├── index.html      # Complete self-contained dashboard (UI, Tailwind config, Chart.js & simulation math)
└── README.md       # Project documentation, mathematical model & usage guide
```

---

## 🚀 Getting Started

### Option 1: Run Locally
No build tools, Node.js, or package installations are required:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/placement-prep-dashboard.git
   cd placement-prep-dashboard
   ```
2. **Open in your browser:**
   Double-click `index.html` or serve it locally with Python/VS Code Live Server:
   ```bash
   python3 -m http.server 8000
   # Visit http://localhost:8000
   ```

### Option 2: Deploy via GitHub Pages
1. Push `index.html` and `README.md` to your GitHub repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch** (`main` / `root`) and click **Save**.
4. Your interactive dashboard will be live at `https://your-username.github.io/placement-prep-dashboard/`.

---

## 🔮 Future Enhancements

* **Baseline Diagnostic Calibration:** Input initial mock scores per section (Aptitude, Logical, Verbal, Technical) to unlock personalized score-range projections.
* **LocalStorage Persistence:** Save custom weekly schedules and track actual completed hours against planned targets over the 8-week sprint.
* **CSV / PDF Study Plan Export:** Export the 8-week milestone breakdown into a printable weekly tracker.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
