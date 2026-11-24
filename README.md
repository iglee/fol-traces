# FOL Pretrain Dataset Generation
Code for generating FOL-Pretrain dataset

## Data Generation Instructions
Run every command from the repository root. The scripts import `src.*`, so they are run as modules (`python -m`).

- To generate FOL rule sets generation with SymPy, run
```python -m src.fol_generator``` 
Some post processing might be required, as detailed in `scripts/process_generated_rules.py` (`python -m scripts.process_generated_rules`) for organizing the resulting data into post processing format for the next steps.

- Then, with GPT-4 or GPT-3.5, generate predicates like `Exists(x)` or `Relates(x,y)`. Some results from example runs with predicates are shown in `data/batches` and `data/predicate_prompted`.
  
First, to generate predicate prompts and batch prompt the models, run

```python -m scripts.batch_prompt_predicates```

Then, retrieve the batches

```python -m scripts.retrieve_gpt_batches```

Finally, process the resulting files

```python -m scripts.process_prompted_predicates```

- To generate certain FOL datasets with rules and predicates, run
  
```python -m src.generate_data```
