# Data Professional Survey Dashboard in Power BI

A single-page Power BI dashboard summarising an online survey of 630 data professionals. It covers roles, salaries, favourite programming languages, job satisfaction and how hard it was to break into the field.

> **Guided learning project.** This dashboard follows the Power BI tutorial and final project by
> [Alex The Analyst](https://github.com/AlexTheAnalyst/Power-BI). The source Excel file is the course file.
> I built the report myself in Power BI Desktop while following the course.

## Context

The project practises the core Power BI workflow: importing an Excel file, cleaning and reshaping it in Power Query, and building an interactive one-page report with cards, charts and gauges.

## Questions

1. How many people took the survey, and what is their average age?
2. What is the average salary per job title?
3. Which programming languages are most popular, and with which roles?
4. Which countries do respondents live in?
5. How happy are respondents with their salary and with their work/life balance?
6. How difficult was it to break into data?

## Technologies

- Microsoft Power BI Desktop (`.pbix`)
- Power Query (data transformation)
- Microsoft Excel (source data)

## Dataset and source

| Item | Detail |
|---|---|
| File | `Power BI - DataProfessionalSurvey.xlsx`, one sheet with 630 responses and 28 columns. The responses were collected from 10 to 26 June 2022 (`Date Taken` column). |
| Source | Course material. The file is **byte-identical** (same Git blob hash `aee81e1…`) to `Power BI - Final Project.xlsx` in [AlexTheAnalyst/Power-BI](https://github.com/AlexTheAnalyst/Power-BI). That repository does not state a license. |
| Personal data | Checked before publishing: the `Email` column contains a single anonymised placeholder value for every row, and `City`, `Country`, `Referrer`, `Browser` and `OS` are empty. |

The Excel file is kept unchanged so the report can be refreshed.

## Data model and transformations

The model contains one table, `Data Professional Survey`, loaded from the Excel sheet.

The `.pbix` report layout uses columns that **do not exist in the source Excel**:

| Column in the model | Indicates |
|---|---|
| `Q1 - Which Title Best Fits your Current Role?.1` | Power Query *Split Column* on the job title |
| `Q5 - Favorite Programming Language.1` | *Split Column* on the free-text "Other" answers |
| `Q11 - Which Country do you live in?.1` | *Split Column* on the country answer |
| `Average Salary` | A column derived from the salary-range answer (`Q3`) |

The exact Power Query steps are stored in compressed form inside the `.pbix` and can only be inspected in **Power BI Desktop** (*Transform data* → *Applied steps*). They are not described here in more detail to avoid guessing.

## Visualisations

Read from the report layout in the `.pbix`:

| Visual | Type | Measure |
|---|---|---|
| Count of Survey Taker | Card | Count of `Unique ID` |
| Average Age Survey Taker | Card | Average of `Q10 - Current Age` |
| Average Salary by Job Title | Bar chart | Average of `Average Salary` by job title |
| Favorite Programming Language | Stacked column chart | Count of respondents by language, split by job title |
| Survey Countries | Treemap | Count of respondents by country |
| Happiness with Salary | Gauge | Average, min and max of `Q6 (Salary)` |
| Happy With Work-Life Balance | Gauge | Average, min and max of `Q6 (Work/Life Balance)` |
| Difficulty to Break Into Data | Donut chart | Count of answers to `Q7` |

## Repository structure

```
.
├── PortafolioProject5-DataProfessionalSurveyBreakdown.pbix   # Power BI report (unchanged)
├── Power BI - DataProfessionalSurvey.xlsx                    # Source data (unchanged)
└── README.md
```

## Results

The only facts verified outside Power BI are that the data contains **630 responses collected in June 2022**. The values shown on the dashboard (average salaries, satisfaction scores, rankings) were **not** extracted, because that requires opening the report in Power BI Desktop.

**No dashboard screenshot is included.** Power BI Desktop was not available when this documentation was written, and an image of the dashboard was not created by any other means.

## How to open

1. Install **Power BI Desktop** (Windows, free) from Microsoft.
2. Clone or download this repository.
3. Open `PortafolioProject5-DataProfessionalSurveyBreakdown.pbix`.
4. If Power BI asks for the data source, go to *Transform data* → *Data source settings* and point it to `Power BI - DataProfessionalSurvey.xlsx` in this folder.

## Limitations

- The data is a voluntary online survey, so it is not a representative sample of data professionals.
- Salary is collected as ranges, so `Average Salary` is an approximation.
- The report has a single page with no documented measures (DAX) or drill-through.

## Next steps

- Export a real screenshot from Power BI Desktop and add it to this README.
- Document the Power Query applied steps and add explicit DAX measures.
- Publish to the Power BI service (*Publish to web*) if sharing is appropriate.

## Credits

- Tutorial and survey data: [Alex The Analyst – Power-BI](https://github.com/AlexTheAnalyst/Power-BI).

## Contact

**Kevin Espinoza**, Civil Engineer transitioning into Data Analytics and Automation
GitHub: [@kevinEspinozaTech](https://github.com/kevinEspinozaTech) · Email: [k.espinozano@gmail.com](mailto:k.espinozano@gmail.com)
