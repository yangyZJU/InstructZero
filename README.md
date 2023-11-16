# InstructZero 代码解读，欢迎指正

# InstructZero: Efficient Instruction Optimization for Black-Box Large Language Models



## Installation
- Create env and download all the packages required as follows:
```
conda create -n InstructZero
conda install pytorch==1.13.1 torchvision==0.14.1 torchaudio==0.13.1 pytorch-cuda=11.6 -c pytorch -c nvidia
conda install botorch -c pytorch -c gpytorch -c conda-forge
pip install -r requirements.txt # install other requirements
```

## Usage
1. Firstly, you need to prepare your OPENAI KEY.
```
export OPENAI_API_KEY=Your_KEY
```
2. Secondly, run the script to reproduce the experiments.
```
bash experiments/run_instructzero.sh
```

## Hyperparameters
Here we introduce the hyperparameters in our algorithm.
- instrinsic_dim: the dimension of the projection matrix, default=10
- soft tokens: the length of the tunable prompt embeddings, you can choose from [3, 10]

## Frequently Asked Questions
- API LLMs and open-source LLMs support: currently, we only support for Vicuna-13b and GPT-3.5-turbo (ChatGPT), respectively. We will support more models in the next month (July). Current Plan: WizardLM-13b for open-source models and Claude, GPT-4 for API LLMs.
- Why is the performance of [APE](https://github.com/keirp/automatic_prompt_engineer) quite poor on ChatGPT? Answer: we only have access to the textual output from the black-box LLM, e.g., ChatGPT. So we could not calculate the log probability as the score function in InstructZero as original APE.
- Cost for calling ChatGPT API: On the single dataset(e.g., EN-DE dataset), the estimated cost is $1. We will merge the cost computation function into our repo. Stay tuned!
- How long does it take to run one task? It is supposed to be less than 10 minutes.



### Citation
Please consider citing our paper if you used our code, or results, thx!
```
@article{chen2023instructzero,
  title={InstructZero: Efficient Instruction Optimization for Black-Box Large Language Models},
  author={Chen, Lichang and Chen, Jiuhai and Goldstein, Tom and Huang, Heng and Zhou, Tianyi},
  journal={arXiv preprint arXiv:2306.03082},
  year={2023}
}
```
