# Old Italian to Modern Italian Translation

The project compares traditional translation models (MADLAD, NLLB) with large language models (PHI-4, QWEN3) using various prompting strategies.

### `human_ratings.csv`
Human evaluation scores (1-5 scale) for translation quality assessment, containing:
- Source sentences from the dataset
- Model outputs and variants
- Human ratings for quality validation

## Translation Models and Notebooks

#### [`MADLAD.ipynb`](MADLAD.ipynb)
- **Model**: Google MADLAD-400-3B-MT
- **Output**: Italian-to-Italian translation
- **Results**: Stored in `madlad/madlad_translations.csv`

#### [`NLLB.ipynb`](NLLB.ipynb)
- **Model**: Facebook NLLB-200-3.3B
- **Output**: Italian-to-Italian translation
- **Results**: Stored in `nllb/nllb_translations.csv`

### Large Language Models

#### [`PHI-4.ipynb`](PHI-4.ipynb)
- **Model**: Microsoft PHI-4-mini-instruct
- **Approaches**: 
  - Zero-shot prompting (4 variants)
  - Few-shot prompting (4 variants)
- **Prompt Variants**:
  - v0: Expert role-based prompt
  - v1: Simple translation prompt
  - v2: Historical context-aware prompt
  - v3: Italian language prompt
- **Results**: 
  - `phi-4/phi-4_translations.csv` (zero-shot)
  - `phi-4/phi-4_translations_fewshot.csv` (few-shot)

#### [`QWEN3.ipynb`](QWEN3.ipynb)
- **Model**: Qwen3-1.7B
- **Approaches**: Same as PHI-4 (zero-shot and few-shot with 4 variants each)
- **Results**:
  - `qwen3/qwen3_translations.csv` (zero-shot)
  - `qwen3/qwen3_translations_fewshot.csv` (few-shot)

## Evaluation and Analysis

### [`analytics.ipynb`](analytics.ipynb)
Comprehensive analysis notebook containing:
- Performance comparison across all models
- Prompt effectiveness analysis for LLMs
- Visualization of evaluation scores
- Statistical analysis of translation quality
- Cohen's Kappa calculations

### Evaluation Metrics
All models are evaluated using:
1. **Gemini LLM-as-Judge**: Automated scoring (1-5 scale)
   - With historical context
   - Without historical context
2. **Human Evaluation**: Manual quality assessment (1-5 scale)
3. **Cohen's Kappa**: Reliability between human and LLM evaluations

### `kappa_results.csv`
Contains Cohen's Kappa scores measuring agreement between human and LLM evaluations for all model variants and contexts.

## Output Generation

### [`outputs.ipynb`](outputs.ipynb)
Processes all translation results and generates standardized JSONL files for submission:
- Translation files: `Saffron_Mafia-hw2_transl-{model}.jsonl`
- LLM-as-judge files: `Saffron_Mafia-hw2_transl-judge-{model}_{context}.jsonl`

## Directory Structure

```
├── dataset.csv                    # Original Old Italian sentences
├── human_ratings.csv             # Human evaluation scores
├── kappa_results.csv
├── requirements.txt              # Python dependencies
├── Saffron_Mafia_Report_HW2.pdf # Final project report
│
├── MADLAD.ipynb                   # MADLAD translation model
├── NLLB.ipynb                   # NLLB translation model
├── PHI-4.ipynb                  # PHI-4 LLM experiments
├── QWEN3.ipynb                  # QWEN3 LLM experiments
├── analytics.ipynb              # Analysis and visualization
├── outputs.ipynb                # Output file generation
│
├── madlad/                      # MADLAD model results
│   ├── madlad_translations.csv
│   └── madlad_translations_with_eval.csv
├── nllb/                        # NLLB model results
│   ├── nllb_translations.csv
│   └── nllb_translations_with_eval.csv
├── phi-4/                       # PHI-4 model results
│   ├── phi-4_translations.csv
│   ├── phi-4_translations_with_eval.csv
│   ├── phi-4_translations_fewshot.csv
│   └── phi-4_translations_fewshot_with_eval.csv
├── qwen3/                       # QWEN3 model results
│   ├── qwen3_translations.csv
│   ├── qwen3_translations_with_eval.csv
│   ├── qwen3_translations_fewshot.csv
│   └── qwen3_translations_fewshot_with_eval.csv
│
└── outputs/                     # Formatted submission files
    ├── madlad/
    │   ├── Saffron_Mafia-hw2_transl-madlad.jsonl
    │   ├── Saffron_Mafia-hw2_transl-judge-madlad_with_context.jsonl
    │   └── Saffron_Mafia-hw2_transl-judge-madlad_without_context.jsonl
    ├── nllb/
    │   └── [similar structure]
    ├── phi-4/
    │   ├── [zeroshot variants v0-v3]
    │   ├── [fewshot variants v0-v3]
    │   └── [corresponding judge files with/without context]
    └── qwen3/
        └── [similar structure to phi-4]
```


## Best Performing Model Variants

Based on the evaluation results, the following JSONL files contain the best performing variants for each model:

### PHI-4 Best Variants
- **Translation**: [`Saffron_Mafia-hw2_transl-phi-4-zeroshot-v0.jsonl`](outputs/phi-4/Saffron_Mafia-hw2_transl-phi-4-zeroshot-v0.jsonl) (Expert role-based prompt)
- **Evaluation with context**: [`Saffron_Mafia-hw2_transl-judge-phi-4-zeroshot-v0_with_context.jsonl`](outputs/phi-4/Saffron_Mafia-hw2_transl-judge-phi-4-zeroshot-v0_with_context.jsonl)
- **Evaluation without context**: [`Saffron_Mafia-hw2_transl-judge-phi-4-zeroshot-v0_without_context.jsonl`](outputs/phi-4/Saffron_Mafia-hw2_transl-judge-phi-4-zeroshot-v0_without_context.jsonl)

### QWEN3 Best Variants
- **Translation**: [`Saffron_Mafia-hw2_transl-qwen3-zeroshot-v0.jsonl`](outputs/qwen3/Saffron_Mafia-hw2_transl-qwen3-zeroshot-v0.jsonl) (Expert role-based prompt)
- **Evaluation with context**: [`Saffron_Mafia-hw2_transl-judge-qwen3-zeroshot-v0_with_context.jsonl`](outputs/qwen3/Saffron_Mafia-hw2_transl-judge-qwen3-zeroshot-v0_with_context.jsonl)
- **Evaluation without context**: [`Saffron_Mafia-hw2_transl-judge-qwen3-zeroshot-v0_without_context.jsonl`](outputs/qwen3/Saffron_Mafia-hw2_transl-judge-qwen3-zeroshot-v0_without_context.jsonl)

### Traditional Models
- **MADLAD**: [`Saffron_Mafia-hw2_transl-madlad.jsonl`](outputs/madlad/Saffron_Mafia-hw2_transl-madlad.jsonl)
- **NLLB**: [`Saffron_Mafia-hw2_transl-nllb.jsonl`](outputs/nllb/Saffron_Mafia-hw2_transl-nllb.jsonl)

*Note: Best variants are determined based on Gemini evaluation scores as analyzed in `analytics.ipynb`.*

## Dependencies

Install required packages:
```bash
pip install -r requirements.txt
```

Key dependencies:
- `transformers` - Hugging Face models
- `torch` - PyTorch framework
- `pandas` - Data manipulation
- `google-genai` - Gemini API for evaluation
- `matplotlib`, `seaborn` - Visualization
- `scikit-learn` - Evaluation metrics


## 👥 Authors

- Sahar Khanlari
- Marco Natale
