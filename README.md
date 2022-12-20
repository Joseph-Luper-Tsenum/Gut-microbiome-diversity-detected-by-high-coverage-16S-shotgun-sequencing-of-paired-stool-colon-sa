# Gut microbiome diversity detected by high-coverage 16S & shotgun sequencing of paired stool/colon samples - Data Analysis

### By Joseph Luper Tsenum
Email: tsenumjosephluper@phystech.edu

Phystech School of Biological and Medical Physics (FBMF)

Moscow Institute of Physics and Technology (National Research University)

Russian Federation


### Introduction

The gut microbiome has a key role in human health and disease (Efimova et al. 2018). However, studying the complex structure and function of the gut microbiome through next generation sequencing is a challenging task and it results to reproducibility issues (Efimova et al. 2018)

### How the Efimova et al. 2018 sequenced the data

Here, Efimova et al. 2018 obtained cross-sectional colon biopsies and faecal samples from nine participants in their COLSCREEN study and sequenced them in high coverage through Illumina pair-end shotgun (for faecal samples) and IonTorrent 16S (for paired feces and colon biopsies) technologies (Efimova et al. 2018). The metagenomes comprised of between 47 and 92 million reads per sample and the targeted sequencing coverage was more than 300 k reads per sample across seven (7) hypervariable regions of the 16S gene (Efimova et al. 2018). Their data is publicly available together with the code for metagenomic analysis using up-to-date bioinformatics algorithms (Efimova et al. 2018). These results will contribute to the full understanding into developing 
all-inclusive microbiome analysis pipelines and also provide data for onward testing for complex gut microbiome analysis (Efimova et al. 2018).

### Basic report

Performed preprocessing of our data and analyzed essential taxonomic and functional composition (without analysis of factors = meta-data about the samples).

### Data quality

Assessment of raw data quality, number of reads and read quantity distribution

Number of the reads per sample before and after the quality filtering. Quality filtering (using split_libraries_fastq.py QIIME1.9 script (Caporaso et al. 2010)) included: trimming of low-quality read ends (quality threshold = 20) and discarding of trimmed reads shorter than 75% of the initial length. Vertical line denotes minimal number of reads (5000 reads).

