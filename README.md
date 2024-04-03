# PAN 2024 Task 1 Baseline Models

This repo contains the baseline models for the multi-author writing style analysis task at PAN 2024. The dataset and evaluation script, data.zip and evaluator.py respectively, are available on the task's homepage [here](https://pan.webis.de/clef24/pan24-web/style-change-detection.html).

## Usage

### Fine-tuning the models

To fine-tune the models from scratch, extract data.zip to the directory containing finetune_models.py, then run the command 

    py finetune_models.py

from the command line in said directory. This should generate 3 folders containing the fine-tuned versions of the roberta-large model for the 3 subtasks.

### Generating solution files

To generate the solution files for the validation sets, place the script "run_models.py" in the directory that contains the dataset subdirectory and the fine-tuned models, and run the command

    py run_models.py

This should create a new subdirectory named "solutions" that contains the solution files for each subtask. The format for the individual solution files is in accordance with the PAN 2024 submission guidelines. See [here](https://pan.webis.de/clef24/pan24-web/style-change-detection.html#data) for more details.

### Evaluating the results

The script for evaluating the results, "evaluator.py" is a modified version of the evaluation script provided by the PAN 2024 team [here](https://github.com/pan-webis-de/pan-code/tree/master/clef24/multi-author-analysis/evaluator). To run the evaluator, place the "evaluator.py" script in the directory that contains the dataset and solutions subdirectories and run the command

    py evaluator.py -p ./solutions -t ./data -o .

This will create the file "evaluation.txt", which has the F1 scores of the model for the 3 subtasks.