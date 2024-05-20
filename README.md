# AlphaTherapy

DOI

## Introduction

## Table of contents

## Requirements

## Installation

### 1. Downloading AlphaTherapy

代码：
```
git clone https://github.com/bm2-lab/AlphaTherapy.git

### 2. Downloading example data and example output of AlphaTherapy
Due to the storage limit of git repository, we did not upload our example data and output files of these example data. Instead, we have uploaded the example data and their corresponding output files to the google drive. 

### 3. Installing CellModel

代码：

cd .scripts/gym_cell_model
pip install -e .

## Usage

### 1. Rational design of sequential drug treatments for tumors by AlphaTherapy
As mentioned above, users can specify three paramenters when using AlphaTherapy. Notably, for the drugpool, 如果用户想要使用自定义的drugpool，他应该先构建一个drugpool.
#### 1.1 Drugpool construction
Command
python ./scripts/utils/build_drugset.py --input FDA_drugset.xlsx --output FDA_drugset.pickle

* input:
* output:

This command line will take a input file like “FDA_drugset.xlsx” in the directory “./data/” and will output a file like "FDA_drugset.pickle" in the directory "./scripts/gym_cell_model/gym_cell_model/data". The output file will be used in the gym environment of cell model.

#### 1.2 Configurations
Command
python ./scripts/utils/write_scenario_configs.py --drugset_file_name FDA_drugset.pickle --drugset_short_name FDA --cell_line MCF7 A375 --terminal_step 3 6 9


This command will modify two config files.
(1) env_cpd.config: the environment configurations in /scripts/gym_cell_model/gym_cell_model/config/
  add config of ENV_[drugset_short_name]_[cell_line]_[terminal_step]
(2) RL_agent.config: the RL agents configurations in /scripts/AlphaTherapy/config/
 add config of ENV_[drugset_short_name]_[cell_line]_[terminal_step]_SEED[i] i 1-10
#### 1.3 Run RL agents
Command
nohup python train_RL_agents.py --drugset_short_name FDA --cell_line MCF7 --terminal_step 2 --max_workers 10 &

需要注意的是在运行该命令前，你可以在/scripts/AlphaTherapy/config/RL_agent.config中修改一些RL agent模型参数

This command will 记录所有的运行过程中的pth文件和运行过程中episode变化的文件。

#### 1.4 Merge results
Command
python output_result.py --terminal_step 2

This command will 对参数组成的每个env_name的drug combo结果进行整理，并最后输出一个名为env_name.csv的文件储存在/output/AlphaTherapy/中。

### 2. Downstream analysis


## Citation

## Contacts
bm2-lab@tongji.edu.cn
















