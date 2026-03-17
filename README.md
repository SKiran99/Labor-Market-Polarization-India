# Labor-Market-Polarization-India
Analysis of wage inequality, occupational polarization, and employment structure in India using PLFS-style microdata (120,000 worker observations).


# 👷 Labor Market Polarization in India
### An Analysis of Wage Inequality, Occupational Shifts, and Employment Patterns Using PLFS Microdata

## 📌 Project Overview

Labor market polarization — the simultaneous growth of high-skill and low-skill
employment at the expense of middle-skill routine jobs — is a well-documented
phenomenon in developed economies. This project investigates whether a similar
structural shift is underway in India, using a large worker-level microdata
dataset modeled on the Periodic Labour Force Survey (PLFS).

The analysis spans 120,000 worker observations across 15 Indian states,
covering the period 2017–2023, and examines wage inequality, occupational
composition, gender gaps, and returns to education.

---

## 🔬 Research Questions

1. Is India's labor market polarizing — are middle-skill occupations shrinking?
2. How do wages vary by education level, occupation, gender, and state?
3. What is the extent of wage inequality (Gini coefficient) across states?
4. How does the urban–rural divide shape employment composition and wages?

---

## 📊 Key Findings

| Finding | Result |
|---|---|
| Middle-skill employment share (2017–2023) | Declining — consistent with polarization |
| National average Gini (wages) | ~0.42 — high inequality |
| Urban–rural wage gap | Urban workers earn ~18% more |
| Graduate wage premium | Graduates earn ~3–4x more than non-literates |
| Gender wage gap | Women earn ~20% less across all skill tiers |
| Riskiest group | Low-skill rural female workers — lowest wages, highest inequality |

---

## 📈 Visualizations

| Chart | Description |
|---|---|
| `polarization_trend.png` | Employment share by skill tier, 2017–2023 |
| `skill_wage_gradient.png` | Wage distribution and mean wages by occupation |
| `gender_wage_gap.png` | Gender wage gap by skill tier and education |
| `state_gini.png` | Gini coefficient of wages by state |
| `returns_to_education.png` | Mean and median wages by education level |
| `rural_urban_structure.png` | Employment composition — rural vs urban |
| `wage_distribution.png` | Raw and log-wage distributions |

---


# 📂 Data Sources — Labor Market Polarization in India

## Primary Reference Sources

### 1. Periodic Labour Force Survey (PLFS) — MOSPI
- **Provider:** Ministry of Statistics and Programme Implementation, Govt. of India
- **URL:** https://mospi.gov.in/web/plfs
- **Contains:** Individual-level worker data — demographics, education, occupation,
  wages, employment type, industry, hours worked
- **Access:** Free — annual microdata files available for download
- **Coverage:** 2017–18 onwards, ~100,000+ households per round

### 2. PLFS Annual Reports
- **Provider:** MOSPI
- **URL:** https://mospi.gov.in/periodic-labour-force-survey-plfs-annual-report
- **Contains:** Published summary statistics, labour force participation rates,
  unemployment rates, wage tables by state and sector
- **Access:** Free PDF download

### 3. ILO India Labour Statistics
- **Provider:** International Labour Organization
- **URL:** https://ilostat.ilo.org/data/
- **Contains:** Harmonized international labour statistics for India —
  employment by occupation (ISCO), wages, hours, informal employment
- **Access:** Free

### 4. World Bank India Labour Data
- **Provider:** World Bank — World Development Indicators
- **URL:** https://databank.worldbank.org/source/world-development-indicators
- **Contains:** GDP per worker, employment ratios, wage and salaried workers (%)
- **Access:** Free

### 5. National Classification of Occupations (NCO-2015)
- **Provider:** Ministry of Labour & Employment, Govt. of India
- **URL:** https://dge.gov.in/dge/sites/default/files/UploadDocument/2022/NCO-2015.pdf
- **Contains:** India's official occupational classification system used to
  define skill tiers (High / Middle / Low skill)
- **Access:** Free

## Dataset Note
This project uses a simulated microdata dataset of 120,000 worker
observations. Variable structure, coding schemes, and value distributions
are grounded in published PLFS annual reports and ILO India statistics.
Skill tier classification follows the NCO-2015 framework.
---

## 🛠️ Tools & Libraries

| Tool | Purpose |
|---|---|
| Python 3.10+ | Core language |
| Pandas | Microdata handling & aggregation |
| NumPy | Wage computation & Gini coefficient |
| Matplotlib | Publication-quality charts |
| Seaborn | Statistical visualizations |
| SciPy | Distributional statistics (skewness, kurtosis) |

---

# 📐 Methodology Notes — Labor Market Polarization in India

## 1. Conceptual Framework

This project draws on the **task-based framework of labor demand**
(Autor, Levy & Murnane, 2003; Autor, 2019) which categorizes occupations
by the routine-cognitive task content they perform:

| Skill Tier | Occupation Types | Task Content |
|---|---|---|
| **High-Skill** | Managers, Professionals, Technicians | Non-routine cognitive |
| **Middle-Skill** | Clerks, Craft Workers, Machine Operators | Routine cognitive & manual |
| **Low-Skill** | Service Workers, Agricultural Workers, Elementary | Non-routine manual |

**Polarization hypothesis:** Technological change and automation primarily
displace middle-skill routine tasks, leading to employment growth at both
ends of the skill distribution — and a "hollowing out" of the middle.

## 2. Occupation Classification

India's National Classification of Occupations 2015 (NCO-2015) is used
to map occupations to skill tiers. NCO-2015 is aligned with the
International Standard Classification of Occupations (ISCO-08).

## 3. Wage Construction

Monthly wages are constructed for regular wage/salary workers and
self-employed workers based on PLFS variable definitions:
- Regular workers: reported monthly earnings
- Self-employed: monthly net receipts from enterprise

**Log wages** are used in distributional analysis following standard
labour economics practice (wages are right-skewed; log transformation
approximates normality).

## 4. Gini Coefficient

The Gini coefficient is computed from the standard formula:
```
G = (2 * Σ(i * w_i)) / (n * Σ(w_i)) - (n+1)/n
```

where w_i are wages sorted in ascending order and i is rank.
Range: 0 (perfect equality) to 1 (maximum inequality).

## 5. Polarization Measurement

Employment share by skill tier is computed for each survey year:
```
Share(tier, t) = Employed(tier, t) / Total_Employed(t)
```

A decline in middle-skill share alongside growth in high-skill and/or
low-skill share is taken as evidence of polarization.

## 6. Gender Wage Gap

The raw gender wage gap is computed as:
```
Gap(%) = (Mean_Wage_Male - Mean_Wage_Female) / Mean_Wage_Male × 100
```

This is the unadjusted gap — it does not control for occupation or
education differences. A full Oaxaca-Blinder decomposition would be
the natural extension for a research paper.

## 7. Limitations

- Simulated data cannot capture actual PLFS sampling design and weights
- Self-employment income is notoriously underreported in surveys
- Gini coefficient is sensitive to top-coding of wages
- Polarization signal may reflect structural transformation
  (agriculture → services) rather than technology-driven displacement

---

  
## 📄 License

MIT License — see [LICENSE](LICENSE) for details.
