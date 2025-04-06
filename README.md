#  PubMed Research Paper Fetcher

##  Project Description

This command-line Python program fetches research papers from the **PubMed API** based on a user-defined query, identifies papers with **at least one author affiliated with a pharmaceutical or biotech company**, and returns results as a structured **CSV file**.

The tool supports **PubMed's full query syntax**, includes filtering for **non-academic affiliations**, and provides **corresponding author details** for deeper insights. Designed with modularity, typed Python, and performance in mind, the project is fully CLI-enabled, Poetry-managed, and PyPI-ready.


## ✅ Functional Highlights

-  Fetches papers using the **PubMed API** with advanced query support.
-  Filters authors based on **non-academic/company affiliations**.
-  Extracts **corresponding author emails**.
-  Outputs results in a structured **CSV format** or to the **console**.
-  Typed Python with a modular, testable design.
-  Command-line tool powered by **Poetry** with full dependency management.



##  Project Structure

```
pubmed/
├── fetcg_query/
│   └── pubmed_fetcher.py        # Core logic and paper-fetching module
├── get_query/
│   └── get_paper_list.py        # CLI interface for running queries
├── tests/                       # Unit tests
├── pyproject.toml               # Poetry project config  

```



## 🧱 Module Breakdown

### 🔹 `fetch_query` (in `pubmed_fetcher.py`)
Handles core logic:
- `__init__(debug: bool)`: Initialize with debug mode.
- `fetch_pubmed_ids(query: str)`: Retrieves PubMed IDs based on query.
- `fetch_paper_details(pubmed_ids: List[str])`: Gets XML data for paper IDs.
- `parse_paper_details(xml_data: str)`: Extracts title, authors, affiliations, emails.
- `filter_non_academic_authors(...)`: Identifies non-academic authors using heuristics (e.g., presence of keywords like **pharma, biotech**, and absence of academic indicators).
- `save_to_csv(...)`: Saves output as CSV using pandas.

### 🔹 `get_query` (in `get_paper_list.py`)
CLI entry point:
- `run()`: Parses command-line arguments and triggers logic.


## ⚙️ Command-Line Usage

```bash
# Basic Query
poetry run get-papers "your_query_here"

# Save to CSV
poetry run get-papers "your_query_here" -f output.csv

# Enable Debug Mode
poetry run get-papers "your_query_here" -d

# Combine CSV Output + Debug
poetry run get-papers "your_query_here" -f output.csv -d
```

### Example Query:
```bash
poetry run get-papers "lung cancer AND (pharma OR biotech) AND 2023[dp]" -f results.csv -d
```

> ✅ Query syntax supports **AND**, **OR**, **[dp]** (Date of Publication), etc. as per [PubMed's Query Guide](https://www.ncbi.nlm.nih.gov/books/NBK25497/).

---

## 📦 Installation Instructions

### Prerequisites
- Python 3.12+
- [Poetry](https://python-poetry.org/docs/)

### Setup Steps

```bash
# 1. Clone the repository
git clone https://github.com/harleenkaur2003/pubmed-research-fetcher.git
cd pubmed

# 2. Install Poetry (if not already installed)
curl -sSL https://install.python-poetry.org | python3

# 3. Install dependencies
poetry install

# 4. Activate shell
poetry shell

# 5. Run the CLI
poetry run get-papers "your query here"
```

---

##  Testing

```bash
# Run unit tests
pytest
```

---

## 🧾 CSV Output Format

| PubmedID | Title | Publication Date | Non-academic Author(s) | Company Affiliation(s) | Corresponding Author
Email |
|----------|-------|------------------|-------------------------|--------------------------|-----------------------------|

---


##  Tools and Technologies Used

- **Language**: Python (typed)
- **Dependency Management**: [Poetry](https://python-poetry.org/)
- **API**: [PubMed E-utilities](https://www.ncbi.nlm.nih.gov/books/NBK25497/)
- **Data Handling**: `pandas`, `xml.etree.ElementTree`, `requests`
- **CLI**: `argparse`
- **Testing**: `pytest`

---

##  LLM & Assistance

- Used **OpenAI ChatGPT-4** for:
  - Code design & structure.
  - Prompt engineering for filters and heuristics.
  - CLI structure and debugging help.
  - README writing and organization.

🔗 [ChatGPT Session Reference](https://chatgpt.com/share/67ce4517-b6c4-8012-9db2-42090ff54487)

---


