# War and Peace (WarAgent): Large Language Model-based Multi-Agent Simulation of World Wars

<a href='https://arxiv.org/abs/2311.17227'><img src='https://img.shields.io/badge/Paper-PDF-red'></a> 
[![Code License](https://img.shields.io/badge/Code%20License-Apache_2.0-green.svg)](https://github.com/agiresearch/WarAgent/blob/main/LICENSE)


<img align="center" width="854" alt="WWI" src="fig/WWI.png">

**Can we avoid wars at the crossroads of history?**
This question has been pursued by individuals, scholars, policymakers, and organizations throughout human history. In this research, we attempt to answer the question based on the recent advances of Artificial Intelligence and Large Language Models (LLMs). We propose **WarAgent**, an LLM-powered multi-agent AI system, to simulate the participating countries, their decisions, and the consequences, in historical international conflicts, including the World War I, the World War II, and the Warring States Period in Ancient China. By evaluating the simulation effectiveness, we examine the advancements and limitations of cutting-edge AI systems' abilities in studying complex collective human behaviors in diverse settings. In these simulations, the emergent interactions among agents also offer a novel perspective for examining the triggers and conditions that lead to war. Our findings offer data-driven and AI-augmented insights that can redefine how we approach conflict resolution and peacekeeping strategies. The implications stretch beyond historical analysis, offering a blueprint for using AI to understand human history and possibly prevent future international conflicts.

## WarAgent Architecture
![architecture](fig/board_and_stick.jpeg)
- Country Agent & Country Agent Interaction: Each country agent is defined by its corresponding country profile. In each round, the agent reacts to the current situation by generating actions available from the action space.
- Country Agent & Secretary Agent Interaction: Each country agent employs a designated “secretary agent” to verify the appropriateness and basic logical consistency of their actions.
- Board and Stick: The Board is designed to manage international relationships and the Stick functions as an internal record-keeping system for each country that represents the domestic statutes.


## QuickStart
### install environment
```
conda create --name waragent python=3.9
conda activate waragent

git clone https://github.com/dhh1995/PromptCoder
cd PromptCoder
pip install -e .
cd ..

git clone https://github.com/agiresearch/WarAgent.git
cd WarAgent
pip install -r requirements.txt
```

### Set up API keys
If you want to use OpenAI model as base LLM:
```
export OPENAI_API_KEY=your_openai_api_key
```
If you want to use Claude model as base:
```
export CLAUDE_API_KEY=your_claude_api_key
```
### Run WarAgent simulation
Currently, WarAgent supports GPT-4 and Claude-2, two of the strongest large language models. The default choice is GPT-4.

To run the default setting (historically accurate setting):
```
cd src
python main.py --model 'your model choice: {claude-2, gpt-4}' --scenario WWI --present_thought_process
```

To use a different trigger event:
```
new_trigger = 'your trigger event'
python main.py --model 'your model choice: {claude-2, gpt-4}' --scenario WWI --present_thought_process --trigger new_trigger
```

### Demo
```
python main.py --model gpt-4 --scenario WWI --present_thought_process
```
link to [video](https://drive.google.com/file/d/1-0dh0Un72LhswMTiPsYn1xTb12xwjy08/view?usp=sharing) with a 5-minute demo using the above command


## News

-[2023.11.28] We release the initial version of WarAgent, including the source code, data, and evaluation metrics.

-[2024.1.3] Add support for gpt-3.5, which is cheaper than gpt-4, but not very smart.

* gpt-3.5 usage:
```
python main.py --model gpt-3.5-turbo-16k --scenario WWI --present_thought_process
```
thought_process can be found in [gpt3.5_output.log](src/log/trigger/gpt3.5_output.log), one round simulation result in [test_2024-01-02_16:00:17.log](src/log/trigger/test_2024-01-02_16:00:17.log).

* gpt-4 usage:
```
python main.py --model gpt-4-1106-preview --scenario WWI --present_thought_process
```
thought_process can be found in [gpt4_output.log](src/log/trigger/gpt4_output.log), two rounds simulation result in [test_2024-01-02_19:15:43.log](src/log/trigger/test_2024-01-02_19:15:43.log).

Tips: price of gpt-4 is 30 times of gpt-3.5

## License
The source code of WarAgent is licensed under [Apache 2.0](https://github.com/tatsu-lab/stanford_alpaca/blob/main/LICENSE). The intended purpose is solely for research use.

## Reference
```
@article{hua2023war,
      title={War and Peace (WarAgent): Large Language Model-based Multi-Agent Simulation of World Wars}, 
      author={Wenyue Hua and Lizhou Fan and Lingyao Li and Kai Mei and Jianchao Ji and Yingqiang Ge and Libby Hemphill and Yongfeng Zhang},
      year={2023},
      eprint={2311.17227},
      archivePrefix={arXiv},
      primaryClass={cs.AI}
}
```
