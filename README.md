The bioc3301 repository contains all of the unique scripts used in the bioc3301 project. 

The following serves as both a narrative and a structural guide to both core and downstream analysis carried out for BIOC3301 research project "Mainstream Ecological Tools Reveal Temporally Dynamic Core Microbiome in Central London".

This README begins with a description of the directories so that when they are referenced, the reader is aware of what our aim is at each step in the analysis. 

There are five directories, all containing multiple scripts that were submitted as jobs the HPC Cirrus at the EPCC:
1) core_analysis
2) merged_analysis
3) core_microbiome_analysis_1718
4) editing_scripts
5) statistical_scripts

You will note core_analysis refers to the core pipeline analysis performed individually on years 2016, 2017 and 2018. This was carried out using QIIME scripts and involves taking the raw data from Illumina alongside a metadata mapping file, pairing both reads, demultiplexing the Illumina data (using GoLay barcodes) and picking OTUs against a Silva 16S rRNA referencing database. 
- 

You will note that merged_analysis refers to the merged total microbiomes in years 2016, 2017 and 2018.
- 



You will note that core_microbiome_analysis refers to the analysis carried out on the combined CORE microbiomes of 2017 and 2018. An identical analysis was also carried out between years 2016:2017, 2016:2018 and 2016:2017:2018. We have elected to not include the specific scripts for these analyses as they are redundant and only involve very minor changes in file path - this was part of the original design plan. 
You will note that editing_scripts refers to those scripts which were used for removing one set of year's OTUs in pairwise core-microbiome construction (removed 16 for 17-18 pair in this example), removal of samples/OTUS not taken in gordon square and summarisation of the core microbiome into distinct taxonomical levels. 
You will note that statistical_scripts refers to the ANOSIM and KW tests we carried out between years (17/18 specific scripts also given here) as well as scripts we used for the generation of 2D PCoA plots and UPGMA-associated trees using the Interactive Tree of Life resource available at the EMBL. 

The following are timelines
A. Core_analysis
1) 


B. Total merged microbiome analyis (16/17/18) 

C. Core microbiome analysis (17/18 given as example)
