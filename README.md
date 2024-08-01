### Point-Scale PPE experiment at NEON Sites using CLM5
This document outlines the steps and methods for carrying out point-scale Parameter Perturbation Experiments (PPE) in CLM5 for NEON sites. It provides a detailed guide for setting up, executing, and analyzing PPEs to study the impact of different parameters in CLM5.

The perturbation parameter experiment involves using different parameter combinations to run various CLM configurations for each set of parameters. The initial step is to identify the parameters that influence the processes you are interested in.

#### Step 1: Create Your Base Cases

Establish separate cases for both spinup and production phases to ensure efficient simulations.
- **Configuration**: Point simulations should ideally be set up to run on the Casper machine for optimal performance.
- **File Organization**: Store your base cases in a structured folder, such as:
 ```
 .../ctsm/cime/scripts/basecases/
 ```

#### Step 2: Create Your Spreadsheet

When creating your spreadsheet, it is advisable to start with a template. Begin by duplicating an existing example, such as the [Ameriflux Tower Spreadsheet]() or the [Global PPE Spreadsheet](). These templates provide a solid foundation for customization.

**2.1 Customize Parameters**

- **Add/Remove Parameters**: Adjust the spreadsheet to fit your needs, ensuring all relevant parameters are included.
- **Parameter Propagation**: Ensure that `pft_mins` and `pft_maxs` are correctly propagated across all relevant tabs to maintain consistency and accuracy.

**2.2 Publish Your Spreadsheet**

Share your main spreadsheet by publishing it to the web:
  1. Go to **File > Share > Publish to Web**.
  2. Select the main spreadsheet for publishing.
  3. Choose the **CSV** format from the dropdown menu.
  4. Click **Publish** and copy the provided URL.

**URL Format**: Ensure the URL ends in the following format for proper CSV access:
```
  /pub?gid=1732324005&single=true&output=csv
```
#### Step 3: Write Paramfiles and `nl_mods`

Set up and configure the necessary files for your simulation, ensuring you have the correct tools and environment. LHC (Latin Hypercube Sampling) provides better parameter space coverage, resulting in more representative samples and improved accuracy. This is particularly beneficial when exploring complex systems with high-dimensional input spaces, as it efficiently covers the entire space while minimizing the number of samples required. The `template.ipynb` file is used to perturb the parameters. It provides a step-by-step guide on creating different parameter configurations and saving the newly created and updated CLM5 parameter file.

![image](https://github.com/user-attachments/assets/f726d622-9a0f-4b17-bb62-c1de9c598360)

**3.1 Clone the `ppe_tools` Repository**
- **Access Cheyenne**: Log into your Cheyenne account.
- **Clone Repository**: Use the following commands to clone the `ppe_tools` repository into your home directory:
```
cd ~
git clone git clone https://github.com/djk2120/ppe_tools.git
 ```
**3.2 Check for Conda Installation**
a) Verify Conda: Check if Conda is installed by running:
```
which conda
```
You should see a path output similar to `p/glade/work/djk2120/miniconda3/bin/conda`. If no path is returned, proceed to install Miniconda.
 **3.3 Install Miniconda (If Necessary)**
 - Create Directory: Make a directory for Miniconda:
```
mkdir -p ~/miniconda3
```
- Download and Install Miniconda:
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
```
- Remove the installer script:
```
rm -rf ~/miniconda3/miniconda.sh
```          
- Set up Conda for your shell:
```
~/miniconda3/bin/conda init bash
~/miniconda3/bin/conda init zsh
```
**3.4 Create the ppe_py Python Environment**
Enter the `ppe_tools` directory:
```
cd ppe_tools
```
*Create Environment:* Set up the `ppe_py` environment using the provided `environment.yml` file:

```
conda env create -f environment.yml
```
**Note**: This process may take some time to complete.

*3.4.1 Log in to jupyterhub*

See [here](https://arc.ucar.edu/knowledge_base/70549913) for help

*3.4.2 Customize the `template.ipynb` Notebook*
- In the left sidebar, navigate to `ppe_tools/params/template.ipynb`.
- Make a copy of the template for your specific experiment.
- Open the duplicated notebook and ensure the ppe_py environment is the active Python kernel (found in the top right corner).
- Modify the notebook as necessary to fit your experimental requirements.

#### Step 4: Configure the Job Scripts

Prepare and configure the job scripts required to run your simulation ensemble.

- *Edit Job Scripts*: Access the job script templates and adjust parameters such as job name, wall time, and resources to align with your experimental needs.
- *Ensure Compatibility*: Double-check that all paths and dependencies are correctly referenced in the scripts.

#### Step 5: Submit the Ensemble

Submit your prepared ensemble of simulations for execution on the designated computing resources.
- Use the appropriate command or script to submit your job ensemble to the scheduler (e.g., using qsub, sbatch, etc.).
- Keep track of the job status and ensure all simulations run as expected.

#### Step 6: Collect the History

Gather and organize the output data from your simulations for analysis.

- Collect the output files from the specified directories once the simulations are complete.
- Ensure all historical data is stored in an easily accessible and well-organized format for further analysis.
- Check that all expected data files are present and complete before proceeding to data analysis.
