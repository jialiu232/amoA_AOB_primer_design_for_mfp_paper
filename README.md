# amoA_AOB_primer_design

I have clustered 1205 amoA-AOB functional genes with 0.96 similarity with mfpcluster based on the suggestion of MetaFunPrimer; The alignment of cluster representative genes against 1931 soil metagenome files have also done by mfpsearch. This repo will start with mfpcount:    

- First, go to the folder with diamond_results:    
`cd /mnt/home/f0008426/projects/amoA_AOB/get_LAMP_Meta_abun_0.96_AOB/Meta_abun_AOB/redesign_AOB_primers`      

- Summarize the results of aligning amoA-AOB cluster representative genes against 1931 metagenome files:   
`mfpcount -i 0.96.amoA.AOB.pro.fa.diamond_results`    

- Prepare soil metagenome abundant amoA-AOB for primer design:    
`mfpprepare -n /mnt/home/f0008426/projects/amoA_AOB/amoA_AOB_1205_input_data/fungene_9.6_amoA_AOB_1205_unaligned_nucleotide_seqs.fa -p /mnt/home/f0008426/projects/amoA_AOB/amoA_AOB_1205_input_data/fungene_9.6_amoA_AOB_1205_unaligned_protein_seqs.fa -c 0.96.amoA.AOB.pro.fa.clstr -t 0.96.amoA.AOB.pro.fa.diamond_results.recommended_clusters.s_score -m /mnt/home/f0008426/projects/amoA_AOB/amoA_AOB_1205_input_data/pro_trans_nuc_name.txt`    

mfpdesign has not been optimized up to now, I modified the script so that it takes these arguments `java -jar /mnt/research/germs/softwares/Primer_Design/PrimerDesign_latest/PrimerDesign.jar -input amoA_AOB_soilAbund_nucleotide_forPrimerDesign_clustalo-1.2.4_clean.fa -output amoA_AOB_soilAbund_nucleotide_primer_output.txt -subcommand select -productLengthMin 220 -productLengthMax 330 -oligoMinSize 22 -oligoMaxSize 30 -maxMismatches 0 -tempMin 59 -tempMax 61 -hairMax 24 -homoMax 35 -isTreeWeightNeeded f -isHenikoffWeightNeeded f -os linux -assayMax 30 -degenMax 6 -NoTEndFilter t -NoPoly3GCFilter t -PolyRunFilter 4 -GCFilterMin 0.15 -GCFilterMax 0.8` to design the primer for amoA-AOB.    

- Primer design for soil abundant amoA-AOB genes:    
`mfpdesign -i prepped.fungene_9.6_amoA_AOB_1205_unaligned_nucleotide_seqs.fa --min_product_length 220 --max_product_length 330 --min_oligo_length 22 --max_oligo_length 30`    


- Evaluate and optimize to get the final primer outputs:     
`mfpqpcr -i prepped.fungene_9.6_amoA_AOB_1205_unaligned_nucleotide_seqs.fa.primers -t abundant.fungene_9.6_amoA_AOB_1205_unaligned_nucleotide_seqs.fa`

