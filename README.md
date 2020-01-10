# VirusGraphs3
Solidifying the VirusGraphs Infrastructure for Deployment

*insert Charley's figure*

## Linear reference genomes

![](https://github.com/NCBI-Codeathons/VirusGraphs3/blob/master/limit_of_linear.png)
Linear references are the gold standard for genomics applications, including capturing viral genome information and viral sequence recovery. Examples include HIV sequence detection and HIV genome assembly. HIV genome assembly can be loosely classified into whole (reference) genome assebly and HIV genotyping (partial assembly).

## Graph Reference genomes

### Nucleobase graph reference genome

### Approximate k-mer graph reference genome

## Scope

![](https://github.com/NCBI-Codeathons/VirusGraphs3/blob/master/Virus_Graphs_3_Workflow_med_screen.tif)

## Implementation

### Reference graphs

For nucleobase graphs: [NovoGene](https://github.com/NCBI-Hackathons/NovoGraph)
[VG](https://github.com/vgteam/vg).

For approximate k-mer graphs: [original SWIGG](https://github.com/NCBI-Codeathons/SWIGG), [implemented SWIGG](https://github.com/NCBI-Codeathons/Virus_Graphs).

#### Extension of SWIGG
In the original graph created by SWIGG without any filtering parameters, the number of nodes are usually so large that it would result in inefficient visualization and other downstream analysis. Therefore, we implemented the algorithm to make a compact de Bruijn graph. Contraction of nodes starts by a depth-first-search from the source node of the graph. Nodes are included into a supernode continuously as the algorithm walks through the graph. A new supernode is created when the algorithm encounters a node with more than 1 neighbor. The size of the contracted graph is significantly reduced after contraction algorithm is applied (Table ?).

### Transcript modeling
For split-read mapping, [HISAT2](https://ccb.jhu.edu/software/hisat2/index.shtml) was used, and output .bam was pipped into
[StringTie](https://ccb.jhu.edu/software/stringtie/), both in [Galaxy](usegalaxy.eu).

### Visualization

Gephi is used to visualize the output from SWIGG. 
SnapGene
Graphviz

## Results 

### for SWIGG

Graphs built with different k-mer lengths:
![SWIGG built for HIV1 (6 seqs)](https://github.com/NCBI-Codeathons/VirusGraphs3/blob/master/swigg_figure/HIV2_graph_merged.png)

The above figure contains 5 graphs built with different k-mer lengths. (a) k=16, (b) k=20, (c) k=32, (d) k=50, (e) k=90. Longer k-mers cover more repetitive regions. Therefore, longer k-mers result in simpler graphs. Red rectangles highlights the large loop topology in graphs made by small k-mers. The loops are the results of the repeititive k-mers in regions far apart. 


Table of number of nodes and edges before and after contraction

|      |           Before Conrtaction | |         After Contraction ||
|------|----------|--------------------|---------|-------------------|
| kmer | # Nodes  | # Edges            | # Nodes | # Edges           |
| 16   | 38772   | 55265              | 3781    | 4788              |
| 20   | 42442   | 55241              | 2867    | 3641              |
| 32   | 49041   | 55169              | 1350    | 1703              |
| 50   | 52794   | 55061              | 442     | 554               |
| 90   | 54449   | 54821              | 68      | 83                |



### for NovoGraph

Current NovoGraph script.. (TBD).

### for VG



### HIV-1 transcript model

<img src="igv_snapshot_HXB2-mapping_reads_from_SRR3472915_v2.png"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px;" />
**Figure: cDNA+PCR DNAseq ("classic RNAseq").** A. Coverage summary of reads mapped to HXB2 K03455 with HISAT2 with usegalaxy.eu. B. RmDup-processed reads, controling for PCR duplicates after initial alignment. Search strategy = SRA. Searchterms: "HIV-1 and RNAseq and virus". Bioproject: PRJNA320293, specifically SRR3472915. Viewed in IGV.
Source: From https://github.com/NCBI-Codeathons/Virus_Graphs/edit/master/README.md.

Will add predicted isoform models soon..

## Team & contact info

Alejandro Gener (Lead/Corresponding Author)<br />
gener@bcm.edu; itspronouncedhenner@gmail.com<br />
Baylor College of Medicine, Houston, TX, USA<br />
MD Anderson Cancer Center, Houston, TX, USA<br />
Universidad Central del Caribe, Bayamón, PR, USA<br />

Nicolas Cooley<br />
npc19@pitt.edu<br />
Department of Biomedical Informatics, University of Pittsburgh, Pittsburgh PA, USA,15206<br />


Charles Scott Kirby<br />
ckirby4@jhmi.edu<br />
Johns Hopkins University School of Medicine, Baltimore, MD, USA<br />

Zhao Liu<br />
zhaol1@andrew.cmu.edu<br />
Computational Biology Department, Carnegie Mellon University, Pittsburgh, PA, USA<br />

Rahil Sethi<br />
ras143@pitt.edu<br/>
Department of Biomedical Informatics, University of Pittsburgh, Pittsburgh PA, USA,15206<br />

Yutong Qiu<br />
yutongq@andrew.cmu.edu<br />
Computational Biology Department, Carnegie Mellon University, Pittsburgh, PA, USA<br />



