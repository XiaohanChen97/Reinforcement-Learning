# AlphaTherapy

DOI

## Introduction

## Table of contents

## Requirements

## Installation

### 1. Downloading AlphaTherapy

代码：

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

This command line will

#### 1.2 Configurations
Command
python ./scripts/utils/write_scenario_configs.py --drugset_file_name FDA_drugset.pickle --drugset_short_name FDA --cell_line MCF7 A375 --terminal_step 3 6 9

#### 1.3 Run RL agents
Command
nohup python train_RL_agents.py --drugset_short_name FDA --cell_line MCF7 --terminal_step 2 --max_workers 10 &

#### 1.4 Merge results
Command
python output_result.py --terminal_step 2

### 2. Downstream analysis


## Citation

## Contacts
bm2-lab@tongji.edu.cn
















