# LLM-Based-Natural-Language-Inference-NLI-Project
## Repository Structure
The project is broken down into sequential Jupyter Notebooks, analytical tools, and documentation:

1. Pure LLM.ipynb: Establishes the baseline. Evaluates Gemini 2.0 Flash across Zero-Shot, Few-Shot, and Chain-of-Thought (CoT) prompting strategies.

2. Hybrid Model.ipynb: Implements a hybrid routing pipeline. Samples are first passed through a local Cross-Encoder (cross-encoder/nli-distilroberta-base). Low-confidence predictions fall back to Gemini 2.0 Flash.

3. Prompt Repetition.ipynb: Experimental notebook testing the effect of prompt/query duplication on reasoning performance in NLI tasks.

4. Threshold Test.ipynb: Analyzes Cross-Encoder confidence distributions to justify the optimal fallback threshold used in the hybrid pipeline.

5. LLM visualisation.ipynb: Generates figures, confusion matrices, class-level F1 distributions, and cost-accuracy trade-off graphs.

6. vibe_coding_log.txt: A detailed development log recording the prompt-driven human-AI collaboration process and iterative troubleshooting.

## Prerequisites

To run these notebooks, you will need Python 3.8+ and an active internet connection to query the Gemini API and download Hugging Face models.

The LLM inference scripts require an API key for Gemini 2.0 Flash. Set your API key in your environment before launching Jupyter:

Bash
export GEMINI_API_KEY="your_api_key_here"

## Running the Code
The notebooks are designed to be executed sequentially (1 through 4, followed by visualizations).

Important: Scaling to 2000+ Samples

As noted in our vibe_coding_log.txt, running inference on the full dataset generates heavy logging from tqdm progress bars and API calls. This can overwhelm the default Jupyter output buffer, resulting in an IOPub message rate exceeded error and the loss of in-memory variables.

To prevent crashes during large-scale evaluation runs, launch Jupyter with an significantly increased message rate limit:

Bash
jupyter notebook --NotebookApp.iopub_msg_rate_limit=10000

## Evaluation & Metrics
The pipeline automatically calculates and logs key classification metrics across all experiment conditions, including:

1. Overall Accuracy

2. Macro-F1 Score

3. Class-specific Recall (e.g., Neutral-Recall)

4. API Costs ($)

5. Input / Output Token Counts
