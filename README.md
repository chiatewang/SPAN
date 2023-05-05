# Subgenomic RNAs Profile ANalysis (SPAN)

## Subgenomic RNAs Profile ANalysis (SPAN): Profiling of Noncanonical Subgenomic RNAs in SARS-CoV-2 Variants.

### Description:

This repository and pipeline is for the work reported in the manuscript "Profiling of Noncanonical Subgenomic RNAs in SARS-CoV-2 Variants."

The purpose of this pipeline is to process Next Generation Sequencing (NGS) data. 
This script maps the reads against the SARS-CoV-2 genome and generates junction coordinates from splice alignments; junction coordinates next process using python script to identify subgenomic RNAs and finally visualize using R shiny.

All scripts can be run independently. Execute any script for detailed instructions on how to run them.

### Hareware/software requirements: 

1. Linux or MacOS
2. R (version 4.1)
3. python (version 3.8.10)

### Installation:

Environments setup:

    $ cd {path_to_SPAN_folder}/SPAN_v1
    $ conda env create -f ~/SPAN_v1/SPAN.yml -n SPAN
    $ conda activate SPAN
    $ Rscript install.R
         
### Usage:  
1. Activate conda environment.
  
    $ conda activate SPAN
    
2. Prepare fastq files in ~/SPAN_v2/{variant_name} folder
    
    # We provide testing data 
    # Please using SRAToolkit fasterq-dump function to get two fastq for 
    each sra run
    
3. Prepare sample.txt

    $ python ~/SPAN_v2/scripts/generate_sample_list.py
    
4. Executing SPAN pipeline with snakemake
  
    $ snakemake -c1

5. Data visualization
    
    $ Rscript Plot_Profiling.R
    # Venn Diagram page: We provide download buttom for 
    boxplot input "sgRNA_intersection_list.csv".
    # Junction Site Sashimi Plot page: Users can change the parameters to 
    filter out several noncanonical sgRNA junction events.
    # Boxplot page: Each plot can be downloaded separately.
