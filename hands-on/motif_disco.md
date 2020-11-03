# Analyze motifs with RSAT 2020


## Motif analysis <a name="motif"></a>
**Goal**: Define binding motif(s) for the ChIPed transcription factor and identify potential cofactors

### Dataset description
For this training, we will use this dataset:

* ChIP-seq experiment conducted in mouse stem cells, published as: Chen et al (2008) [Integration of External Signaling Pathways with the Core Transcriptional Network in Embryonic Stem Cells](https://www.ncbi.nlm.nih.gov/pubmed/18555785) Cell 133(6),1106–1117.
We will focus on the **Oct4 (also known as Pou5f1)** transcription factor. 

You have at your disposal the set of pre-processed peaks on the IFB cluster in ***/shared/projects/ens_hts_2020/Chip-seq/Oct4_vs_GFP_mm9_summits.bed*** . To focus the region near the summit of the peaks (rather than the complete peaks), use the summit file provided by MACS (only the base corresponding to the summit is listed). The file is on the cloud in the folder Day3.


### Retrieve the peak sequences

For the motif analysis, you first need to extract the sequences corresponding to the peaks. There are several ways to do this (as usual...). If you work on a UCSC-supported organism, the easiest is to use **RSAT fetch-sequences**. Here, we will do this, as the mouse genome is supported at UCSC.

1. Open a connection to a Regulatory Sequence Analysis Tools server. You can choose between various website mirrors.
  * Teaching Server  (recommended for this training) [http://pedagogix-tagc.univ-mrs.fr/rsat/](http://pedagogix-tagc.univ-mrs.fr/rsat/)
2. In the left menu, click on **NGS ChIP-seq** and then click on **fetch-sequences**. A new page opens, with a form
  * Choose the mouse **mm9** genome reference
  *  For the BED file, **upload from your computer** the file you saved above
  *  open the panel **Reference from which the sequences should be fetched**
  *  Add 50bp upstream and downstream. You will obtain sequences of 100bp (summit +/- 50bp)
![screenshot](/images/10_fetch_sequences.png)
  
  
### Motif discovery with RSAT

1. Send the sequences directly to the program **peak-motifs** by clicking on the button peak-motifs located below the results
3. The default peak-motifs web form only displays the essential options. There are only two mandatory parameters that are **already filled**
  * The title box 
  * The sequences
4. We could launch the analysis like this, but we will now modify some of the advanced options in order to fine-tune the analysis according to your data set.
  * Open the "Reduce peak sequences" title, and make sure the "Cut peak sequences: +/- " option is set to 0 (= we wish to analyze our full dataset)
  * Open the “Motif Discovery parameters” title, and check the oligomer sizes 6 (but not 7 or 8). 
  * Under “Compare discovered motifs with databases”, Keep the default
5. You can indicate your email address in order to receive notification of the task submission and completion. This is particularly useful because the full analysis may take some time for very large datasets.
6. Click “GO”. As soon as the query has been launched, you should receive an email indicating confirming the task submission, and providing a link to the future result page.
7. The Web page also displays a link, You can already click on this link. The report will be progressively updated during the processing of the workflow.

### Analyzing the results
The [published protocol](https://www.nature.com/articles/nprot.2012.088) accessible on the cloud provides additional information about the algorithms (see the blue BOXES), as well as guidance to interpret the results (section: ANTICIPATED RESULTS). Additional information regarding motifs found in Oct4 dataset is available in the [publication of peak-motifs](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3287167/)
