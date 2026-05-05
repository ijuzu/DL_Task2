# DL_Task2

This project fine-tunes the Microsoft phi-2 model to generate Lithuanian city descriptions using LoRA (Low-Rank Adaptation). 

## Dataset 
The links for each Wikipedia page of all cities and towns in Lithuania were obtained here: 

https://lt.wikipedia.org/wiki/S%C4%85ra%C5%A1as:Lietuvos_miestai
https://lt.wikipedia.org/wiki/S%C4%85ra%C5%A1as:Lietuvos_miesteliai

### Size
- 359 total cities and towns are in the final dataset. 
 - Training set: 80% (285 cites/towns)
 - Test set: 20% (73 cities/towns)

Each example follows an instruction format: 
Instruct: Apibūdink: <miestas>
Output: <aprašymas>

### Dataset fixes
It was found that the original random split put Šešuoliai in both train and test sets. Also, the split put closely named  cities/towns across the train/test boundary - for example, Kretinga in the train split and Kretingalė in the test split, Panevėžys in test and Šilai (Panevėžys) in train. 

Therefore, the data was resplit to read the existing dataset.jsonl and produce new train.jsonl and test.jsonl datasets. These new sets have duplicates removed and groups similarly named cities/towns so they land in the same split. 

## Metrics used for Evaluation: 
- Perplexity
- BLEU-1 score

## All files: 
- main.py: Main file used for dataset creation and running finetune model iterations
- dataset_creation.py: Code for creating dataset from Wikipedia articles
- resplit_dataset.py: Used to resplit the train/test sets
- finetune.py: Model + LoRA adaptation
- evaluate_comparison: Used to evaluate with base model
- test_model.py: For testing
- dataset.jsonl: Dataset with all Lithuanian cities/towns
- train.jsonl: training set (after the resplitting was completed) 
- test.jsonl: testing set (after the resplitting was completed) 
