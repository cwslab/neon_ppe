### Point-Scale PPE experiment at NEON Sites using CLM5
This document outlines the steps and methods for carrying out point-scale Parameter Perturbation Experiments (PPE) in CLM5 for NEON sites. It provides a detailed guide for setting up, executing, and analyzing PPEs to study the impact of different parameters in CLM5.

##### 1. Identify and select parameters of interest
The perturbation parameter experiment involves using different parameter combinations to run various CLM configurations for each set of parameters. The initial step is to identify the parameters that influence the processes you are interested in. After identifying these parameters, you should organize them as shown in this Google sheet [here](https://docs.google.com/spreadsheets/d/1O6ybBLWzTCEbNqFtjetX9FRFfm0T-jsU4R4pTuofPyU/edit?gid=0#gid=0). This [complete list of CTSMS](https://docs.google.com/spreadsheets/d/1OtkaO_uAmafWKR9kgtRC2Ge6d6fkhymngSpben5SJ_Q/edit?gid=340121780#gid=340121780) parameters can be helpful, especially when determining the minimum and maximum values of the parameters.

##### 2. Sampling the CLM5 parameter space (Latin Hypercube)
LHC (Latin Hypercube Sampling) provides better parameter space coverage, resulting in more representative samples and improved accuracy. This is particularly beneficial when exploring complex systems with high-dimensional input spaces, as it efficiently covers the entire space while minimizing the number of samples required.
![image](https://github.com/user-attachments/assets/f726d622-9a0f-4b17-bb62-c1de9c598360)
The template.ipynb file is used to perturb the parameters. It provides a step-by-step guide on creating different parameter configurations and saving the newly created and updated CLM5 parameter file.

##### 3. Submit the Ensemble
