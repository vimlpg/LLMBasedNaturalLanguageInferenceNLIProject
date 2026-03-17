# LLM-Based-Natural-Language-Inference-NLI-Project

## Repository Structure
The project is broken down into sequential Jupyter Notebooks and documentation:

1. Pure LLM.ipynb: Establishes the baseline. Evaluates Gemini 2.0 Flash across Zero-Shot, Few-Shot, and Chain-of-Thought (CoT) prompting strategies.

2. Hybrid Model.ipynb: Implements a hybrid routing pipeline. Samples are first passed through a local Cross-Encoder (cross-encoder/nli-distilroberta-base). Low-confidence predictions fall back to Gemini 2.0 Flash.

3. Prompt Repetition.ipynb: Experimental notebook testing the effect of prompt/query duplication on reasoning performance in NLI tasks.

4. Threshold Test.ipynb: Analyses Cross-Encoder confidence distributions to justify the optimal fallback threshold used in the hybrid pipeline.

5. LLM visualisation.ipynb: Generates figures, confusion matrices, class-level F1 distributions, and cost-accuracy trade-off graphs.

6. vibe_coding_log.txt: A detailed vibe coding log recording the chat between human and AI collaboration process.

## Prerequisites

The LLM inference scripts require an API key for Gemini 2.0 Flash.

```bash
os.environ["GOOGLE_API_KEY"] = "Your API Key Here"
```

## Running the Code
The notebooks are designed to be executed sequentially (1 through 4, followed by visualisations).

## Evaluation & Metrics
The pipeline automatically calculates and logs key classification metrics across all experiment conditions, including:

1. Overall Accuracy

2. Macro-F1 Score

3. Class-specific Recall (e.g., Neutral-Recall)

4. API Costs ($)

5. Input / Output Token Counts
