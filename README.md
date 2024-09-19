Code for simluations, analyses and figures

of my doctoral thesis on
## Bayesian Inference for the Analysis of RNA-Seq Data

All parts of the thesis have folders with code. 






All code and data used for 

## PART 1: An Introduction to Bayesian Statistics

## PART 2: An Introduction to RNA-Seq Data





All code and data used for 

## PART 3: Analytical Bayesian Framework for Differential Gene Expression Analysis using RNA-Seq Data

### Transparency note
Parts of this chapter are in an arXiv pre-print titled 'A Closed-Form Solution to the 2-Sample Problem for Quantifying Changes in Gene Expression using Bayes Factors' authored by Gurpinder Singh Sidhu, Melissa Tomkins, Richard J. Morris and myself (https://doi.org/10.48550/arXiv.2406.19989). This chapter has largely profited from discussions about differential gene expression all co-authors of this pre-print and Thelonious Omori. 

### Summary
Advances in RNA-sequencing technology have revolutionised our ability to capture the complete RNA profile in tissue samples (bulk RNA-Seq). This wealth of data allows for comparative analyses of RNA levels within cells and tissues, shedding light on transcript dynamics of developmental processes, environmental responses, and treatment effects. However, quantifying changes in gene expression still presents a challenge, given the inherent biological variability, technological limitations, and measurement errors. To address this, we introduce a Bayesian framework tailored to the differential gene expression (DGE) analysis of processed RNA-Seq data. Our framework unifies and streamlines a complex analysis, typically involving parameter estimations and multiple statistical tests, into a concise mathematical equation (i.e. we provide a closed-form or analytical solution). The implementation is a single line of code, enabling rapid and transparent ranking of genes according to statistical evidence for a change in gene expression. Furthermore, we introduce a method evaluating the variability between replicates. We conducted a comparison of our framework with leading differential gene expression tools, finding substantial overlaps in the results and interesting disagreements, mainly caused by pre-filtering and small differences in fold change values, which are currently driving the classification of a 'differentially expressed gene'. This motivated us to explore the possibility of ranking genes instead of classifying DEGs moving forward.


### Using bayexpress
All basic functions to use our Bayesian framework for differential gene expression analysis can be found in [bayexpress_function.py](bayexpress_function.py).


### Figure 3.2, 3.3, 3.4
In Figure 3 we explore the analytical Bayesian framework using synthetic data. All plots from the paper (and more) can be found in [SIM.ipynb](SIM.ipynb).

### Figure 3.5
Venn diagrams of identified differentially expressed genes between WT and mutant (Snf2) yeast using _DESeq2_, _edgeR_ and our new Bayesian framework _bayexpress_. The Venn diagrams can be produced with [package_comparison_RALL.ipynb](package_comparison_RALL.ipynb). RALL stands for Replicates ALL, meaning all 44/42 clean yeast replicates have been used. The data is imported from [DGE_results](DGE_results) which in turn has been carried out via [do_DGE.ipynb](do_DGE.ipynb).

### Figure 3.6
Can be reproduced via [package_comparison_RALL.ipynb](package_comparison_RALL.ipynb).

### Figure 3.7 and 3.8
Plot q-plots gene by gene and find the examples from the paper in [example_genes.ipynb](example_genes.ipynb). For more detailed analyses we also created the stalk(genes) function to look at one gene ('LSR1') or a list of genes (e.g. ['LSR1', 'YLL039C', 'YJL098W', 'YLL026W']) to get read counts in WT and Snf2 mutant, q-value visualisation, and more [stalking_genes.ipynb](stalking_genes.ipynb).

### Figure 3.9
Can be reproduced via [investigating_length_bias.ipynb](investigating_length_bias.ipynb).





All code and data used for 

## PART 4: What is a differentially expressed gene?

### Transparency note
This chapter has largely profited from discussions about differential gene expression with Gurpinder Singh Sidhu, Thelonious Omori, Melissa Tomkins and Richard J. Morris. It is an extension to Chapter 3. 

### Summary
In the last chapter we learned about a new Bayesian framework we developed for ranking genes according to their statistical evidence for gene expression change in RNA-Seq data using Bayes factors. To compare our method to existing popular analyses we had to define what exactly a 'differentially expressed genes' was, and started challenging the current definitions. Here we present a series of bootstrapping experiments on a Yeast data set (1) exploring how different researchers and statistical packages define 'differentially expressed genes', (2) demonstrating which trade-offs appear with setting arbitrary cutoffs, and (3) building motivation for moving away from binary classification towards ranking methods. We will learn about the importance of the number of replicates in a study, how variability can easily be misinterpreted as differential expression, and in which ways we can or cannot avoid these problems.

### Figures 4.1, 4.2, 4.2, 4.3, 4.4, 4.5, 4.6
We found the representation in these Figures so useful, we automized it in [stalking_genes.ipynb](stalking_genes.ipynb). Use the stalk(genes) function to look at one gene ('LSR1') or a list of genes (e.g. ['LSR1', 'YLL039C', 'YJL098W', 'YLL026W']) to get read counts in WT and Snf2 mutant, q-value visualisation, and more. 

In [explore_clean_yeast.ipynb](explore_clean_yeast.ipynb) we identified the example genes we discuss in these Figures. 

### Figure 4.7, 4.8, 4.9, 4.10: Control experiment
For the control experiments DGE analysis has only been done in bayexpress. The analysis has been done in [do_DGE.ipynb](do_DGE.ipynb), we recycled bootstrapping data created for the comparison experiment. The figures have been created in [CONTROL_R3_BF1.ipynb](CONTROL_R3_BF1.ipynb), [CONTROL_R3_BF10.ipynb](CONTROL_R3_BF10.ipynb), and [CONTROL_R3_BF100.ipynb](CONTROL_R3_BF100.ipynb) for 3 replicates and [CONTROL_R10_BF1.ipynb](CONTROL_R10_BF1.ipynb), [CONTROL_R10_BF10.ipynb](CONTROL_R10_BF10.ipynb), and [CONTROL_R10_BF100.ipynb](CONTROL_R10_BF100.ipynb) for 10 replicates. 

### Figure 4.11
Calculating Bayes factors for consistency (nBF) and performing bootstrapping experiments to identify very inconsistent genes (list of genes marked as AOTP = All Over The Place) has been carried out using [explore_clean_yeast_consistency.ipynb](explore_clean_yeast_consistency.ipynb). We explored these sets of genes in later parts of the notebook. 

### Some more files
[do_DGE.ipynb](do_DGE.ipynb) is a notebook doing all Differential Gene Expression analysis discussed in the paper. For running DESeq2 and edgeR we are calling R scripts (e.g. 'Do_DGE-DESeq2.R') to carry out the analysis. This is where the parameters for the packages are set. 

For bootstrapping experiments we created 100 shuffled data sets consisting of 3, 6, 12, and 20 replicates of the pool of 44/42 which we used for package comparison. This was done in [comparison_data.ipynb](comparison_data.ipynb).

All code is written in Python 3.10.6, the conda environment export can be found in [environment.yml](environment.yml).





All code and data used for 

## PART 5: RNA-Seq in the detection of long-distance mobile mRNA in plants

### Transparency note
Parts of this chapter have been uploaded to bioRxiv in a manuscript titled ['Re-analysis of mobile mRNA datasets highlights challenges in the detection of mobile transcripts from short-read RNA-Seq data'](https://www.biorxiv.org/content/10.1101/2024.07.25.604588.abstract) authored by Pirita Paajanen, Melissa Tomkins, Ruth Veevers, Michelle Heeney, Hannah Rae Thomas, Federico Apelt, Eleftheria Saplaoura, Saurabh Gupta, Margaret Frank, Dirk Walther, Christine Faulkner, Julia Kehr, Friedrich Kragler, Richard J. Morris and myself \cite{Paajanen_Morris_2024}. Other parts may be recognised from two further of our articles emerging from the PLAMORF project, which are central to Chapter 6, that are authored by subgroups of the former author list.

### Summary
The long-distance transport of messenger RNAs (mRNAs) has been shown to be important for several developmental processes in plants. A popular method for identifying travelling mRNAs is to perform RNA-Seq (RNA-Sequencing) on grafted plants. This approach depends on the ability to correctly assign sequenced mRNAs to the genetic background from which they originated. The assignment is often based on the identification of single-nucleotide polymorphisms (SNPs) between otherwise identical sequences. A major challenge is therefore to distinguish SNPs from sequencing errors. In the following 3 chapters we are presenting our efforts to investigate and improve the accuracy of mobile mRNA detection using RNA-Seq data. Here, we give an introduction to the experimental setup and explain our motivation that led to the work presented in Chapter 6.




All code and data used for 

# PART 6: Bayes factors for the Analysis of RNA-Seq Data in the Detection of mobile mRNA in Plants

### Transparency note
The work presented in this chapter is a collaborative effort of Melissa Tomkins, Saurabh Gupta, Federico Apelt, Julia Kehr, Friedrich Kragler, Richard J. Morris and myself. The statistical method introduced -- Bayes factors in the detection of mobile mRNAs -- has been [published](https://doi.org/10.1098/rsif.2022.0644) in 2022. A [software package](https://doi.org/10.21203/rs.3.rs-2520491/v1) to carry out this analysis has been published in 2023. Jump to software package [baymobil](github.com/mtomtom/baymobil). 

### Summary
In Chapter 5 we learned about the long-distance mobility of mRNAs and that one way to investigate this phenomenon is by combining grafting of plants and RNA-Sequencing. Because the transport of mRNAs is thought to happen in very low numbers, sequencing errors present a major issue in distinguishing signals (SNPs from other genotypes) from noise in the analysis. To tackle this problem we show in this chapter how we can employ Bayesian inference to significantly improve detection accuracy by incorporating prior information into the analysis. We demonstrate how Bayes factors can be computed analytically using read counts (from processed RNA-Seq data) over all the SNPs in an mRNA. We create simulated data to evaluate the performance of the proposed framework, and to compare Bayes factors with other analyses. Our results suggest experimental design criteria (mainly concerning read-depth) for improved graft-mobile mRNA detection and show the pitfalls of filtering for sequencing errors or focusing on single SNPs within an mRNA.



All code and data used for 

## PART 7: The adventurous endeavors of applying Bayes factors in the detection of mobile mRNAs on real RNA-Seq data

### Transparency note
The learnings uncovered during our efforts to apply Bayes factors on real RNA-Seq data to detect mobile mRNAs are documented in a [re-analysis study](https://www.biorxiv.org/content/10.1101/2024.07.25.604588.abstract) carried out by Pirita Paajanen, Melissa Tomkins, Ruth Veevers, Michelle Heeney, Hannah Rae Thomas, Federico Apelt, Eleftheria Saplaoura, Saurabh Gupta, Margaret Frank, Dirk Walther, Christine Faulkner, Julia Kehr, Friedrich Kragler, Richard J. Morris and myself.

### Summary
After demonstrating how we can improve the detection accuracy for mobile mRNA in RNA-Seq data using Bayesian inference we couldn't wait to see the improvements when applying it to real data. We started re-analysing several published data sets with the aim to establish a high-confidence dataset of mobile mRNAs. Our results suggest that previously reported variability between experiments can also be explained by a lack of detection accuracy, which has implications for existing mobile mRNA annotations and challenges current views on long-distance mRNA communication. We could confirm our concern about sequencing errors and detection criteria, but found further analysis problems that we couldn't resolve yet. Therefore, this chapter does not present the obvious results that we and the community had so eagerly awaited (Bayes factors for all genes, high-confidence mobile lists, ...), but we discuss why cannot present them. We hope that the uncovered issues are not only appreciated by the mobile mRNA community but also travel further into other areas in genomics, as in particular studies using single nucleotide polymorphisms (SNPs) to detect variants may be affected as well.

