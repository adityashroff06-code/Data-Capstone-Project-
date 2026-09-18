# Data Capstone Project — CRM Migration Data Audit

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-Data_Quality-150458?logo=pandas&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

Capstone coursework (George Brown College) simulating a real post-migration scenario: a company has moved customer records from a legacy system into a new CRM, and the data team must **audit the migration** — quantify what was lost, corrupted, or duplicated, and report the findings to stakeholders.

## The scenario

After a CRM migration, nobody fully trusts the new system yet. This exercise runs a structured **data quality audit** comparing the legacy export (`old_system_data.csv`) against the new CRM extract (`new_crm_data.csv`) across four dimensions:

| Audit dimension | Check performed |
|---|---|
| **Completeness** | Null/missing values per field in both systems |
| **Accuracy** | Field-by-field comparison (email, phone, date of birth) for customers present in both systems |
| **Integrity** | Records that exist in one system but not the other |
| **Uniqueness** | Duplicate `CustomerID`s within each system |

Dates of birth are normalized with `pd.to_datetime(..., errors="coerce")` before comparison so format drift between systems doesn't produce false mismatches.

## Deliverables

```
Exercise Three/
├── CRM_Data_Audit.ipynb                    # Clean, scripted audit (the reusable version)
├── Exercise_3 .ipynb                       # Audit run with printed report output
├── old_system_data.csv                     # Legacy system export (sample)
├── new_crm_data.csv                        # New CRM extract (sample)
├── Data_Audit_Assignment.docx              # Assignment brief
├── Post_Migration_CRM_Audit_Report.docx    # Written audit report for stakeholders
└── Data-Audit-Report-Analysis.pptx         # Presentation of findings
```

The CSVs are small **synthetic samples** (customer ID, name, email, phone, date of birth) designed to exercise every audit rule; the same script scales unchanged to full production extracts.

## Running the audit

```bash
git clone https://github.com/adityashroff06-code/Data-Capstone-Project-.git
cd Data-Capstone-Project-

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook "Exercise Three/CRM_Data_Audit.ipynb"
```

## Why this matters

Data migration audits are one of the most common real-world analytics tasks — every system change (CRM, ERP, billing) needs one. The pattern demonstrated here (completeness → accuracy → integrity → uniqueness, then a stakeholder-facing report) mirrors how professional data teams sign off on a migration.

## License

Released under the [MIT License](LICENSE).

## Author

**Aditya Shroff** — [GitHub](https://github.com/adityashroff06-code) · [LinkedIn](https://www.linkedin.com/in/aditya-shroff-8033a31b0)
