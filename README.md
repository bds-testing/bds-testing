# BDS Testing Challenge – Automation Solution (Python)

This repository contains a lightweight Python solution for the 3 tasks described in **BDS_Testing_Usecases_v3.0.pdf**.

## Prerequisites
- Python 3.10+ 
- Internet access (Tests #1 and #2 call public EUMETSAT endpoints)

## Setup but i had some problems with zscaler so why i got some errors at beggining
```bash
python -m venv .venv
source .venv/bin/activate    # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Run each test has the inpute inside the file 

### Test #1 – Search API automation
1) Extract OSDD parameters (XML -> JSON):
```bash
python test1_search_api/extract_parameters.py \
  --pi EO:EUM:DAT:METOP:ASCSZF1B \
  --out test1_search_api/output/parameters.json
```

2) Extract product fields from search results (JSON -> JSON):
```bash
python test1_search_api/extract_products.py \
  --pi EO:EUM:DAT:METOP:ASCSZF1B \
  --dtstart 2025-02-03T04:41:59Z \
  --dtend   2025-02-04T04:41:59Z \
  --out test1_search_api/output/products.json
```

### Test #2 – REST API traversal automation (browse tree)
```bash
python test2_rest_api/product_count.py \
  --collection EO:EUM:DAT:METOP:SOMO12 \
  --date 2023-04-12 \
  --out test2_rest_api/output/products_2023_04_12.csv
```

### Test #3 – Backend log parsing
Put `logs.zip` under `test3_log_parsing/input/logs.zip` (already included in this submission).
```bash
python test3_log_parsing/parse_logs.py \
  --zip test3_log_parsing/input/logs.zip \
  --out test3_log_parsing/output/product_events.log
```

## Outputs
- Test #1: `test1_search_api/output/parameters.json`, `test1_search_api/output/products.json`
- Test #2: `test2_rest_api/output/products_YYYY_MM_DD.csv`
- Test #3: `test3_log_parsing/output/product_events.log`

## Made by Indrit
