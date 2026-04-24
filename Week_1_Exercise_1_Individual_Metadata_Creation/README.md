# Week 1 — Exercise 1: Individual Metadata Creation

Individual exercise for the Data Management course: create DataCite (XML) and schema.org (JSON-LD) metadata for a publicly available dataset.

## Author

- Yash Annapure (individual submission)

## Dataset

**Ransomware Dataset 2024** — a balanced tabular dataset of Windows PE file features for malware detection and classification, published on Zenodo.

- Landing page / DOI: <https://doi.org/10.5281/zenodo.13890887>
- Creator: Hussain, Amjad (Air University)
- Publisher: Zenodo
- Publication year: 2024
- License: CC-BY-4.0
- Format: CSV (21,752 rows × 77 columns, ~19.72 MB)

Each row represents one Windows PE sample carrying DOS/PE header fields (entry point, image sizes, subsystem, DLL characteristics, section attributes for `.text` and `.rdata`) and sandbox-derived behavioral counters (registry read/write/delete, network DNS/HTTP/connections, process and file activity, DLL calls, API count). Target columns are `Class` (Benign/Malware), `Category`, and `Family` (26 malware families including WannaCry, Ryuk, REvil, LockBit, Cerber, Dharma, Gandcrab, and others). The dataset is balanced with 10,876 benign and 10,876 malicious samples.

## Repository layout

```
Week_1_Exercise_1_Individual_Metadata_Creation/
├── Dataset/
│   └── Final_Dataset_without_duplicate.csv   # source dataset (deduplicated)
├── Week_1_Exercise_1_Individual_Metadata_Creation.ipynb  # metadata builder
├── Dataset_datacite.xml                       # DataCite 4.5 metadata
├── Dataset_schema.org.json                    # schema.org JSON-LD (@type: Dataset)
└── README.md
```

## How to reproduce

The project uses a local `.venv` (Python 3.x with pandas and lxml).

```bash
# activate the shared venv from the repo root
source .venv/Scripts/activate        # Windows (Git Bash)

# run the notebook
jupyter nbconvert --to notebook --execute --inplace \
  Week_1_Exercise_1_Individual_Metadata_Creation.ipynb
```

Re-executing the notebook regenerates `Dataset_datacite.xml` and `Dataset_schema.org.json` from the CSV.

## Metadata standards applied

- **DataCite Metadata Schema 4.5** (`http://datacite.org/schema/kernel-4`) — required properties (Identifier, Creator, Title, Publisher, PublicationYear, ResourceType) plus Subjects, Language, Sizes, Formats, Version, Rights, and Description (Abstract).
- **schema.org Dataset** (`https://schema.org/Dataset`) — `@type: Dataset` with identifier, creator (with affiliation), publisher, license, distribution (DataDownload with SHA-256), keywords, and a `variableMeasured` array enumerating all 77 CSV columns.
