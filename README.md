# InvLP

## Introduction
This repository contains a snapshot of the Julia code used to generate computational results presented in the following paper:
> Gupta, R., & Zhang, Q. (2020). Decomposition and Adaptive Sampling for Data-Driven Inverse Linear Optimization. arXiv preprint arXiv:2009.07961.

(To be updated to the correct <em>INFORMS Journal of Computing</em> reference)

A preprint of this paper is also available on [arXiv](https://arxiv.org/abs/2009.07961) and our research group's [website](https://qizh.cems.umn.edu/publications/journal-articles).

The code in this repository here requires the following software:
1. [Gurobi](https://www.gurobi.com/)
2. [BARON](https://minlp.com/baron-solver)
3. [Julia](https://julialang.org/) with the following packages:
    - JuMP
    - Gurobi
    - Linear Algebra
    - CSV
    - DataFrames
    - Printf
    - BARON

Details of the specific versions of these softwares that we used can be found in Section 6 of the paper.

Next, we provide the steps that one needs to follow to reproduce our results.

## Reproduction of Results

### Table 1
The code used to generate results presented in this table can be found [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/RandomSampling). The main program is in [RandomSampling.jl](https://github.com/ddolab/InvLP/blob/main/CaseStudy1_Customer_Preference_Learning/RandomSampling/RandomSampling.jl). One needs to edit the values of ``n`` (dimension of (FOP)) and ``J_scheme`` (J_scheme = 1 for the low J case, and J_scheme = 2 to set J as 250 irrespective of the level of noise in data) parameters in line 159 and line 160 of the main program, respectively to generate computational performance data for different $n$ values considered in the paper. The main program will generate 10 random instances of training data for each of the three levels of noise in Table 1 and solve the resulting instances of (IOP) by both Algorithm 1 and Algorithm 2. The results for Algorithm 1 will be available in REPL, and more detailed results for Algorithm 2 will become available in a ``Results`` folder in the root directory that you specify on line 2 of the main program.

We provide the raw results files, that we used to obtain Table 1, in the folder [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/Results/RandomSampling). These can be considered as a sample of what the output from the main program will be.

### Figure 5
Data for the three subplots here can also be obtained by running [RandomSampling.jl](https://github.com/ddolab/InvLP/blob/main/CaseStudy1_Customer_Preference_Learning/RandomSampling/RandomSampling.jl). Specifically, solving the random training instances with Algorithm 2 will generate ``ErrEvolSummary_dim_n_Noise_w.csv`` files where, ``n`` stands for the dimension of (FOP) and ``w`` is such that $`\sigma = 1/w.`$ These ``.csv`` files will have the data on how the prediction error evolves as Algorithm 2 processes data all the 100 experiments one by one. 

Sample output data for this figure can be found [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/Results/RandomSampling/Decomposition/High_fixed_J_250/Results1_dim_25_noise_10).

### Figure 6
The code for generating results in Figure 6 is available [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/AdaptiveSampling); main program is [InstanceGenerator.jl](https://github.com/ddolab/InvLP/blob/main/CaseStudy1_Customer_Preference_Learning/AdaptiveSampling/InstanceGenerator.jl). One needs to edit the values of n and S parameters on lines 11 and 12 of the main program, respectively to generate the different curves shown in Figure 6. Running the main program will store the prediction error evolution data in a ``Results`` folder in the root directory. Sample output data for this program is shown [here](https://github.com/ddolab/InvLP/tree/main/CaseStudy1_Customer_Preference_Learning/Results/AdaptiveSampling). 
### Cost Estimation for Production Planning

### Support
