# Genetic Algorithm Application

This repository contains three Jupyter notebook experiments that apply genetic algorithms to:

1. The 0/1 knapsack problem.
2. Filter-based feature selection.
3. Wrapper-based feature selection.

## Project Layout

| Notebook | Purpose | Default input |
| --- | --- | --- |
| `knapsack.ipynb` | Select items subject to a bag capacity constraint | `dataset/question_1/knapsack-data/10_269` |
| `filter_ga.ipynb` | Select features using a classifier-independent fitness function | `dataset/question_2/wbcd/wbcd.data` and `wbcd.names` |
| `wrapper_ga.ipynb` | Select features using Naive Bayes classification accuracy | `dataset/question_2/wbcd/wbcd.data` and `wbcd.names` |

The repository also includes larger knapsack instances (`100_995` and `23_10000`) and the Sonar dataset. Change the input path in the relevant notebook to use them.

## Requirements

- Python 3
- Jupyter Notebook or JupyterLab
- NumPy
- pandas
- matplotlib
- scikit-learn
- DEAP

Install the Python packages with:

```bash
pip install jupyter numpy pandas matplotlib scikit-learn deap
```

## Running the Experiments

Start Jupyter from the repository root:

```bash
jupyter notebook
```

Open and run one of the notebooks. The notebooks use five GA runs with seeds `42`, `52`, `62`, `72`, and `82`, a population size of 50, and 100 generations. They also plot convergence using the average fitness of the five best individuals.

## Recorded Results

The following values are the final results currently saved in the notebooks.

### Knapsack

The configured instance has 10 items and capacity 269. The exact optimum for this instance is **295**. The GA's best retained value in each run was:

| GA run | Best value retained | Total weight | Optimal? |
| ---: | ---: | ---: | :---: |
| 1 | 294 | 260 | No |
| 2 | 293 | 249 | No |
| 3 | 295 | 269 | Yes |
| 4 | 294 | 260 | No |
| 5 | 295 | 269 | Yes |

The GA reached the optimum in 2 of 5 runs. The best value observed was 295, and the mean best value across runs was 294.2.

### Filter GA

The filter-based experiment uses the WBCD dataset. Its saved final output currently contains one completed result:

| GA run | Final fitness | Classification accuracy |
| ---: | ---: | ---: |
| 1 | 0.9491201839 | 0.9385964912 (93.86%) |

The notebook output does not currently contain final result lines for runs 2-5, so no values are inferred for those runs. Rerun the notebook to regenerate the complete result set.

### Wrapper GA

The wrapper-based experiment evaluates selected features with Naive Bayes. Its saved final results are:

| GA run | Final fitness | Classification accuracy |
| ---: | ---: | ---: |
| 1 | 1.0 | 0.9561403509 (95.61%) |
| 2 | 1.0 | 0.9385964912 (93.86%) |
| 3 | 1.0 | 0.9122807018 (91.23%) |
| 4 | 1.0 | 0.9561403509 (95.61%) |
| 5 | 1.0 | 0.8947368421 (89.47%) |

The wrapper GA achieved fitness 1.0 in all five recorded runs. The mean recorded classification accuracy was 92.98%, with a best accuracy of 95.61%.

## Notes

- A chromosome uses binary values to represent whether an item or feature is selected.
- The knapsack fitness rewards total item value while penalizing capacity violations.
- Feature-selection accuracy depends on the train/test split and classifier evaluation implemented in each notebook.