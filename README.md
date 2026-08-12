# Model C MIC Prediction

This repository contains the code used to construct, validate, and apply Model C.

## Repository scope

The repository is intentionally limited to the Model C workflow. Historical development code for earlier models is not included.

### Input

- `input/14B_expanded_pathogen_feature_matrix.csv`  
  Fixed Model 3B pathogen-feature matrix used as the starting pathogen cohort for Notebook 22.

### Notebooks

Run/order of the Model C workflow:

1. `22_Audit_Ecoli_Assembly_Availability.ipynb`  
   Audits assembly availability for the starting pathogen cohort.

2. `23_Targeted_AMR_Sequence_Data_Interface.ipynb`  
   Defines the targeted AMR locus panel and extracts targeted nucleotide sequences from the selected assemblies.

3. `24_Targeted_AMR_Sequence_Alignment_and_Kernel.ipynb`  
   Aligns the targeted sequences and constructs candidate sequence-similarity kernels.

4. `25_Model_C_Pathogen_Kernel_Candidate_Construction.ipynb`  
   Combines the sequence kernel with the fixed Model 3B pathogen-kernel component to construct Model C pathogen-kernel candidates.

5. `26_Model_C_Nested_Pathogen_Out_Selection_and_Validation.ipynb`  
   Performs nested pathogen-out model selection and validation and fits the final Model C reference model.

6. `30_New_Ecoli_Pathogen_Model_C_MIC_Prediction.ipynb`  
   Applies the fixed Model C framework to a newly supplied *Escherichia coli* pathogen.

## Important scope note

This is a compact code-availability repository rather than a one-click reconstruction of every historical upstream model-development step.

Some notebooks reference fixed outputs produced by earlier Model 3B or intermediate Model C analyses. Those historical development pipelines and generated output archives are outside the scope of this repository. The notebooks are retained in the form used for the reported Model C analyses so that the computational procedures are transparent.

Large NCBI genome resources and external software/database resources are also obtained outside the repository as required by the notebooks.

## Starting cohort

The supplied `14B_expanded_pathogen_feature_matrix.csv` contains the fixed starting pathogen cohort used for the assembly-availability audit in Notebook 22.

## Software

The notebooks were developed in Google Colab/Python. Individual notebooks install or check external tools when required, including NCBI Datasets, AMRFinderPlus, BLAST, and MAFFT.

## Citation

Please cite the associated manuscript when using this code.
