# LLM Based Natural Language Inference NLI Project
This repository developed an LLM-based inference pipeline to perform Natural Language Inference (NLI) tasks. The system evaluates the logical relationship between premise and hypothesis sentences (Entailment, Contradiction, or Neutral) using the MultiNLI dataset.

We explored standalone Large Language Model prompting strategies (Zero-Shot, Few-Shot, Chain-of-Thought) using Gemini 2.0 Flash, and developed a cost-efficient Hybrid Routing Pipeline that combines local Cross-Encoders with LLM fallbacks. Performance evaluated via standard classification benchmark

## Repository Structure
The project is structured sequentially across several Jupyter Notebooks, supported by visualisation script, development log, dataset, and exported result tables:

- `multinli_1.0_dev_matched.jsonl`: The raw MultiNLI dataset containing the premise-hypothesis pairs used for evaluating the models.

- `nli_comparison.xlsx`: A comprehensive spreadsheet containing all experimental results, including overall metrics (Accuracy, Macro-F1, API Costs), per-class breakdowns, error analysis, and threshold selection data.
   
- `1. Pure LLM.ipynb`: Establishes the baseline. Evaluates Gemini 2.0 Flash across Zero-Shot, Few-Shot, and Chain-of-Thought (CoT) prompting strategies.

- `2. Hybrid Model.ipynb`: Implements a hybrid routing pipeline. Samples are first passed through a local Cross-Encoder (cross-encoder/nli-distilroberta-base). Low-confidence predictions fall back to Gemini 2.0 Flash.

- `3. Prompt Repetition.ipynb`: Experimental notebook testing the effect of prompt/query duplication on reasoning performance in NLI tasks.

- `4. Threshold Test.ipynb`: Analyses Cross-Encoder confidence distributions to justify the optimal fallback threshold used in the hybrid pipeline.

- `LLM visualisation.ipynb`: Generates figures, confusion matrices, class-level F1 distributions, and cost-accuracy trade-off graphs.

- `vibe_coding_log.txt`: A detailed vibe coding log recording the chat between human and AI collaboration process.

## Prerequisites

The LLM inference scripts require an API key for Gemini 2.0 Flash.

```bash
os.environ["GOOGLE_API_KEY"] = "Your API Key Here"
```

The Hybrid and Repetition notebooks require `sentence-transformers` 
for the local Cross-Encoder model.


```bash
pip install sentence-transformers
from sentence_transformers import CrossEncoder
```

## Evaluation & Metrics
The pipeline automatically calculates and logs key classification metrics across all experiment conditions, including:

1. Overall Accuracy

2. Macro-F1 Score

3. Class-specific Recall (e.g., Neutral-Recall)

4. API Costs ($)

5. Input / Output Token Counts
