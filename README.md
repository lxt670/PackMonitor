# HFuzzer & PackageHallucination Project

This repository contains two main components for testing package hallucination in code generation models:

## Setup Instructions

1. Install Python dependencies:
```bash
pip install -r requirements.txt
```

## HFuzzer Configuration

To use HFuzzer:

1. **Deploy Local Model**:
   - Download the models you need to test and save them locally (HFuzzer will use this as the target model)
   - Configure the path of your local model in the corresponding script (`HFuzzer/script/vanilla.py` or `HFuzzer/script/RAG_run.py`)

2. **Configure Cloud Model API**:
   - Obtain API credentials for a cloud LLM service (like DeepSeek, HFuzzer will use this as the tester model)
   - Configure the API in `HFuzzer/Framework/Tool.py` 

3. **Run Baseline Scripts**:
```bash
# Run RAG baseline
python HFuzzer/script/RAG_setup.py
python HFuzzer/script/RAG_run.py

# Or run vanilla baseline
python HFuzzer/script/vanilla.py
```

## Package4U Configuration

To test package hallucination with Package4U:
1. **Download Data**:
   - Download the data for Package4U testing (JavaScript and Python code) and save it in `Package4U/PackageHallucination/Data/` directory
   - You can download the data from [here](https://zenodo.org/records/14676377)

1. **Prepare Models**:
   - Download and place models in `Package4U/PackageHallucination/Models/` directory
   - Supported models should be in compatible format

2. **Run Tests**:
```bash
cd Package4U/PackageHallucination

# Test DeepSeek model (1B parameters) on Python code
python run_test.py DeepSeek_1B --language Python

# For JavaScript testing
python run_test.py DeepSeek_1B --language Javascript
```

## Notes

- Ensure you have adequate GPU resources for local model deployment
- Cloud API may require additional configuration (keys, endpoints etc.)
