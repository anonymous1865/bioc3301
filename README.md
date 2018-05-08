The bioc3301 repository contains all of the unique scripts used in the bioc3301 project. 

The following serves as both a narrative and a structural guide to both core and downstream analysis carried out for BIOC3301 research project "Mainstream Ecological Tools Reveal Temporally Dynamic Core Microbiome in Central London".

This README begins with a description of the directories and then a protocol for how analysis in each was conducted. We do this so that the reader is not only aware of how we structured our analysis, but also so they understand each step in the analysis.

There are five directories, all containing multiple scripts that were submitted as jobs the HPC Cirrus at the EPCC:

1) core_analysis (PROTOCOL INCLUDED)
2) merged_analysis (PROTOCOL INCLUDED)
3) core_microbiome_analysis_1718 (PROTOCOL INCLUDED)
4) editing_scripts
5) statistical_scripts

You will note core_analysis (3X) refers to the core pipeline analysis performed individually on years 2016, 2017 and 2018. This was carried out using QIIME scripts and involves taking the raw data from Illumina alongside a metadata mapping file, pairing both reads, demultiplexing the Illumina data (using GoLay barcodes) and picking OTUs against a Silva 16S rRNA referencing database.
- join_paired_ends: This script was used to join the read 1 and read 2 produced by the Illumina MiSeq sequencing platform. 
- demultiplex_otus: This script then utilised the index provided by the Illumina MiSeq to demultiplex the OTUs. This was necessary because we only used one Illumina sequencing chip - it would have been impossible to keep track of different sample IDs and fragment information otherwise. 
- pick_silva_otus: Takes the fully prepared sequences (seqs.fna) and picks OTUs at a 97% sequence identity threshold against the SILVA 16S rRNA referencing database.
- core_diversity_analysis_18
This represents the entirety of the core analysis pipeline as OTUs have now been produced and are ready for further analysis.

You will note that merged_analysis (4X) refers to the merged total microbiomes in years 2016, 2017 and 2018. This was the first downstream analysis we attempted and it involved merging the OTUs we produced in the core analysis for each year (see core_analysis folder) and performing core diversity analysis.
- Merge_maps: This scripts takes the .tsv metadata mapping files from each year and combines them so that merged analysis can occur. 
- Merge_all_otus: This takes the .biom tables producing by picking OTUs in the core analysis of each each and merges them together to create a merged .biom table.
- Merged_CDA: This performs core diversity analysis to produce PCoA plots and other metrics etc. on the merged biom table and correlates it to the merged mapping file.
- Gordon_merged_cda: This script we used to carry out merged 16-17-18 CDA but only on the samples collected at Gordon Square Park so we could compare them temporally for significance. (27/30 samples). This incorporated a .biom table that was created using the remove_non_gordon_otus in editing scripts folder.
- We then carried out various statistical analyses.


You will note that core_microbiome_analysis (2X) refers to the analysis carried out on the combined CORE microbiomes of 2017 and 2018. An identical analysis was also carried out between years 2016:2017, 2016:2018 and 2016:2017:2018. We have elected to not include the specific scripts for these analyses as they are redundant and only involve very minor changes in file path - this was part of the original design plan. 
- identify_core_microbiome_CDA_1718: This script incorporated a 1718 only .biom table which required the use of remove_16_otus (editing_scripts) on the combined 16/17/18 .biom OTU table. It produced various .biom tables based on various core microbiome definitions (% presence in all samples). We elected to choose 50%. 
- core_microbiome_CDA_1718: This script carried out core diversity analysis on the above defined core microbiome table (50% definition) using the merged mapping file (there was no need to update the latter). 

You will note that editing_scripts (3X) refers to those scripts which were used for removing one set of year's OTUs in pairwise core-microbiome construction (removed 16 for 17-18 pair in this example), removal of samples/OTUS not taken in gordon square and summarisation of the core microbiome into distinct taxonomical levels. 
- Summarise core microbiome: This script was used to summarise specific taxonomic levels. It is required for the function of some of the statistical tests, particularly the KW test which compared L2 and L3 abundance over time (see stats_scripts folder). 
- Remove 16_otus: This 'type' of script was required for the core_merged folder in which we looked at the core microbiome on a pairwise year. Note that other versions named remove 17_otus and remove 18_otus existed. 
- Remove non_gordon_otus: This script removes the  three samples from the .biom table that were not taken in Gordon Square park. It was required for any analysis we carried out in which we wanted to look at the temporal effect on core microbiome - i.e merged 161718 and core_merged 1718.

You will note that statistical_scripts (4X)refers to the ANOSIM and KW tests we carried out between years (17/18 specific scripts also given here) as well as scripts we used for the generation of 2D PCoA plots and UPGMA-associated trees using the Interactive Tree of Life resource available at the EMBL. 
- anosim_test_1718: We used this script to compare unifrac matrices temporally. Equivalents existed for 1618 and 1718 too.
- create_upgma_for_tree: This script was used to create a upgma plot that could be inputted into a web browser program (Interactive Tree of Life) that represents beta diversity well visually. 
- kw_test_L2L3_1718: Used this script to compare phyla and class abundance temporally.
- make_2D_plot_1718: Used this script to generate 2D PCoA plots that are used in the report.


