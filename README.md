# Modelling Potential RNA:RNA Interactions Between SARS-CoV-2 and Human Transcriptome

## *Introduction*
The Mod-RNA bioinformatic pipeline, consisting of scripts, linked repositories, and example files as described in this README.md, were collaboratively produced by a group of Post-doctoral, Graduate and Undergraduate biologists and computer scientists as part of the [hackseqRNA](https://www.hackseq.com/rna): COVID-19 Ultra-hackathon event, which occurred remotely from May 22 - 24, 2020. Mod-RNA is a bioinformatics pipeline used to integrate SARS-CoV-2 sub-genomic RNA from transcriptome data and RNA secondary structure predictions to generate RNA:RNA interaction network visualizations.

## *Description*
SARS-CoV-2 is the causative agent of the 2019 - present global pandemic resulting in wide-spread global infection, mortality, and significant impacts on human populations. Inter-kingdom RNA:RNA interactions are important for pathogenesis in some viruses, but have not been extensively studied in SARS-CoV-2 or other coronaviruses. We predicted interactions between SARS-CoV-2 miRNA and human host mRNA using virus transcriptome, secondary RNA structure predictions, and hybridization modelling *in silico*. 

Whether RNA viruses, like SARS-CoV-2, produce host-interfering miRNAs has not been widely accepted nor studied to date. In other viruses, miRNA interactions are thought to be adaptive, since even a single mutation in the small seed-pairing region can give rise to greater phenotypic effects, compared to point mutations in protein-coding genes. However, since most coronaviruses are known to replicate within the cytoplasm of the host cell, access to the host molecular machinery required to produce viral miRNAs was assumed to be limited within the group; recent *in silico* analysis of coronavirus RNA subcellular localization signals suggests that SARS-CoV-2 more effectively localizes to the host cell nucleolus and mitochondrial matrix than related pandemic-causing MERS and SARS coronaviruses (Wu et al., 2020). This supports a higher probability that SARS-CoV-2 may have evolved anti-host miRNA-interacting mechanisms. 

Direct RNA and Nanoball DNA sequencing reveal that the SARS-CoV-2 transcriptome is highly complex, containing a mixture of both canonical and non-canonical subgenomic RNAs arising from discontiguous transcription events (Kim et al., 2020). Recent efforts to take a first look at the conserved structural and non-structural elements in the SARS-CoV-2 genome identified a number of complex structural elements, similar to SARS and MERS (Rangan et al., 2020), some of which play important roles related to viral replication and discontiguous transcription in coronaviruses (Yang and Leibowitz, 2015). Since the genome contains numerous structural elements, it is assumed that the non-canonical subgenomic RNA would also contain elements of conserved structure, as well as novel secondary structure derived through truncated fusions, frameshifted ORFs, body-to-body junctions, or possible recombination events.

While previous studies have aimed to model the interaction between structures in the SARS-CoV-2 genome and the human transcriptome (Liu et al, 2020; Periwal et al., 2020; Saçar Demirci and Adan, 2020), none have integrated recently published studies of the SARS-CoV-2 genome structure and viral transcriptome during infection (Ramya et al., 2020; Kim et al., 2020). It is our hope that Mod-RNA will provide a framework for early investigations into potential miRNA:mRNA interaction networks occurring during infection of humans by SARS-CoV-2, and foster a deeper understanding of potential miRNA found in the transcriptome of the virus while driving more targeted research toward a viable treatment option. We hope that it will inspire further research into such RNA:RNA interactions *in vivo*, using RNA-RNA or Protein-RNA cross-linking or other approaches, which hopefully capture such molecular interactions in time and space.

## *Objectives*
1. Integration of the latest SARS-CoV-2 transcriptome and RNA secondary structure data to predict potential pathogen and host miRNA:mRNA interactions;
2. Visualization of predicted miRNA structures & miRNA:mRNA network interactions;
3. Production of [ViRBase](http://www.rna-society.org/virbase/)-compatible network dataset; and 
4. Report the findings of our work in an open access preprint.

## Useful Resources 

1. Non-canonical SARS-CoV-2 sgRNAs from [UCSC browser deposit](http://genome.ucsc.edu/cgi-bin/hgTables) by Kim et al., 2020 
2. Human 3’UTR database - [UTRdb](http://utrdb.ba.itb.cnr.it/) 
3. Human enhancer database - [EnhancerAtlas](http://www.enhanceratlas.org/)
4. [CD-HIT](http://weizhongli-lab.org/cd-hit/) (Limin et al., 2012)
5. [ViennaRNA](https://www.tbi.univie.ac.at/RNA/) (Lorenz et al., 2011)
6. [Cytoscape](https://js.cytoscape.org/)

## Bioinformatics Approach and Tools Used

1. The sequences for 477 non-canonical SARS-CoV-2 sgRNAs (Kim D et al., 2020) were obtained from the [UCSC genome browser](http://genome.ucsc.edu/cgi-bin/hgTables).  Redundant hits were removed using [CD-HIT](http://weizhongli-lab.org/cd-hit/)  to obtain a FASTA file with 148 sgRNA sequences (identity threshold = 99%).   
2. The non-redundant sequences were aligned with RNA secondary structure regions predicted by Rangan et al. (2020) to obtain secondary structures for the continuous sgRNAs. 
3. The structure of the 200 nucleotides around junction sites for discontinuous sgRNAs were predicted using ViennaRNA’s RNAfold (120 nucleotide window, slide = 40 nucleotides). Structures with MFE < -20 kCal/mol used for further analysis.  
4. HuntMi (Gudyś A et al., 2013) was used to distinguish pre-miRNA hairpins from pseudo hairpins. Details to be added after discussion. 
5. MatureBayes (Gkirtzou K et al., 2010) used to predict miRNAs from pre-miRNAs.
6. Two more tools from ViennaRNA were used (RNAplfold followed by RNAplex) to find viral miRNA:host mRNA interactions.

## Visualization Approach and Tools Used

* [Cytoscape.js](https://js.cytoscape.org/) was used to visualize the network of possible interactions between RNA molecules of the host and viral.
* [ViennaRNA](https://www.tbi.univie.ac.at/RNA/) was used to plot structure models developed by the pipeline team.
* Parse pipeline output into cytoscape appropriate JSON: [https://github.com/varun-kotipalli/Model_RNA/tree/master/Visualization/parser](https://github.com/varun-kotipalli/Model_RNA/tree/master/Visualization/parser)
* Current development git repo for network visualization: [https://github.com/taytayp/cytoscape-rna-model](https://github.com/taytayp/cytoscape-rna-model)

## *The Team*
 
|        Name        	|     GitHub ID    	|       Work Done       	|
|:------------------:	|:----------------:	|:---------------------:	|
| Amber Paulson      	| damselflywingz    | Team Leaad            	|
 
### Pipeline Construction Team: 

|        Name        	|     GitHub ID    	|       Work Done       	|
|:------------------:	|:----------------:	|:---------------------:	|
| Teresa Tavella     	|         -        	| Pipeline Construction 	|
| Michaela Agapiou   	| magapiou         	| Pipeline Construction 	|
| Anna Valyaeva      	| kirushka         	| Pipeline Construction 	|
| Sanjana Bhatnagar  	| sanjanabhatnagar 	| Pipeline Construction 	|
| Christina Akirtava 	| bio2data         	| Pipeline Construction 	|
 
 ### Visualization/Analysis Team:

|        Name       	| GitHub ID  	|        Work Done       	|
|:-----------------:	|------------	|:----------------------:	|
| Jason Laird       	| jlaird-bio 	| Visualization/Analysis 	|
| Jaspreet Singh    	| Jaspreet990 | Visualization/Analysis 	|
| Fatemeh Kiannejad 	| kfate      	| Visualization/Analysis 	|
| Mary Chung        	| mary-chung 	| Visualization/Analysis 	|
  
### Integrated management Team :

|       Name       	|    GitHub ID    	|       Work Done       	|
|:----------------:	|:---------------:	|:---------------------:	|
| Salini Konikkat  	|        -        	| Integrated management 	|
| Taylor Falk      	| taytayp         	| Integrated management 	|
| Clara Smoniewski 	| c-smon          	| Integrated management 	|
| Thomas Ng        	| ngthomas        	| Integrated management 	|

### Integrated management Team :

|       Name       	|    GitHub ID    	|       Work Done       	|
|:----------------:	|:---------------:	|:---------------------:	|
| Varun Kotipalli  	| varun-kotipalli 	| GitHub support        	|

## Note to Prospective Contributors

Development of Mod-RNA occurred under unprecedented circumstances and each member of the team contributed many hours of work to produce this resource. As a result of the SARS-CoV-2 pandemic, many junior scientists are facing unprecedented challenges to continue working in the science fields. If you see value in this work, please consider supporting one of the team members by providing internship, scholarship, mentorship, work-study, or employment to continue working on developing Mod-RNA and conducting RNA research. During this pandemic, bioinformatic researchers can continue to remotely carry out important research  to contribute to many challenges we face as a global society.
The team does not have capacity to provide on-going support for Mod-RNA, and this tool is made available in draft.

## References
1. Gkirtzou K, Tsamardinos I, Tsakalides P, and Poirazi P (2010) MatureBayes: A Probabilistic Algorithm for Identifying the Mature miRNA within Novel Precursors. PLoS One 5(8):e11843. [doi:10.1371/journal.pone.0011843](https://doi.org/10.1371/journal.pone.0011843)
2. Gudyś A, Wojciech Szcześniak M, Sikora M, and Makałowska I (2013) HuntMi: an efficient and taxon-specific approach in pre-miRNA identification. BMC Bioinformatics 14:83. [doi:10.1186/1471-2105-14-83](https://dx.doi.org/10.1186%2F1471-2105-14-83)
3. Kim D, Lee J-Y, Yang J-S, Kim JW, Kim N, and Chang H (2020) The architecture of SARS-Cov-2 transcriptome. Cell 181: 914-921. [doi:10.1016/j.cell.2020.04.011](https://doi.org/10.1016/j.cell.2020.04.011)
4. Limin F, Beifang N, Zhengwei Z, Sitao W, and Weizhong L (2012) CD-HIT: accelerated for clustering the next generation sequencing data. Bioinformatics 28 (23):3150-3152. [doi:10.1093/bioinformatics/bts565](https://doi.org/10.1093/bioinformatics/bts565)
5. Lorenz R, Bernhart SH,Höner zu Siederdissen C, Tafer H,Flamm C, Stadler PF, and HofackerIvo L (2011) ViennaRNA Package 2.0. Algorithms for Molecular Biology, 6:1 26 [doi:10.1186/1748-7188-6-26](http://dx.doi.org/10.1186/1748-7188-6-26)
8. Liu Z, Wang J, Xu Y, Guo M, Mi K, Xu R, Pei Y, Zhang Q, Luan X, Hu Z, Liu X. (2020) Implications of the virus-encoded miRNA and host miRNA in the pathogenicity of SARS-CoV-2. arXiv:200404874 q-bio. http://arxiv.org/abs/2004.04874
1. Periwal N, Sarma S, Arora P, Sood V. (2020) In-silico analysis of SARS-CoV-2 genomes: Insights from SARS encoded non-coding RNAs. bioRxiv. 2020.03.31.018499. [doi.org/10.1101/2020.03.31.018499](https://doi.org/10.1101/2020.03.31.018499)
6. Rangan R, Zheludev IN, Das R.  RNA genome conservation and secondary structure in SARS-CoV-2 and SARS-related viruses. bioRXiv. [doi:10.1101/2020.03.27.012906](https://doi.org/10.1101/2020.03.27.012906)
6. Saçar Demirci MD, Adan A. (2020) Computational analysis of microRNA-mediated interactions in SARS-CoV-2 infection. Bioinformatics; http://biorxiv.org/lookup/doi/10.1101/2020.03.15.992438
7. Wu K, Zou J, Chang HY. (2020) RNA-GPS Predicts SARS-CoV-2 RNA Localization to Host Mitochondria and Nucleolus. Bioinformatics. [http://biorxiv.org/lookup/doi/10.1101/2020.04.28.065201](http://biorxiv.org/lookup/doi/10.1101/2020.04.28.065201)


