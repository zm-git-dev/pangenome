
# Pangenome

- #### [The Gap-free Rice Genomes Provide Insights for Centromere Structure and Function Exploration and Graph-based Pan-genome Construction](https://www.biorxiv.org/content/10.1101/2020.12.24.424073v1.full) 

They used vg tookit 

> Construction of Graph-based Pan-genome 
> MH63RS3 was set as a reference and the pan-PAVs sequences were saved in variant call format (VCF). The graph-based pan-genome was construct via the vg (https://github.com/vgteam/vg, version v1.29.0) toolkit (Garrison et al., 2018) with default parameters.


Personnaly I think vg toolkit is for variant detections



A nice review on pangenome graph construction [here](https://www.annualreviews.org/doi/abs/10.1146/annurev-genom-120219-080406?casa_token=R6e5ES5--xUAAAAA:f86Y40wI1cktnEteKSDmOPNRUP1S5f_gszyuRYp-m4I5bBURTSRfz7Yk2mxEKNONVHTVz15GgdMC)

they suggested [minigraph](https://github.com/lh3/minigraph#limit) and seqwish as alignment-based pangenome construction


> Recent unpublished methods explore two new alternatives to alignment-based pangenome construction. Minigraph (https://github.com/lh3/minigraph) extends the minimap2 (83) alignment chaining model to work on graphs. It applies this alignment model to progressively build out a pangenome graph from a series of genomes that contains large sequences (>250 base pairs) that were not previously seen in other genomes. The resulting pangenome does not contain all input sequences and variation between them but rather a representative subset and large structural variants. By contrast, seqwish (48; https://github.com/ekg/seqwish) generates the full variation graph implied by a collection of sequences and alignments between them. The paths embedded in its output graph precisely and completely reconstruct the input sequences, while the topology of the graph describes all variants represented in the input alignments.


Moreover here in [Building pan-genome infrastructures for crop plants and their use in association genetics](https://academic.oup.com/dnaresearch/article/28/1/dsaa030/6117190?login=true) 





The [soybean pangenome paper](https://www.sciencedirect.com/science/article/pii/S0092867420306188?casa_token=_UUFS2Uk31cAAAAA:I7vnED-Tk-_XVb0_7iF-hJCaXAKvEFnQgvZFX5_XEsq6iav-aYP7mEKXtl12dsm5VZfs1-Bh) finaly show me that vg is for structural variation detection...After constructing the graph base pangenome, it is possible to call variant with thousand of genotypes. They used mummer and vg for this section.


*Structural Variation Identification*

SNPs and indels were identified using show-snps (-ClrT) of the MUMmer4 toolkit. We use the SVMU (structural variants from MUMmer) (Chakraborty et al., 2019) pipeline to automate presence and absence variation (PAV) discovery by parsing the result of NUCmer. From the SVMU results, insertion/deletion (with tag INS/DEL) was treated as PAV. The genome region neither detected as synteny block by NUCmer nor insertion/deletion by SVMU was also treated as the PAV region.

For copy number variation (CNV), we first filtered the synteny block less than 100 bp. The sequence region with two or more separate synteny blocks (> 90% identity) overlapping was detected as CNV. Translocation and inversion events (both refer to structure variation ≥ 1 Kbp) were detected by manual check depending on their location and orientation to their neighboring blocks based on the non-allelic homology blocks from the above alignment using MUMmer4. The neighboring blocks belonging to same type of events were merged together. For structural variation merging, we referred to a reported method from human beings (Audano et al., 2019). The ZH13 genome was set as the reference genome, SoyW01 served as the initial callset and new sites were added per sample. Any variants in the sample that had 50% reciprocal overlap with an existing discovery variant was excluded. This merging was performed separately by each variant type.

For graph-based genome construction and analyses, the ZH13 genome was set as a reference, the nonredundant structural variations with repetitive sequences less than 90% were saved in variant call format (VCF), and graph-based genome construction was performed via the vg (https://github.com/vgteam/vg, version v1.6.0) toolkit (Garrison et al., 2018). To genotype the structural variations in 2,898 accessions, we mapped the Illumina short reads from each accession to the graph-based genome via vg toolkit using default parameters.


An other interesting analysis is the *Core and Dispensable Gene Family Clustering*

ORTHOMCL for the orthologues detection, and they performed the annotation using KEEG, Interproscan.

> The core and dispensable gene sets were estimated based on gene family clustering using OrthoMCL (Li et al., 2003) v2.0.9. For each de novo accession and ZH13, a gene containing CDS with 100% similarity to other genes was removed by using the cd-hit-est of CD-HIT (Li and Godzik, 2006) v4.6 toolkit with the parameter of –c 1 –aS 1. Protein sequences of the remaining genes were subjected to homologous searching by BLASTp (Camacho et al., 2009) with parameters of –evalue 1-e10 –max_target_seqs 116. OrthoMCL (version 2.0.9) was used to deal with the BLAST result with the parameter of percentMatchCutoff = 50 and -I 1.5 to make gene family clustering. The gene families that were shared among accessions were defined as core gene families, the gene families that were missed in one or two accessions were defined as softcore gene families, the gene families that were missed in more than two accessions were defined as dispensable gene families, and those that only existed in one accession were defined as private gene families. For phylogenetic analysis of each gene family, MUSCLE (Edgar, 2004) v3.8.31 was used for sequence alignment and MEGA6 (Tamura et al., 2013) was used for phylogenetic tree building.

> For gene function annotation, KEGG pathway analysis was performed using KOBAS 3.0 (Xie et al., 2011), protein domain was annotated by InterProScan 5 (Jones et al., 2014), and Gene Ontology was annotated by PANNZER2 (Törönen et al., 2018). The enrichment test was performed by the ClusterProfiler (Yu et al., 2012) v3.10.1 package in R 3.5.0 (R Development Core Team, 2013). QTL information was obtained from SoyBase (https://www.soybase.org/search/qtllist_by_symbol.php).


Definitively, the [soybean pan-genome](https://www.sciencedirect.com/science/article/pii/S0092867420306188?casa_token=_UUFS2Uk31cAAAAA:I7vnED-Tk-_XVb0_7iF-hJCaXAKvEFnQgvZFX5_XEsq6iav-aYP7mEKXtl12dsm5VZfs1-Bh) is an excellent guide for my thesis pangenome.






















- #### EUPAN TOOLBOX [EUPAN enables pan-genome studies of a large number of eukaryotic genomes](https://academic.oup.com/bioinformatics/article/33/15/2408/3091809?login=true)

- #### Nice review on the application of the pangenome [How the pan-genome is changing crop genomics and improvement](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-020-02224-8)
-
- #### Great inspiration from my virtual mentor  *Philipp E. Bayer* for R-genes pangenomics [publications](https://onlinelibrary.wiley.com/doi/full/10.1111/pbi.13262)


- #### [Sesame pangenome](https://onlinelibrary.wiley.com/doi/full/10.1111/pbi.13022) 
- #### Tool for multiple whole genome alignment for eucakyotes in a context of pangenome | [SibeliaZ](https://www.nature.com/articles/s41467-020-19777-8) |[Github](https://github.com/medvedevgroup/SibeliaZ) | Conda version available usiong the following command line `conda install -c bioconda sibeliaz`
- #### [GSAlign: an efficient sequence alignment tool for intra-species genomes](https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-020-6569-1)


- #### 2021 | [Pan-genomes: moving beyond the reference](https://www.nature.com/articles/d42859-020-00115-3)



```javascript


FURTHER READING
Tettelin, H. et al. Genome analysis of multiple pathogenic isolates of Streptococcus agalactiae: implications for the microbial “pan-genome”. Proc. Natl Acad. Sci. USA 102, 13950–13955 (2005).

Li, R. et al. Building the sequence map of the human pan-genome. Nat. Biotechnol. 28, 57–63 (2010).

Golicz, A. A. et al. The pangenome of an agronomically important crop plant Brassica oleracea. Nat. Commun. 7, 13390 (2016).

Montenegro, J. D. et al. The pangenome of hexaploid bread wheat. Plant J. 90, 1007–1013 (2017).

Zhao, Q. et al. Pan-genome analysis highlights the extent of genomic variation in cultivated and wild rice. Nat. Genet. 50, 278–284 (2018).

Gao, L. et al. The tomato pan-genome uncovers new genes and a rare allele regulating fruit flavor. Nat. Genet. 51, 1044–1051 (2019).

Alonge, M. et al. Major impacts of widespread structural variation on gene expression and crop improvement in tomato. Cell. 182, 145–161 (2020).

Liu, Y. et al. Pan-genome of wild and cultivated soybeans. Cell 182, 162–176 (2020).




```

- #### 2021 | [Targeted plant improvement through genome editing: from laboratory to field](https://link.springer.com/article/10.1007/s00299-020-02655-4)
- #### 2021 | [Hotter, drier, CRISPR: the latest edit on climate change](https://link.springer.com/article/10.1007/s00122-020-03764-0)

- #### 2021 | [Building pan-genome infrastructures for crop plants and their use in association genetics](https://academic.oup.com/dnaresearch/advance-article/doi/10.1093/dnares/dsaa030/6117190?login=true)

- #### 2016 | [The pangenome of an agronomically important crop plant Brassica oleracea](https://www.nature.com/articles/ncomms13390)


- #### [How the pan-genome is changing crop genomics and improvement](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-020-02224-8)

- #### [definition](https://www.grandomics.com/en/pan-genome/)


- #### Apple pan-genome | 02 Noember 2020 | Domestication | Assembly improvement | [Phased diploid genome assemblies and pan-genomes provide insights into the genetic history of apple domestication](https://www.nature.com/articles/s41588-020-00723-9) | [Code availability](https://github.com/XuepengSun/apple_diploid_genomes)

- #### PacBIO a dit "Sequencing multiple individuals is the best way to understand genomic variation in a species or across closely related species." [photo](https://programs.pacificbiosciences.com/l/1652/2020-09-18/426l8j)

- #### [Eight high-quality genomes reveal pan-genome architecture and ecotype differentiation of Brassica napus](https://www.nature.com/articles/s41477-019-0577-7)

- #### [Discovery and population genomics of structural variation in a songbird genus](https://www.nature.com/articles/s41467-020-17195-4)

- #### [Pan-Genome of Wild and Cultivated Soybeans](https://www.sciencedirect.com/science/article/abs/pii/S0092867420306188)

- ##### [Six reference-quality genomes reveal evolution of bat adaptations](https://www.nature.com/articles/s41586-020-2486-3)

- #### [Sunflower pan-genome analysis shows that hybridization altered gene content and disease resistance](https://www.nature.com/articles/s41477-018-0329-0)

- #### [Beyond a Single Reference Genome – The Advantages of Sequencing Multiple Individuals](https://youtu.be/mfldTjg1EqI)
- #### [Rice](https://www.nature.com/articles/s42003-020-0890-8#Sec8) | [Rice wild](https://link.springer.com/article/10.1007/s11427-020-1738-x)
- #### [Plant pan-genomes are the new reference](https://www.nature.com/articles/s41477-020-0733-0)
- #### [Super-Pangenome by Integrating the Wild Side of a Species for Accelerated Crop Improvement](https://www.cell.com/trends/plant-science/fulltext/S1360-1385(19)30281-X)
