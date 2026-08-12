# Model C MIC Prediction

This repository contains the code used to construct, validate, and apply Model C.

## Repository scope

The repository is intentionally limited to the Model C workflow. Historical development code for earlier models is not included.

### Input

- `input/14B_expanded_pathogen_feature_matrix.csv`  
  Fixed Model 3B pathogen-feature matrix used as the starting pathogen cohort for Notebook 22.

- `input/15B_full_gene_genomic_antibiotic_kernels_outputs.zip`  
  Fixed Model 3B pathogen and antibiotic kernel outputs required by the Model C kernel-construction workflow. This large archive is stored using Git LFS.

- `input/16B_optimised_full_gene_model3_interaction_outputs.zip`  
  Fixed optimised Model 3B interaction-model outputs required by Model C selection, validation, and prediction.

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

6. `27_Model_C_Pathogen_Similarity_and_Prediction_Support.ipynb`  
   Evaluates nearest-training-pathogen similarity and defines the empirical prediction-support range.

7. `28_Model_C_BioSample_Level_MIC_Prediction_Matrix.ipynb`  
   Constructs the completed Model C BioSample-by-antibiotic MIC prediction matrix.

8. `30_New_Ecoli_Pathogen_Model_C_MIC_Prediction.ipynb`  
   Applies the fixed Model C framework to a newly supplied *Escherichia coli* pathogen.

### Comparison notebook

- `32_Three_Model_Pathogen_Out_Validation.ipynb`  
  Compares Models 3, 3B, and C on the common pathogen-out validation cohort.

## External source data

The Model C workflow uses the fixed NCBI Pathogen Detection AMR metadata release:

- Release: `PDG000000004.6171`
- File: `PDG000000004.6171.amr.metadata.tsv`
- Source: https://ftp.ncbi.nlm.nih.gov/pathogen/Results/Escherichia_coli_Shigella/PDG000000004.6171/AMR/PDG000000004.6171.amr.metadata.tsv

This fixed release should be used to reproduce the pathogen AMR metadata and genomic feature inputs used in the analysis. The NCBI metadata file is obtained directly from NCBI and is not stored in this repository.

## Important scope note

This is a compact code-availability repository rather than a one-click reconstruction of every historical upstream model-development step.

Historical Model 3 and Model 3B development notebooks are outside the scope of this repository. The fixed Model 3B reference files required directly by the Model C workflow are supplied under `input/` so that the Model C notebooks can use the same reference inputs as the reported analysis.

Large NCBI genome resources and external software/database resources are obtained outside the repository as required by the notebooks.

## Starting cohort

The supplied `14B_expanded_pathogen_feature_matrix.csv` contains the fixed starting pathogen cohort used for the assembly-availability audit in Notebook 22.

## Software

The notebooks were developed in Google Colab/Python. Individual notebooks install or check external tools when required, including NCBI Datasets, AMRFinderPlus, BLAST, and MAFFT.

## Citation

Please cite the associated manuscript when using this code.

