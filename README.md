# GEBench: Benchmarking Image Generation Models as GUI Environments

<div align="center">

[![Paper](https://img.shields.io/badge/Paper-arXiv-red)](./assets/GEBench.pdf)
[![Project Page](https://img.shields.io/badge/Project-Page-blue)](YOUR_PROJECT_PAGE_URL)
[![Dataset](https://img.shields.io/badge/Dataset-HuggingFace-green)](https://huggingface.co/datasets/stepfun-ai/GEBench)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Task: GUI Generation](https://img.shields.io/badge/Task-GUI%20Generation-1E90FF)

</div>

![Benchmark Comparison](./assets/teaser.jpg)

## Features

- **5 Data Types**: Type 1 (single-step), Type 2 (multi-step), Type 3 (text-fictionalapp), Type 4 (text-realapp), Type 5 (grounding)
- **Bilingual Support**: Automatic Chinese/English prompt selection based on folder naming
- **5-Dimensional Metrics**: goal, logic, consistency, ui, quality

## Quick Start

### Installation

```bash
# Clone repository
git clone https://github.com/stepfun-ai/GEBench
cd GEBench

# Create conda environment
conda create -n gebench python=3.10 -y
conda activate gebench

# Install dependencies
pip install -r requirements.txt
```
### Data

The GEBench data is available on HuggingFace:

📊 **[StepFun-ai/GEBench](https://huggingface.co/datasets/stepfun-ai/GEBench)** - HuggingFace Datasets Hub

To download:

```bash
cd /path/to/GEBench
git clone https://huggingface.co/datasets/stepfun-ai/GEBench ./data
```

### Generate Images

```bash
python scripts/generate.py --data-type type1 --data-folder data/01_single_step --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY
python scripts/generate.py --data-type type2 --data-folder data/02_multi_step --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY
python scripts/generate.py --data-type type3 --data-folder data/03_trajectory_text_fictionalapp --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY
python scripts/generate.py --data-type type4 --data-folder data/04_trajectory_text_realapp --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY
python scripts/generate.py --data-type type5 --data-folder data/05_grounding_data --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY

# With multiple workers
python scripts/generate.py --data-type type1 --data-folder data/01_single_step --output-dir outputs/gemini --gemini-api-key YOUR_GEMINI_API_KEY --workers 4
```

### Evaluate Results

```bash
python scripts/evaluate.py --data-type type1 --output-folder outputs/gemini/01_single_step --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY
python scripts/evaluate.py --data-type type2 --output-folder outputs/gemini/02_multi_step --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY
python scripts/evaluate.py --data-type type5 --output-folder outputs/gemini/05_grounding_data --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY

# With multiple workers
python scripts/evaluate.py --data-type type1 --output-folder outputs/gemini/01_single_step --dataset-root data --openai-api-key YOUR_OPENAI_API_KEY --workers 4
```
