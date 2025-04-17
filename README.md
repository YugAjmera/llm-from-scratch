# llm-from-scratch
Code to write, train and fine-tune "famous" LLMs from scratch in Pytorch.

## Load a model
```
# Load GPT2-models: "gpt2", "gpt2-medium", "gpt2-large", "gpt2-xl"
from src.load_gpt2 import GPT2_model
model = GPT2_model("gpt2").to(device)

# Load pretrained version
model = GPT2_model.from_pretrained("gpt2").to(device)
```

## Instruction Fine-tune on Alpaca GPT-4 dataset
The [Alpaca dataset](https://github.com/tatsu-lab/stanford_alpaca/tree/main) is a synthetic dataset developed by Stanford researchers using the OpenAI davinci model to generate instruction/output pairs and fine-tuned Llama. The dataset covers a diverse list of user-oriented instructions, including email writing, social media, and productivity tools.

We'll use an [updated version]((https://github.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM)) that, instead of davinci-003 (GPT-3), uses GPT-4 to get an even better model.
```
wget https://raw.githubusercontent.com/Instruction-Tuning-with-GPT-4/GPT-4-LLM/main/data/alpaca_gpt4_data.json
```
The Alpaca-GPT4 dataset is just a single JSON file, that contains 52K instruction-following data generated by GPT-4 with prompts in Alpaca style. 
```
instruction: str, describes the task the model should perform. 
                  Each of the 52K instructions is unique.
input:       str, optional context or input for the task.
output:      str, the answer to the instruction as generated by GPT-4.
```


