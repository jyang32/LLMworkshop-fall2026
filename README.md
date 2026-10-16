# Beyond ChatGPT: Methodological Uses of Large Language Models in Social Science

## LLMs as Annotators

This workshop treats a generative large language model (LLM) as a measurement instrument for text. Using populism in political speeches as a running example, participants:

1. Translate a theoretical definition of populism into a prompt and a structured output format;
2. Use Python (LangChain) and a free, open-weight model (`openai/gpt-oss-20b`, served through Groq) to score speeches from the Global Populism Database;
3. Compare the model's scores with those of trained human coders;
4. Examine where the model and the humans disagree, and what that reveals about the measure.

The tutorial is a partial reproduction and extension of Törnberg (2023), [*How to Use Large Language Models for Text Analysis*](https://arxiv.org/abs/2307.13106). No prior experience with LLMs is assumed.

## Repository contents

```
Beyond_ChatGPT_LLM_Methods_Module1.ipynb   The tutorial notebook
requirements.txt                           Python dependencies
data/
  module1_populism_sample.csv              The 24 speeches used in the analysis
  module1_groq_gpt_oss_20b_results.csv     Saved model annotations
```

## Data

The speech texts are not included in this repository. Download the **Global Populism Database (GPD) v2** (Hawkins et al.) from [populism.byu.edu](https://populism.byu.edu/Pages/Data) and place it so the folder looks like this:

```
data/global-populism-dataset-zi/
  gpd_v2_20220427.csv
  speeches_20220427/
    speeches_20220427/
      Albania_Berisha_Campaign_1.txt
      ...
```

Please cite the original authors if you use these data. The files included in `data/` are:

- **Analysis sample** (`module1_populism_sample.csv`): 24 whole speeches balanced across four ranges of the human score. The notebook documents the rule used to select them.
- **Saved results** (`module1_groq_gpt_oss_20b_results.csv`): model annotations from a previous run. You can complete every analysis section from this file without making any API calls.

## Requirements

- Python 3.10 or newer
- [Anaconda](https://www.anaconda.com/download) or [Miniconda](https://docs.conda.io/projects/miniconda/en/latest/)
- Jupyter (installed with the requirements below)
- A free [Groq](https://console.groq.com/) API key, needed only for the optional live annotation sections. Free-tier requests are rate-limited.

## Setup

Clone the repository and create the environment:

```bash
git clone https://github.com/jyang32/LLMworkshop-fall2026.git
cd LLMworkshop-fall2026
conda create -n llmworkshop-fall2026 python=3.12 pip -y
conda activate llmworkshop-fall2026
python -m pip install -r requirements.txt
python -m ipykernel install --user --name llmworkshop-fall2026 --display-name "Python (LLM Workshop Fall 2026)"
```

To make live API calls, create a file named `.env` in the repository folder containing:

```
GROQ_API_KEY=your_key_here
```

Never commit this file; it is already listed in `.gitignore`.

## Running the tutorial

```bash
jupyter lab
```

Open `Beyond_ChatGPT_LLM_Methods_Module1.ipynb`, select the **Python (LLM Workshop Fall 2026)** kernel, and run the cells from top to bottom. Live API calls are off by default; to make them, set `RUN_LIVE_DEMO = True` (one call) or `RUN_LIVE_BATCH = True` (up to 24 calls) in the configuration cell.

## References

- Hawkins, K. A., Aguilar, R., Castanho Silva, B., Jenne, E. K., Kocijan, B., & Rovira Kaltwasser, C. (2019). *Global Populism Database*. [populism.byu.edu](https://populism.byu.edu/Pages/Data).
- Törnberg, P. (2023). How to use Large Language Models for Text Analysis. [arXiv:2307.13106](https://doi.org/10.48550/arXiv.2307.13106).
