# amoA_AOB_primer_design

I have clustered 1205 amoA-AOB functional genes with 0.96 similarity with mfpcluster based on the suggestion of MetaFunPrimer; The alignment of cluster representative genes against 1931 soil metagenome files have also done by mfpsearch. This repo will start with mfpcount:

First, go to the folder with diamond_results:   
`cd /mnt/home/f0008426/projects/amoA_AOB/get_LAMP_Meta_abun_0.96_AOB/Meta_abun_AOB/redesign_AOB_primers`  

Summarize the results of aligning amoA-AOB cluster representative genes against 1931 metagenome files:  
`mfpcount -i 0.96.amoA.AOB.pro.fa.diamond_results`

Prepare soil metagenome abundant amoA-AOB for primer design:
`mfpprepare -n /mnt/home/f0008426/projects/amoA_AOB/amoA_AOB_1205_input_data/fungene_9.6_amoA_AOB_1205_unaligned_nucleotide_seqs.fa -p /mnt/home/f0008426/projects/amoA_AOB/amoA_AOB_1205_input_data/fungene_9.6_amoA_AOB_1205_unaligned_protein_seqs.fa -c 0.96.amoA.AOB.pro.fa.clstr -t 0.96.amoA.AOB.pro.fa.diamond_results.recommended_clusters.s_score -m /mnt/home/f0008426/projects/amoA_AOB/amoA_AOB_1205_input_data/pro_trans_nuc_name.txt`

Primer design for soil abundant amoA-AOB genes:

