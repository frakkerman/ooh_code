# Pricing and Offering of Out-of-Home Delivery

This project contains code for the paper titled "Learning Dynamic Selection and Pricing of Out-of-Home Deliveries". Contact us if you are interested in the working paper (under review). 

## Citation

We still need to add a reference to our paper.

## Environment

The code is written in Python 3.10. We use PyTorch 2.0.0 to model neural network architectures and hygese 0.0.0.8, the Python HGS implementation. A requirements.txt details further requirements of our project. We tested our project on a Windows 11 environment, and a high-performance Linux cluster.


## Folder Structure
The repository contains the following folders:

- **`Environments/`**: Contains the problem and all related data.
- **`Src/`**: Contains the main code for all algorithms.
  - **`Algorithms/`**: Contains all algorithmic implementations.
  - **`Utils/`**: Contains utility functions, e.g., data loading, actor and critic class structure, prediction models.


On the first level you can see run.py which implements the overall policy training and evaluation loop. For running PPO we use a seperate file called run_ppo.py.

### Src 

On the first level you can see a parser.py, wherein we set hyperparameters and environment variables, and config.py, which preprocesses inputs.


`Algorithms`: 
* Agent.py: Groups several high-level agent functionalities
* Baseline.py: Contains the baseline, StaticPricing.
* DSPO.py: Contains our proposed contribtuoon, Dynamic Selection and Pricing of OOH (DSPO)
* Heuristic.py: Conntains the benchmark heuristics by Yang et al. (2016).
* PPO.py: Contains the Gaussian PPO policy, as proposed in Schulman et al. (2017)

`Utils`: 
* Actor.py and Critic.py: Contain the neural network architectures for actor and critic respectively.
* Basis.py: Contains the state representation module.
* Predictors.py: Contains the prediction models used for DSPO and the linera benchmark.
* Utils.py: Contains several helper functions such as plotting.

### Environments
* `OOH`: Contains the implementation of the OOH environments and the used data.


## To the make the code work

 * Create a local python environment by subsequently executing the following commands in the root folder
	* `python3 -m venv venv`
	* `source venv/bin/activate`
	* `python -m pip install -r requirements.txt`
	* `deactivate`

 * `Src/parser.py` Set your study's hyperparameters in this file, e.g., which environment to use or setting learning rates
 
 * `run.py` Execute this file using the command line `python3 run.py`.
 
 * Note that you might have to adapt your root folder's name to `ooh_code`
 
 * Note that `hygese.py` requires a slight change to one source file when running with `--load_data=True`, this change is indicated when running the code
 
## License
* [MIT license](https://opensource.org/license/mit/)
* Copyright 2023 © [Fabian Akkerman](https://people.utwente.nl/f.r.akkerman), [Peter Dieter](https://en.wiwi.uni-paderborn.de/dep3/schryen/team/dieter/88592), [Martijn Mes](https://www.utwente.nl/en/bms/iebis/staff/mes/)

## Bibliography

### Data sets used

Parallelization of a Two-Phase Metaheuristic for Routing Problems with Time Windows
Hermann Gehring and Jörg Homberger
Journal of Heuristics 2002

2021 Amazon last mile routing research challenge: Data set
Daniel Merchan, Jatin Arora, Julian Pachon, Karthik Konduri, Matthias Winkenbach, Steven Parks and Joseph Noszek
Transportation Science 2022

### Benchmarks

Proximal Policy Optimization Algorithms
John Schulman, Filip Wolski, Prafulla Dhariwal, Alec Radford and Oleg Klimov
ArXiv preprint 2017

Choice-Based Demand Management and Vehicle Routing in E-Fulfillment
Xinan Yang, Arne K. Strauss, Christine S. M. Currie, and Richard Eglese
Transportation Science 2016 50:2, 473-488 

