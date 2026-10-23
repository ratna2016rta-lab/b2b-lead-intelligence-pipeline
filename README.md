# B2B Lead Intelligence & Qualification Pipeline

A Python-based pipeline that transforms raw company records into structured B2B lead-qualification reports.

## What It Does

- Cleans company data imported from Excel.
- Extracts business-like company names from email addresses when names are missing.
- Removes records without company names and deduplicates records.
- Extracts city information from full addresses.
- Checks likely company domains and verifies homepage content.
- Generates company-type keywords and assesses website condition.
- Uses rule-based scoring to classify leads for custom app/website development or PulseBoard.
- Exports structured Excel reports with lead priority and classification rationale.

## Technologies

Python, Pandas, Requests, BeautifulSoup, Openpyxl, Wordsegment, and Jupyter Notebook.

## Project Files

- `company_lead_pipeline.ipynb`: Main pipeline notebook.
- `requirements.txt`: Required Python packages.
- `.gitignore`: Excludes private datasets and temporary files.

## Getting Started

1. Install the packages listed in `requirements.txt`.
2. Open `company_lead_pipeline.ipynb`.
3. Update the input Excel path and output directory.
4. Run the notebook cells in order.

## Limitations

- Website discovery uses domain guessing, not exhaustive web search.
- A website not being found does not prove that the company has no website.
- Company-name extraction and city detection use heuristics and may require manual review.
- Lead qualification uses rule-based scores, not a trained machine-learning model.
- Website condition describes technical website signals, not company financial health.

## Data Privacy

Real company contact records, email addresses, phone numbers, and generated lead reports are not included in this repository.

## Pipeline Workflow

1. **Data Cleaning**
   - Reads the input Excel file
   - Standardizes column names
   - Fills missing company names from email local parts
   - Removes invalid and duplicate records
   - Extracts city names from addresses
   - Saves `cleaned_companies.xlsx`

2. **Website Intelligence**
   - Generates possible domain names from company names
   - Checks DNS availability
   - Fetches and validates homepage content
   - Determines whether the website belongs to the company
   - Evaluates website condition
   - Saves `website_check_results.xlsx`

3. **Lead Qualification**
   - Uses website presence, website condition, company type, and business keywords
   - Classifies each company for Custom Build or PulseBoard
   - Assigns a priority score
   - Generates a justification for every classification
   - Saves `lead_qualification_results.xlsx`

## Input Format

The input Excel file should contain columns similar to:

| Company Name | Phone Number | Email Address | State | Full Address |
|---|---|---|---|---|
| ABC Traders | 9876543210 | abc@gmail.com | Odisha | Bhubaneswar, Odisha |

Missing values can be marked as `other`.

## Output Files

| File | Description |
|---|---|
| `cleaned_companies.xlsx` | Cleaned and deduplicated company data with extracted city names |
| `website_check_results.xlsx` | Website availability, condition, company type, and keywords |
| `lead_qualification_results.xlsx` | Final lead category, priority score, and justification |

## Technologies Used

- Python
- Pandas
- Openpyxl
- Requests
- BeautifulSoup
- Wordsegment
- TQDM
- Excel automation

## How to Run

1. Clone this repository:

```bash
git clone [https://github.com/your-username/b2b-lead-intelligence-pipeline.git](https://github.com/your-username/b2b-lead-intelligence-pipeline.git)
cd b2b-lead-intelligence-pipeline
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Open the notebook:

```bash
jupyter notebook company_lead_pipeline.ipynb
```

4. Update the input file path in the configuration cell:

```python
INPUT_FILE = "path/to/your_input_file.xlsx"
OUTPUT_DIR = "path/to/output_folder"
```

5. Run all cells.


## Future Improvements

- Add web-search fallback for companies with non-standard domains
- Use an LLM to improve company-type classification
- Add a Streamlit dashboard for sales-team filtering
- Add CRM integration
- Add email/phone validation
- Add automated lead-ranking reports

## Author

Ratna Bibhusan Panda 
B.Tech Student | Data Science & AI-ML Enthusiast  
[LinkedIn](www.linkedin.com/in/ratna-bibhusan-panda-274325402) | [GitHub](https://github.com/ratna2016rta-lab)