![image](https://user-images.githubusercontent.com/58364462/208775846-4cc1ff5a-4f2e-437b-84a9-549eb2f6c207.png)

#### Samples with low coverage

List of samples that had insufficient number of high-quality reads after the quality filtering (< 5000 reads) and were excluded from further analysis: All samples passed the filter.

#### Read classification statistics

Reads were classified using a closed-reference OTU picking (uclust_ref algorithm) implemented in QIIME1.9 (Caporaso et al. 2010) against a 16S rRNA sequence database (Greengenes v. 13.5 (DeSantis et al. 2006), 97% OTU similarity).

Proportion of classified reads: Distribution of the successfully classified reads for each sample is shown below

![image](https://user-images.githubusercontent.com/58364462/208776067-f1c7cf33-0d97-4e6e-9c4f-d321358a77da.png)

#### Samples with insufficient proportion of classified reads

Warning: there are samples with low proportion of classified reads (<70%). It is recommended to repeat the analysis by creating an additional project without including these samples: All samples passed the filter.


### Taxonomic composition

Heatmap of taxonomic composition

The interactive heatmap represents relative abundance of major microbial taxa (columns) in the samples (rows). Using the drop-down list “Heatmap settings” on the right of the heatmap, users can select taxonomic rank of interest. For convenience of comparison between close values, clicking on a cell “freezes” the displayed value of cell on the Legend and additionally the displayed abundance of top 10 taxa of corresponding sample (click again or on the cross near sample name to “unfreeze”). Use the Top control to change the way of major composition display between the top features in the selected sample and the top features across all samples on the average.

![now6](https://user-images.githubusercontent.com/58364462/208776392-ac265053-57a8-4184-bb8c-941f1a778f99.png)

#### Major taxa

The boxplots represent distribution of relative abundance for 25 most abundant taxa across all samples (for each taxonomic rank). For proper display on log scale, zero values were replaced with a pseudocount not higher than minimum value of relative abundance of major taxa.

phylum

![image](https://user-images.githubusercontent.com/58364462/208776559-3d49d5ec-5eea-4e17-b869-a7781e3a0a88.png)

class

![image](https://user-images.githubusercontent.com/58364462/208776608-248730ae-c40d-448d-9c8e-74161aaafa46.png)

order

![image](https://user-images.githubusercontent.com/58364462/208776674-d3572caf-ea12-4b80-bcb1-6653f71c14f6.png)

family

![image](https://user-images.githubusercontent.com/58364462/208776737-acc703fc-58d9-4827-b5e3-4c093ff62587.png)

genus

![image](https://user-images.githubusercontent.com/58364462/208776812-a81ea7d5-b19e-4522-b450-88f3ee9021dc.png)

species

![image](https://user-images.githubusercontent.com/58364462/208776882-4c89f5fd-b531-4c3d-ac49-77c17f4f5697.png)

OTU

![image](https://user-images.githubusercontent.com/58364462/208776954-0bfc4f91-810d-4d8d-96f0-382025a6b602.png)

#### Complete taxonomic composition

The table contains relative abundance of all microbial taxa for each taxonomic rank.

Raw counts can be found in the uploaded raw_counts.xlsx

Percent can be found in the uploaded full_taxonomic_composition.xlsx

#### Taxonomic core

The plot represents the proportion of OTUs shared across the varying proportion of samples.

![image](https://user-images.githubusercontent.com/58364462/208777323-e921aeed-e175-4a8c-8b00-b687e699d7b2.png)


### Analysis of outliers

Automatic filtering of the user samples with extreme taxonomic composition (based on the combined analysis of user and external data). Analysis of outliers: samples in upper 1% tail of distribution of median distance between each sample and closest 50% of neighbours approximated by normal distribution. List of outliers: ERR3452799


### PCoA visualization based on taxonomic composition

Distribution of the samples by their taxonomic composition in reduced dimensionality. The closer the samples (points) on the plot, the more similar their composition. Vectors show the directions in which the levels of the respective major taxa increase. Method of dimension reduction: PCoA (Principal Coordinate Analysis); dissimilarity metric: weighted UniFrac. Clicking on a dot “freezes” the detailed information about the sample on the right of the plot (click again or on the cross near sample name to “unfreeze”). Switch between the display modes with or without outliers and with or without vectors showing major microbial “drivers” using the respective controls.

![now7](https://user-images.githubusercontent.com/58364462/208777526-063db280-793b-4947-8f60-a029de506a61.png)


### Enterotypes

Enterotyping (cluster analysis of samples by their composition) was performed according to the original protocol (Arumugam et al, 2011). The optimal number of clusters was determined according to the highest Calinski-Harabasz index. Silhouette width is a measure of the clustering quality. For each of the enterotypes, there is a list of its drivers – microbial taxa distinguishing the samples belonging to the cluster from the other samples.

Number of enterotypes: 2

Calinski-Harabasz index: 7.712

Average silhouette width of the clusters: 0.282


### Microbial drivers

![now8](https://user-images.githubusercontent.com/58364462/208777809-b1413fb1-19f0-4287-bca1-ae681ccf88b9.png)

![now9](https://user-images.githubusercontent.com/58364462/208777835-fa6edf10-328d-4e12-92e9-d2f2285ac3a6.png)


### Hierarchical clustering

The tree shows clustering of the samples by similarity of their taxonomic composition at varying levels of detail. Dissimilarity metric: weighted UniFrac; linkage: Ward’s method.

![now10](https://user-images.githubusercontent.com/58364462/208777959-839325c1-f2bc-4aec-8409-41efbce51325.png)


### Alpha-diversity

#### Interactive plot

The measure describes the conditional number of taxa in each sample. Metric: Shannon index. Clicking on a dot “freezes” the displayed value on Y axis and additionally the abundance of top 10 taxa (click on it or on the cross near the sample name to “unfreeze”). In addition, the mean and confidence interval value appear when the mouse is over the boxplot. Controls at the top and bottom-right allow to change the displayed data.


### Static plots

Chao1 index

![image](https://user-images.githubusercontent.com/58364462/208778147-6d1a44fb-18f1-4b65-8650-3a26185fa3c7.png)

Shannon index

![image](https://user-images.githubusercontent.com/58364462/208778208-14f151c6-49cb-4517-b173-dd17aac12142.png)


### Taxa co-occurence analysis

#### Co-occurence graph

Co-occurrence of microbial genera was analyzed basing on correlation analysis of their relative abundance using SPIEC-EASI software. In the graph, vertices show genera; pairs of highly co-occurring genera are connected with blue lines. The graph shows the members of the cooperatives - groups of highly co-occurring genera corresponding to isolated components (singleton vertices are omitted). Parameters of SPIEC-EASI algorithm: Meinshausen and Bühlmann neighbourhood selection method (MB), minimum lambda ratio= 0.1, number of lambda iterations = 20, model selection using StARS algorithm (number of StARS subsamples = 50).

![now11](https://user-images.githubusercontent.com/58364462/208778325-6252f239-1ef9-48c6-9650-73ba5c9db922.png)

#### Members of the cooperatives

Cooperative content can be found in the uploaded members_cooperative.csv

#### Abundance of the cooperatives

Relative abundance of each cooperative in the samples can be found in the uploaded sample_cooperative.csv


### Reconstruction of metabolic potential

Predicted functional composition of microbiota.

Heatmap of functional composition

The interactive heatmap represents relative abundance of major pathways (columns) in the samples (rows). To switch between KEGG or MetaCyc nomenclatures, use the drop-down list in “Heatmap settings”. For convenience of comparison between close values, clicking on a cell “freezes” the displayed value of the cell in the displayed abundance of top features of the sample (click again or on the cross near the sample name to “unfreeze”). Use the Top control to change the way of major composition display between the top features in the selected sample and the top features across all samples on the average.


#### Vitamins synthesis

Gut microbes are known to produce a number of vitamins. The boxplots represent median, standard deviation and quartiles of the vitamin biosynthesis pathways in the samples.

Gene groups

Relative abundance of KEGG Ortology gene groups involved in vitamins synthesis can be found in the uploaded vitamin_genes.csv

Pathways

Relative abundance of pathways involved in vitamins synthesis can be found in the uploaded vitamin.csv

Plots

Total relative abundance of the genes involved in vitamins biosynthesis summed across the respective pathways.

KEGG pathways

![image](https://user-images.githubusercontent.com/58364462/208779048-8d068042-eeab-42fb-ac46-a6185846f64f.png)

Description of pathways can be found in the uploaded knb_vitamin_pathways_descriptions.pdf

#### Complete functional composition

The table contains relative abundance of all functional features.

Percents can be found in the uploaded full_metabolic_potential.xlsx


#### Synthesis of short-chain fatty acids (SCFAs)

Gut microbes are known to produce SCFAs. The boxplots represent median, standard deviation and quartiles of the SCFAs biosynthesis pathways in the samples.

#### Synthesis of butyrate

Gene groups: Relative abundance of KEGG Ortology gene groups involved in butyrate synthesis can be found in the uploaded butyrate_genes.csv

Pathways: Relative abundance of pathways involved in butyrate synthesis can be found in the uploaded butyrate.csv

Plots

Total relative abundance of the genes involved in butyrate synthesis summed across the respective pathways.

KEGG pathways

![image](https://user-images.githubusercontent.com/58364462/208779596-5520105d-185c-4658-96e9-d7197a07096d.png)

Description of pathways can be found in the uploaded knb_butyrate_pathways_descriptions.pdf


#### Synthesis of propionate

Gene groups: Relative abundance of KEGG Ortology gene groups involved in propionate synthesis can be found in the uploaded propionate_genes.csv

Pathways: Relative abundance of pathways involved in propionate synthesis can be found in the uploaded propionate.csv

Plots

Total relative abundance of the genes involved in propionate synthesis summed across the respective pathways.

KEGG pathways

![image](https://user-images.githubusercontent.com/58364462/208779928-e60c778e-d73e-44a4-90bf-5d9b4d0beb49.png)

Description of pathways can be found in the uploaded knb_propionate_pathways_descriptions.pdf


### All features tables

All calculated features can be downloaded here.

#### Alpha-diversity data

The table contains alpha-diversity values of all samples can be found in the uploaded alpha_diversity.xlsx

#### Complete taxonomic composition

The table contains relative abundance of all microbial taxa for each taxonomic rank.

Raw counts can be found in the uploaded raw_counts.xlsx

Percent can be found in the uploaded full_taxonomic_composition.xlsx

#### Complete functional composition

The table contains relative abundance of all functional features.

Percents can be found in the uploaded full_metabolic_potential.xlsx

#### Beta-diversity data

Table of weighted UniFrac distances between samples can be found in the uploaded beta_diversity.csv


For more information about basic analysis report, check this public URL: https://biota.knomics.ru/public-report?key=xdjekvwq-WorbgfbDYqxbPSxucrfJJzR


### Paired analysis report


For more information about paired analysis report, check this public URL: https://biota.knomics.ru/public-report?key=z_3FdAdX0G7x_8ch9wkiz5iKjoh85UVj


### References

1. Efimova, D., et al. (2018) Knomics-Biota - a system for exploratory analysis of human gut microbiota data. BioData Mining 11(1), 25.


