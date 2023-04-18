# Auto-Llama-cpp: An Autonomous Llama Experiment
This is a fork of Auto-GPT with added support for locally running llama models through llama.cpp.
This is more of a proof of concept. It's sloooow and most of the time you're fighting with the too small context window size or the models answer is not valid JSON. But sometimes it works and then it's really quite magical what even such a small model comes up with. 
But obviously don't expect GPT-4 brilliance here.


## Supported Models
---
Since this uses [llama.cpp](https://github.com/ggerganov/llama.cpp) under the hood it should work with all models they support. As of writing this is 
* LLaMA
* Alpaca
* GPT4All
* Chinese LLaMA / Alpaca
* Vigogne (French)
* Vicuna
* Koala

## Installation
run these commands

git clone https://github.com/rhohndorf/Auto-Llama-cpp.git
cd Auto-Llama-cpp
pip install -r requirements.txt

Download https://huggingface.co/eachadea/legacy-ggml-vicuna-13b-4bit/resolve/main/ggml-vicuna-13b-4bit.bin (8GB) and place it in your models folder (for testing I made one in the root directory of this project with another folder called 13B for the size but if you're trying out multiple llms you'll likely have a folder somewhere else for all of them)

Rename "env.template" file to ".env" changing any environment variables that you need (like the path to your recently downloaded model)

run this command to start

python scripts/main.py

once you have things running and can see what it does, try changing ai_settings.yml and scripts/data/prompt.txt to change how the ai behaves
## Model Performance (the experience so far)
---

### Response Quality
So far I have tried 
* Vicuna-13b-4BIT 
* LLama-13B-4BIT

Overall the Vicuna model performed much better than the original LLama model in terms of answering in the required JSON format and how much sense the answers make. I just couldn't get it to stop starting every answer with ### ASSISTANT.
I am very curious to hear how well others models perform. The 7B models seemed have problems with grasping what's asked of them in the prompt, but I tried very little in this direction since the inference speed didn't seem to be much faster for me.

### Inference Speed
The biggest problem at the moment is indeed inference speed. As the agent is self prompting a lot, a few seconds of infernce that are acceptable in a chatbot scenario become minutes and more. 
Testing things like different prompts etc is a pain under these conditions. 

## Discussion
Fell free to add your thoughts and experiences in the [discussion](https://github.com/rhohndorf/Auto-Llama-cpp/discussions) area. What models did you try? How well did they work ou for you? 

## Future Plans
---

1. Add GPU Support via GPTQ
2. Improve Prompts
3. Remove external API support (This is supposed to be completely self-contained agent)
4. Add support for [Open Assistent](https://github.com/LAION-AI/Open-Assistant) models
