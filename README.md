# LLM-Based-Natural-Language-Inference-NLI-Project
Repository Structure
The project is broken down into sequential Jupyter Notebooks, analytical tools, and documentation:

1. Pure LLM.ipynb: Establishes the baseline. Evaluates Gemini 2.0 Flash across Zero-Shot, Few-Shot, and Chain-of-Thought (CoT) prompting strategies.

2. Hybrid Model.ipynb: Implements a hybrid routing pipeline. Samples are first passed through a local Cross-Encoder (cross-encoder/nli-distilroberta-base). Low-confidence predictions fall back to Gemini 2.0 Flash.

3. Prompt Repetition.ipynb: Experimental notebook testing the effect of prompt/query duplication on reasoning performance in NLI tasks.

4. Threshold Test.ipynb: Analyzes Cross-Encoder confidence distributions to justify the optimal fallback threshold used in the hybrid pipeline.

LLM visualisation.ipynb: Generates figures, confusion matrices, class-level F1 distributions, and cost-accuracy trade-off graphs (saved to figures/).

vibe_coding_log.txt: A detailed development log recording the prompt-driven human-AI collaboration process and iterative troubleshooting.

LLM_Group Report.docx: The final academic report containing literature review, methodology, comprehensive results, and evaluation.

🚀 Getting Started
Prerequisites

To run these notebooks, you will need Python 3.8+ and an active internet connection to query the Gemini API and download Hugging Face models.

Bash
# Clone the repository
git clone https://github.com/your-username/repo-name.git
cd repo-name

# Install required packages
pip install pandas numpy scikit-learn transformers matplotlib jupyter tqdm
Environment Variables

The LLM inference scripts require an API key for Gemini 2.0 Flash. Set your API key in your environment before launching Jupyter:

Bash
export GEMINI_API_KEY="your_api_key_here"
💻 Running the Code
The notebooks are designed to be run sequentially. Open your Jupyter environment and start with Notebook 1:

Bash
jupyter notebook
⚠️ Important Note on Scaling (IOPub Message Rate Limit)

If you intend to scale the inference up to the full 2,000+ sample evaluation, the heavy logging from tqdm progress bars and API calls may crash the default Jupyter output buffer, resulting in an IOPub message rate exceeded error and loss of in-memory variables.

To prevent this, launch Jupyter with an increased message rate limit:

Bash
jupyter notebook --NotebookApp.iopub_msg_rate_limit=10000
📊 Evaluation & Metrics
The pipeline automatically calculates and logs key classification metrics across all experiment conditions, including:

Overall Accuracy

Macro-F1 Score

Class-specific Recall (e.g., Neutral-Recall)

API Costs ($)

Input / Output Token Counts

Use LLM visualisation.ipynb after generating predictions to view the Cost-Accuracy Trade-off by Strategy.
