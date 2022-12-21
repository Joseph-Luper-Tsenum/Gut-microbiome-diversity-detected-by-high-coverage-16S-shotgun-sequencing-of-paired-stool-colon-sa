# Gut microbiome diversity detected by high-coverage 16S & shotgun sequencing of paired stool/colon samples - Data Analysis

### By Joseph Luper Tsenum
Email: tsenumjosephluper@phystech.edu

Phystech School of Biological and Medical Physics (FBMF)

Moscow Institute of Physics and Technology (National Research University)

Russian Federation


### Introduction

The gut microbiome has a key role in human health and disease (Efimova et al. 2018). However, studying the complex structure and function of the gut microbiome through next generation sequencing is a challenging task and it results to reproducibility issues (Efimova et al. 2018)

### How Efimova et al. 2018 sequenced gut microbiome data

Here, Efimova et al. 2018 obtained cross-sectional colon biopsies and faecal samples from nine participants in their COLSCREEN study and sequenced them in high coverage through Illumina pair-end shotgun (for faecal samples) and IonTorrent 16S (for paired feces and colon biopsies) technologies (Efimova et al. 2018). The metagenomes comprised of between 47 and 92 million reads per sample and the targeted sequencing coverage was more than 300 k reads per sample across seven (7) hypervariable regions of the 16S gene (Efimova et al. 2018). Their data is publicly available together with the code for metagenomic analysis using up-to-date bioinformatics algorithms (Efimova et al. 2018). These results will contribute to the full understanding into developing all-inclusive microbiome analysis pipelines and also provide data for onward testing for complex gut microbiome analysis (Efimova et al. 2018).

### Raw Data

18 samples were analyzed in this project: ERR3452791.fastq.gz, ERR3452792.fastq.gz, ERR3452799.fastq.gz, ERR3452800.fastq.gz, ERR3452801.fastq.gz, ERR3452802.fastq.gz, ERR3452803.fastq.gz, ERR3452804.fastq.gz, ERR3452805.fastq.gz, ERR3452806.fastq.gz, ERR3452807.fastq.gz, ERR3452808.fastq.gz, ERR3452809.fastq.gz, ERR3452810.fastq.gz, ERR3452811.fastq.gz, ERR3452812.fastq.gz, ERR3452813.fastq.gz, ERR3452814.fastq.gz


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

The metadata can be found in the uploaded metadata.txt


### Taxonomic composition

Heatmap of taxonomic composition

The interactive heatmap represents relative abundance of major microbial taxa (columns) in the samples (rows). Using the drop-down list “Heatmap settings” on the right of the heatmap, users can select taxonomic rank of interest. For convenience of comparison between close values, clicking on a cell “freezes” the displayed value of cell on the Legend and additionally the displayed abundance of top 10 taxa of corresponding sample (click again or on the cross near sample name to “unfreeze”). Use the Top control to change the way of major composition display between the top features in the selected sample and the top features across all samples on the average.

![now13](https://user-images.githubusercontent.com/58364462/208781515-92f91b8c-bcb4-4fb8-b2ca-956beac1c65f.png)


### Analysis of outliers

Automatic filtering of the user samples with extreme taxonomic composition (based on the combined analysis of user and external data). Analysis of outliers: samples in upper 1% tail of distribution of median distance between each sample and closest 50% of neighbours approximated by normal distribution. List of outliers: ERR3452799


### PCoA visualization based on taxonomic composition

Distribution of the samples by their taxonomic composition in reduced dimensionality. The closer the samples (points) on the plot, the more similar their composition. Vectors show the directions in which the levels of the respective major taxa increase. Method of dimension reduction: PCoA (Principal Coordinate Analysis); dissimilarity metric: weighted UniFrac. Clicking on a dot “freezes” the detailed information about the sample on the right of the plot (click again or on the cross near sample name to “unfreeze”). Switch between the display modes with or without outliers and with or without vectors showing major microbial “drivers” using the respective controls.

![now14](https://user-images.githubusercontent.com/58364462/208781564-d32ce00b-1534-4b4d-8f1f-f008fada8b41.png)

![now15](https://user-images.githubusercontent.com/58364462/208781596-c1c5f466-34af-4780-9901-51d73b963179.png)

#### Alpha-diversity

The measure describes the conditional number of taxa in each sample. Metric: Shannon index.

Alpha-diversity

The measure describes the conditional number of taxa in each sample. Metric: Shannon index. Clicking on a dot “freezes” the displayed value on Y axis and additionally the abundance of top 10 taxa (click on it or on the cross near the sample name to “unfreeze”). In addition, the mean and confidence interval value appear when the mouse is over the boxplot. Controls at the top and bottom-right allow to change the displayed data

![now16](https://user-images.githubusercontent.com/58364462/208781706-b2ffb0b6-bdc0-4e56-a686-761eed650270.png)

#### Сomparison

Wilcoxon signed-rank test is applied to compare the alpha-diversity between the two groups. Alpha-diversity does not vary significantly between groups (p= 0.1730709208049953)


### Taxa co-occurence analysis

#### Co-occurence graph

Co-occurrence of microbial genera was analyzed basing on correlation analysis of their relative abundance using SPIEC-EASI software. In the graph, vertices show genera; pairs of highly co-occurring genera are connected with blue lines. The graph shows the members of the cooperatives - groups of highly co-occurring genera corresponding to isolated components (singleton vertices are omitted). Parameters of SPIEC-EASI algorithm: Meinshausen and Bühlmann neighbourhood selection method (MB), minimum lambda ratio= 0.1, number of lambda iterations = 20, model selection using StARS algorithm (number of StARS subsamples = 50).

No cooperatives detected. Possible reasons: too few or too many co-occurring taxa or insufficient number of samples to perform the analysis.


### Statistical analysis

#### General difference of community structure between two groups
Test if there are significant differences in overall community composition between the samples of two groups. Method: permutational multivariate analysis of variance (PERMANOVA), beta-diversity metric: weighted UniFrac. The result includes the total number of samples, number of PERMANOVA permutations, p-value for the null hypothesis that there is no difference between the groups, as well as information on the equality of group dispersions (obtained using PERMDISP method with same number of permutations). If the group variations are not equal, the results should be interpreted with caution. Samples-outliers listed in the taxonomic composition section are excluded from this analysis.

![now17](https://user-images.githubusercontent.com/58364462/208782269-b370ce66-832c-4baf-b1bb-5df707732399.png)

#### General difference of metabolic potential structure between two groups

Test if there are significant differences in overall metabolic structure between the samples of two groups. Method: permutational multivariate analysis of variance (PERMANOVA), beta-diversity metric: Bray-Curtis distance. The result includes the total number of samples, number of PERMANOVA permutations, p-value for the null hypothesis that there is no difference between the groups, as well as information on the equality of group dispersions (obtained using PERMDISP method with same number of permutations). If the group variations are not equal, the results should be interpreted with caution. Samples-outliers listed in the taxonomic composition section are excluded from this analysis.

![now18](https://user-images.githubusercontent.com/58364462/208782514-b6a44e63-dc4e-4247-9642-691ae4fd40a3.png)

#### Taxonomic composition

Individual microbial taxa for which relative abundance is significantly different between two groups are identified.

#### Wilcoxon test comparison

Method: Wilcoxon signed rank test. The analysis includes the following steps: filtration of rare taxa (taxon must be present in at least 10% of the samples at the level of >0.2%), Wilcoxon signed rank test applied to each taxon to detect the taxa differentially abundant between the groups. Multiple testing adjustment is performed using Benjamini–Hochberg procedure. Contribution of each taxon to the inter-group difference is estimated using LDA method. Samples-outliers listed in the taxonomic composition section are excluded from this analysis.

#### Cladogram of differences

Tree-like summary of the taxa differentially abundant in two groups constructed using LefSe.

#### All results of the test

All features were discarded during the filtering.

#### Generalized linear mixed effect model

A generalized mixed effects linear model is fitted for each taxon to identify if it is differentially abundant between the groups. "Subject_id", is treated as a random effect. The specific probability distribution is selected heuristically depending on the number of samples. For >100 samples, a zero-inflated negative binomial regression is fitted; in other cases - a negative binomial model. Rare taxa are excluded from the analysis (a taxon must be present in at least 10% of the samples at the level of >0.2%). Multiple testing adjustment is performed using Benjamini–Hochberg procedure. Contribution of each taxon to the inter-group difference is estimated using LDA method. The information about distribution family, terms of the model and sample size is displayed in "Model details" section.

Differentially abundant taxa: Tables of differentially abundant taxa overpresented in the groups can be found in the paired analysis report public URL. Overpresented in group: stool

Overpresented in group: biopsy and the table can be found in the paired analysis report public URL.

#### Cladogram of differences

Tree-like summary of the taxa differentially abundant in two groups constructed using LefSe.

Cladogram

![image](https://user-images.githubusercontent.com/58364462/208783214-60f1631f-0e05-44f0-be9e-3cb33348886d.png)

#### List of differentially abundant taxa 

Increased in stool and increased in biopsy and the list can be found in the paired analysis report public URL

### Excluded features

phylum: p__Fusobacteria, p__Spirochaetes, p__Synergistetes, p__[Thermi], p__Cyanobacteria

class: c__Flavobacteriia, c__Fusobacteriia, c__Chloroplast, c__Spirochaetes, c__4C0d-2, c__Deinococci, c__Opitutae, c__Rubrobacteria, c__Epsilonproteobacteria, c__Synergistia, c__RF3, c__Sphingobacteriia, c__[Saprospirae]

order: o__Fusobacteriales, o__Vibrionales, o__Streptophyta, o__Caulobacterales, o__Thiobacterales, o__ML615J-28, o__Oceanospirillales, o__Spirochaetales, o__I025, o__Aeromonadales, o__Myxococcales, o__Flavobacteriales, o__Deinococcales, o__Sphaerochaetales, o__Alteromonadales, o__[Saprospirales], o__MLE1-12, o__Rhodobacterales, o__Ellin6067, o__YS2, o__Campylobacterales, o__Rickettsiales, o__u(c__Alphaproteobacteria), o__Halanaerobiales, o__Bdellovibrionales, o__Rhodocyclales, o__Rhodospirillales, o__Chromatiales, o__CW040, o__Synergistales, o__Neisseriales, o__Rubrobacterales, o__Gemellales, o__Anaeroplasmatales, o__u(c__Clostridia), o__Hydrogenophilales, o__Natranaerobiales, o__[Cerasicoccales], o__Sphingobacteriales

family: f__Mycobacteriaceae, f__Flavobacteriaceae, f__Dermacoccaceae, f__Acetobacteraceae, f__Sphaerochaetaceae, f__Listeriaceae, f__u(c__Clostridia), f__Campylobacteraceae, f__u(o__Ellin6067), f__Shewanellaceae, f__Rubrobacteraceae, f__mitochondria, f__u(o__Bacillales), f__Bradyrhizobiaceae, f__Caulobacteraceae, f__Spirochaetaceae, f__Leuconostocaceae, f__Gemellaceae, f__Methylocystaceae, f__Hydrogenophilaceae, f__Aerococcaceae, f__Dethiosulfovibrionaceae, f__Gordoniaceae, f__Rhodospirillaceae, f__u(o__Gemellales), f__Halanaerobiaceae, f__Dermabacteraceae, f__Bacteriovoracaceae, f__u(o__Aeromonadales), f__Dietziaceae, f__Burkholderiaceae, f__Neisseriaceae, f__Helicobacteraceae, f__Nocardioidaceae, f__Chitinophagaceae, f__Oceanospirillaceae, f__Geodermatophilaceae, f__Succinivibrionaceae, f__Rs-045, f__Erythrobacteraceae, f__Anaerobrancaceae, f__Leptotrichiaceae, f__Rhodocyclaceae, f__Synergistaceae, f__[Acidaminobacteraceae], f__Cellulomonadaceae, f__Enterococcaceae, f__Streptomycetaceae, f__u(c__Alphaproteobacteria), f__Eubacteriaceae, f__Brucellaceae, f__Deinococcaceae, f__Rhizobiaceae, f__u(o__CW040), f__Sinobacteraceae, f__Colwelliaceae, f__[Chromatiaceae], f__u(o__Pasteurellales), f__Dehalobacteriaceae, f__u(o__YS2), f__u(o__ML615J-28), f__Fusobacteriaceae, f__Intrasporangiaceae, f__[Cerasicoccaceae], f__Sphingobacteriaceae, f__u(o__MLE1-12), f__Actinomycetaceae, f__RF16, f__Vibrionaceae, f__Halothiobacillaceae, f__u(o__Chromatiales), f__u(o__Actinomycetales), f__[Weeksellaceae], f__u(o__Synergistales), f__Aeromonadaceae, f__u(o__Streptophyta), f__u(o__Rhizobiales), f__Phyllobacteriaceae, f__u(o__Lactobacillales), f__Rhodobacteraceae, f__Halomonadaceae, f__u(o__Myxococcales), f__u(o__Thiobacterales), f__Gracilibacteraceae, f__Anaeroplasmataceae, f__Pseudonocardiaceae, f__Xanthomonadaceae, f__Methylobacteriaceae

genus: g__u(f__Streptomycetaceae), g__u(f__[Paraprevotellaceae]), g__Renibacterium, g__u(f__Nocardioidaceae), g__u(f__Peptococcaceae), g__u(f__Phyllobacteriaceae), g__u(o__Synergistales), g__Afipia, g__Megasphaera, g__u(f__Methylobacteriaceae), g__u(f__Rhodobacteraceae), g__u(f__Methylocystaceae), g__Mycetocola, g__Gordonia, g__Anaerofustis, g__Hydrogenophilus, g__Aggregatibacter, g__Oribacterium, g__u(f__Anaerobrancaceae), g__Anaerostipes, g__u(f__Carnobacteriaceae), g__Cloacibacillus, g__Treponema, g__Shuttleworthia, g__Azovibrio, g__Providencia, g__u(f__Sphingomonadaceae), g__Dehalobacterium, g__Helicobacter, g__u(o__Thiobacterales), g__Pseudoxanthomonas, g__Phyllobacterium, g__Sediminibacterium, g__Cloacibacterium, g__u(f__Erythrobacteraceae), g__Rubrobacter, g__u(f__Aeromonadaceae), g__Roseivivax, g__Succinivibrio, g__u(f__Shewanellaceae), g__u(o__Ellin6067), g__Paracoccus, g__u(f__Streptococcaceae), g__Thermoanaerobacterium, g__Sarcina, g__u(f__Gemellaceae), g__Schlegelella, g__u(f__Pseudomonadaceae), g__Halothiobacillus, g__Fusobacterium, g__Weissella, g__Porphyromonas, g__Dietzia, g__Eggerthella, g__Sphingobacterium, g__KD1-23, g__u(f__Rhodospirillaceae), g__Enhydrobacter, g__Selenomonas, g__1-68, g__Acinetobacter, g__Pyramidobacter, g__Kocuria, g__Slackia, g__u(f__[Chromatiaceae]), g__u(o__Streptophyta), g__Pediococcus, g__Peptococcus, g__Enterococcus, g__Halomonas, g__u(f__Geodermatophilaceae), g__Finegoldia, g__Agrobacterium, g__Salinibacterium, g__Delftia, g__u(f__Anaeroplasmataceae), g__u(o__MLE1-12), g__u(f__Helicobacteraceae), g__Atopobium, g__Microbacterium, g__Rhodobacter, g__Leuconostoc, g__Stenotrophomonas, g__u(f__Caulobacteraceae), g__u(f__Xanthomonadaceae), g__Facklamia, g__u(f__Sphingobacteriaceae), g__u(o__Myxococcales), g__Mogibacterium, g__u(f__Colwelliaceae), g__u(f__Halanaerobiaceae), g__02d06, g__Morganella, g__Synergistes, g__Actinobacillus, g__Deinococcus, g__Mitsuokella, g__Arcobacter, g__Moryella, g__u(f__Leptotrichiaceae), g__Campylobacter, g__u(o__Lactobacillales), g__u(f__Propionibacteriaceae), g__u(o__Pasteurellales), g__u(f__Dehalobacteriaceae), g__u(f__Moraxellaceae), g__Christensenella, g__u(f__RF16), g__Mycoplana, g__u(f__Comamonadaceae), g__u(f__Bifidobacteriaceae), g__u(o__Aeromonadales), g__u(f__Leuconostocaceae), g__Holdemania, g__Filifactor, g__Caulobacter, g__u(f__Listeriaceae), g__u(o__Bacillales), g__Vibrio, g__Capnocytophaga, g__Cupriavidus, g__u(f__Aerococcaceae), g__u(f__Bacteriovoracaceae), g__Moraxella, g__Leptotrichia, g__Limnohabitans, g__Anaerotruncus, g__u(f__mitochondria), g__Edwardsiella, g__u(f__Sinobacteraceae), g__Bulleidia, g__Coprobacillus, g__u(f__Acetobacteraceae), g__u(o__Actinomycetales), g__Actinomyces, g__TG5, g__Pseudochrobactrum, g__Comamonas, g__u(o__Gemellales), g__Succiniclasticum, g__u(f__Rs-045), g__Ralstonia, g__u(f__Micrococcaceae), g__Oxalobacter, g__Pseudoramibacter_Eubacterium, g__u(f__Microbacteriaceae), g__Flavisolibacter, g__u(o__Chromatiales), g__Citrobacter, g__u(f__Bradyrhizobiaceae), g__Neisseria, g__Pandoraea, g__Carnobacterium, g__Aquabacterium, g__Peptoniphilus, g__Sphaerochaeta, g__Erwinia, g__Variovorax, g__Trabulsiella, g__u(o__YS2), g__Bradyrhizobium, g__Dermacoccus, g__Alkanindiges, g__u(o__CW040), g__Lactococcus, g__Candidatus Rhodoluna, g__Leucobacter, g__Pedobacter, g__u(f__Intrasporangiaceae), g__Sharpea, g__5-7N15, g__Jeotgalicoccus, g__Mannheimia, g__Alloiococcus, g__Gemella, g__Flexispira, g__vadinHB04, g__Actinomycetospora, g__Sodalis, g__u(o__ML615J-28), g__Sphingobium, g__u(f__Prevotellaceae), g__Lutispora, g__u(f__Oceanospirillaceae), g__Chryseobacterium, g__Myroides, g__Aerococcus, g__u(f__Neisseriaceae), g__u(f__Desulfovibrionaceae), g__Dechloromonas, g__Demequina, g__Thiobacillus, g__Butyrivibrio, g__Brochothrix, g__u(f__Rhizobiaceae), g__Geobacillus, g__Brachybacterium, g__Pseudobutyrivibrio, g__u(o__Rhizobiales), g__Fusibacter, g__u(f__[Cerasicoccaceae]), g__Micrococcus, g__Rubellimicrobium, g__Mycobacterium, g__Vagococcus, g__Janibacter, g__Enterobacter, g__rc4-4, g__Kytococcus, g__Candidatus Accumulibacter, g__RFN20, g__u(c__Clostridia), g__u(c__Alphaproteobacteria), g__u(f__Vibrionaceae), g__Peptostreptococcus, g__Methylobacterium, g__Sphingomonas

species: s__u(g__Mannheimia), s__u(g__Morganella), s__u(g__Aggregatibacter), s__u(g__Sphingobium), g__Stenotrophomonas s__geniculata, s__u(g__Roseivivax), s__u(c__Clostridia), g__Lactobacillus s__zeae, g__Lactobacillus s__ruminis, s__u(f__Anaerobrancaceae), s__u(g__Rubellimicrobium), g__Ruminococcus s__flavefaciens, s__u(g__RFN20), s__u(g__Enterobacter), s__u(g__Bradyrhizobium), s__u(f__Bacteriovoracaceae), s__u(f__Neisseriaceae), g__Lactobacillus s__reuteri, s__u(g__Trabulsiella), s__u(f__Listeriaceae), s__u(g__Caulobacter), s__u(f__Halanaerobiaceae), g__Lactobacillus s__acidipiscis, s__u(g__Mycoplana), g__Paracoccus s__marcusii, s__u(g__Lutispora), s__u(o__Rhizobiales), s__u(f__Rs-045), s__u(g__Peptoniphilus), s__u(o__Lactobacillales), s__u(g__Neisseria), g__Capnocytophaga s__ochracea, s__u(g__Pedobacter), s__u(g__Rhodobacter), g__Streptococcus s__minor, s__u(g__Filifactor), g__Bifidobacterium s__bifidum, s__u(g__Pediococcus), g__Staphylococcus s__succinus, s__u(g__Holdemania), s__u(g__Actinobacillus), s__u(f__[Cerasicoccaceae]), g__Staphylococcus s__haemolyticus, s__u(g__Veillonella), s__u(g__Campylobacter), g__Bulleidia s__moorei, s__u(g__Candidatus Accumulibacter), s__u(f__Sphingobacteriaceae), s__u(g__Limnohabitans), s__u(f__Streptococcaceae), s__u(g__Oribacterium), s__u(f__Intrasporangiaceae), s__u(g__5-7N15), s__u(g__Comamonas), g__Kocuria s__rhizophila, s__u(g__Faecalibacterium), s__u(g__Enterococcus), s__u(f__Methylocystaceae), g__Bifidobacterium s__animalis, s__u(f__Rhodospirillaceae), s__u(g__vadinHB04), s__u(g__Weissella), s__u(g__Jeotgalicoccus), s__u(g__Actinomycetospora), g__Clostridium s__bowmanii, s__u(g__Succiniclasticum), g__Staphylococcus s__pettenkoferi, s__u(o__Aeromonadales), s__u(f__Leptotrichiaceae), s__u(f__Propionibacteriaceae), s__u(g__Atopobium), s__u(g__Moryella), s__u(g__Finegoldia), s__u(g__Stenotrophomonas), s__u(g__Sarcina), s__u(g__Dechloromonas), g__Ruminococcus s__callidus, g__Staphylococcus s__aureus, s__u(g__Thermoanaerobacterium), s__u(o__MLE1-12), s__u(g__Enhydrobacter), s__u(g__Candidatus Rhodoluna), s__u(g__Pseudochrobactrum), s__u(g__Succinivibrio), s__u(g__Dehalobacterium), s__u(g__Halomonas), s__u(f__Dehalobacteriaceae), g__Roseburia s__faecis, s__u(g__Mycobacterium), s__u(f__Rhodobacteraceae), s__u(g__Anaerostipes), s__u(g__Renibacterium), g__Streptococcus s__agalactiae, s__u(f__Acetobacteraceae), s__u(g__Fusibacter), s__u(f__Oceanospirillaceae), g__Coprobacillus s__cateniformis, s__u(g__Alloiococcus), g__Enhydrobacter s__aerosaccus, s__u(g__Pseudobutyrivibrio), s__u(g__Sphaerochaeta), s__u(g__Ralstonia), s__u(g__Gordonia), s__u(g__Porphyromonas), s__u(f__Xanthomonadaceae), s__u(f__Peptococcaceae), s__u(g__rc4-4), s__u(g__Agrobacterium), s__u(o__Streptophyta), s__u(o__Thiobacterales), s__u(f__Erythrobacteraceae), g__[Eubacterium] s__cylindroides, g__Brachybacterium s__conglomeratum, s__u(g__Providencia), g__Pseudomonas s__citronellolis, g__Veillonella s__dispar, g__Peptostreptococcus s__anaerobius, s__u(o__Pasteurellales), s__u(g__Mitsuokella), s__u(g__Salinibacterium), g__Clostridium s__perfringens, s__u(o__Myxococcales), s__u(c__Alphaproteobacteria), g__Kocuria s__palustris, g__Sphingomonas s__yabuuchiae, g__Propionibacterium s__granulosum, s__u(g__Arcobacter), s__u(g__Mogibacterium), g__Sphingomonas s__azotifigens, s__u(f__Nocardioidaceae), s__u(f__[Chromatiaceae]), g__Micrococcus s__luteus, s__u(f__Geodermatophilaceae), g__Eggerthella s__lenta, g__Trabulsiella s__farmeri, g__Haemophilus s__influenzae, s__u(g__Lactococcus), s__u(f__Gemellaceae), s__u(g__Hydrogenophilus), s__u(o__Gemellales), s__u(g__Afipia), s__u(g__Anaerotruncus), s__u(f__Comamonadaceae), s__u(g__Leuconostoc), s__u(f__RF16), s__u(g__Acinetobacter), g__Prevotella s__melaninogenica, s__u(g__Geobacillus), s__u(f__Pseudomonadaceae), g__Corynebacterium s__kroppenstedtii, g__Variovorax s__paradoxus, s__u(g__Aquabacterium), g__Lactobacillus s__mucosae, s__u(f__Helicobacteraceae), s__u(f__Moraxellaceae), s__u(o__CW040), s__u(g__Leucobacter), s__u(f__[Paraprevotellaceae]), s__u(g__Christensenella), s__u(g__Synergistes), s__u(f__Colwelliaceae), s__u(g__Carnobacterium), s__u(g__Fusobacterium), g__Enterococcus s__cecorum, s__u(g__Myroides), g__Sphingobacterium s__mizutaii, s__u(g__Kocuria), s__u(g__Schlegelella), s__u(g__Megasphaera), s__u(g__Dietzia), s__u(g__Bulleidia), g__Aggregatibacter s__segnis, g__Acinetobacter s__lwoffii, g__Oxalobacter s__formigenes, g__Corynebacterium s__bovis, s__u(f__Micrococcaceae), g__Rothia s__dentocariosa, s__u(g__Demequina), s__u(g__Rubrobacter), s__u(g__Flexispira), s__u(g__Cloacibacillus), s__u(g__Propionibacterium), s__u(f__Microbacteriaceae), s__u(g__Peptococcus), s__u(g__Citrobacter), s__u(g__Shuttleworthia), s__u(g__TG5), s__u(g__Vagococcus), s__u(g__Anaerofustis), s__u(o__Actinomycetales), s__u(g__Gemella), s__u(g__02d06), s__u(f__Aerococcaceae), g__Corynebacterium s__durum, s__u(g__Edwardsiella), s__u(g__Paracoccus), s__u(g__Microbacterium), g__Stenotrophomonas s__acidaminiphila, s__u(o__Bacillales), s__u(g__Azovibrio), g__Actinobacillus s__parahaemolyticus, s__u(g__Cupriavidus), s__u(g__Dermacoccus), s__u(g__Sharpea), s__u(f__Carnobacteriaceae), s__u(g__Butyrivibrio), s__u(f__Phyllobacteriaceae), s__u(g__Collinsella), s__u(f__mitochondria), s__u(g__Cloacibacterium), g__Pseudomonas s__viridiflava, g__Serratia s__marcescens, s__u(f__Methylobacteriaceae), g__Pyramidobacter s__piscolens, s__u(g__Brochothrix), s__u(g__Delftia), g__Parabacteroides s__gordonii, s__u(g__Mycetocola), s__u(g__Actinomyces), s__u(g__1-68), g__Pseudoxanthomonas s__mexicana, g__Erwinia s__dispersa, s__u(g__Deinococcus), s__u(f__Aeromonadaceae), g__Clostridium s__hiranonis, s__u(g__Selenomonas), g__Staphylococcus s__epidermidis, g__Pseudomonas s__alcaligenes, g__Helicobacter s__pylori, s__u(g__Slackia), g__Pseudomonas s__fragi, s__u(g__Leptotrichia), g__Coprococcus s__catus, s__u(g__Erwinia), s__u(o__YS2), g__Methylobacterium s__adhaesivum, s__u(g__Halothiobacillus), g__Acinetobacter s__schindleri, g__Streptococcus s__anginosus, g__Acinetobacter s__johnsonii, s__u(g__Flavisolibacter), s__u(g__Pyramidobacter), s__u(o__Ellin6067), s__u(f__Streptomycetaceae), s__u(g__Pandoraea), s__u(f__Sinobacteraceae), s__u(g__Sodalis), s__u(g__Sediminibacterium), g__Pseudomonas s__veronii, s__u(g__Facklamia), s__u(f__Bradyrhizobiaceae), s__u(o__Chromatiales), s__u(g__Alkanindiges), s__u(f__Vibrionaceae), s__u(f__Bifidobacteriaceae), g__Streptococcus s__infantis, s__u(o__Synergistales), s__u(g__KD1-23), s__u(g__Aerococcus), g__Lactobacillus s__agilis, s__u(g__Moraxella), s__u(f__Anaeroplasmataceae), s__u(g__Vibrio), s__u(g__Treponema), s__u(f__Shewanellaceae), s__u(f__Rhizobiaceae), s__u(f__Caulobacteraceae), s__u(f__Leuconostocaceae), s__u(g__Chryseobacterium), s__u(g__Peptostreptococcus), s__u(g__Coprobacillus), g__Alloiococcus s__otitis, s__u(g__Kytococcus), s__u(g__Capnocytophaga), s__u(f__Prevotellaceae), s__u(o__ML615J-28), s__u(g__Janibacter), s__u(g__Thiobacillus), g__Staphylococcus s__equorum, s__u(g__Pseudoramibacter_Eubacterium), s__u(f__Desulfovibrionaceae), s__u(g__Phyllobacterium), s__u(f__Sphingomonadaceae), s__u(g__Micrococcus), s__u(g__Sphingomonas), s__u(g__Methylobacterium)

All results of the test can be found in the uploaded GLMM_test_results_for_taxa.csv


### Model details

![now19](https://user-images.githubusercontent.com/58364462/208783967-97ffdf6c-73fe-4a36-8ded-68109eced0d0.png)

#### Functional composition

Individual microbial taxa for which relative abundance is significantly different between two groups are identified.

#### Wilcoxon test comparison

Method: Wilcoxon signed rank test. The analysis includes the following steps: filtration of rare taxa (taxon must be present in at least 10% of the samples at the level of >0.2%), Wilcoxon signed rank test applied to each taxon to detect the taxa differentially abundant between the groups. Multiple testing adjustment is performed using Benjamini–Hochberg procedure. Contribution of each taxon to the inter-group difference is estimated using LDA method. Samples-outliers listed in the taxonomic composition section are excluded from this analysis.

#### Excluded features

KEGG pathways

ko00020 : Citrate cycle (TCA cycle), ko00062 : Fatty acid elongation, ko00100 : Steroid biosynthesis, ko00120 : Primary bile acid biosynthesis, ko00121 : Secondary bile acid biosynthesis, ko00140 : Steroid hormone biosynthesis, ko00196 : Photosynthesis - antenna proteins, ko00232 : Caffeine metabolism, ko00253 : Tetracycline biosynthesis, ko00280 : Valine, leucine and isoleucine degradation, ko00281 : Geraniol degradation, ko00310 : Lysine degradation, ko00311 : Penicillin and cephalosporin biosynthesis, ko00312 : , ko00331 : Clavulanic acid biosynthesis, ko00350 : Tyrosine metabolism, ko00361 : Chlorocyclohexane and chlorobenzene degradation, ko00362 : Benzoate degradation, ko00363 : Bisphenol degradation, ko00364 : Fluorobenzoate degradation, ko00380 : Tryptophan metabolism, ko00401 : Novobiocin biosynthesis, ko00410 : beta-Alanine metabolism, ko00430 : Taurine and hypotaurine metabolism, ko00440 : Phosphonate and phosphinate metabolism, ko00460 : Cyanoamino acid metabolism, ko00471 : D-Glutamine and D-glutamate metabolism, ko00472 : D-Arginine and D-ornithine metabolism, ko00473 : D-Alanine metabolism, ko00510 : N-Glycan biosynthesis, ko00513 : Various types of N-glycan biosynthesis, ko00514 : Other types of O-glycan biosynthesis, ko00521 : Streptomycin biosynthesis, ko00522 : Biosynthesis of 12-, 14- and 16-membered macrolides, ko00531 : Glycosaminoglycan degradation, ko00532 : Glycosaminoglycan biosynthesis - chondroitin sulfate / dermatan sulfate, ko00534 : Glycosaminoglycan biosynthesis - heparan sulfate / heparin, ko00562 : Inositol phosphate metabolism, ko00563 : Glycosylphosphatidylinositol (GPI)-anchor biosynthesis, ko00565 : Ether lipid metabolism, ko00590 : Arachidonic acid metabolism, ko00591 : Linoleic acid metabolism, ko00592 : alpha-Linolenic acid metabolism, ko00601 : Glycosphingolipid biosynthesis - lacto and neolacto series, ko00621 : Dioxin degradation, ko00622 : Xylene degradation, ko00623 : Toluene degradation, ko00625 : Chloroalkane and chloroalkene degradation, ko00626 : Naphthalene degradation, ko00627 : Aminobenzoate degradation, ko00633 : Nitrotoluene degradation, ko00642 : Ethylbenzene degradation, ko00643 : Styrene degradation, ko00785 : Lipoic acid metabolism, ko00791 : Atrazine degradation, ko00830 : Retinol metabolism, ko00901 : Indole alkaloid biosynthesis, ko00905 : Brassinosteroid biosynthesis, ko00906 : Carotenoid biosynthesis, ko00908 : Zeatin biosynthesis, ko00909 : Sesquiterpenoid and triterpenoid biosynthesis, ko00930 : Caprolactam degradation, ko00941 : Flavonoid biosynthesis, ko00943 : Isoflavonoid biosynthesis, ko00945 : Stilbenoid, diarylheptanoid and gingerol biosynthesis, ko00950 : Isoquinoline alkaloid biosynthesis, ko00965 : Betalain biosynthesis, ko00980 : Metabolism of xenobiotics by cytochrome P450, ko00982 : Drug metabolism - cytochrome P450, ko01053 : Biosynthesis of siderophore group nonribosomal peptides, ko01055 : Biosynthesis of vancomycin group antibiotics, ko01056 : Biosynthesis of type II polyketide backbone, ko01057 : Biosynthesis of type II polyketide products, ko03015 : mRNA surveillance pathway, ko03050 : Proteasome, ko03450 : Non-homologous end-joining

KEGG Modules can be found in the paired analysis report public URL

All results of the test can be found in the uploaded Wilcoxon_test_results_for_pathways_and_reactions.csv


### Generalized linear mixed effect model

A generalized mixed effects linear model is fitted for each taxon to identify if it is differentially abundant between the groups. "Subject_id", is treated as a random effect. The specific probability distribution is selected heuristically depending on the number of samples. For >100 samples, a zero-inflated negative binomial regression is fitted; in other cases - a negative binomial model. Rare taxa are excluded from the analysis (a taxon must be present in at least 10% of the samples at the level of >0.2%). Multiple testing adjustment is performed using Benjamini–Hochberg procedure. Contribution of each taxon to the inter-group difference is estimated using LDA method. The information about distribution family, terms of the model and sample size is displayed in "Model details" section.

#### Differentially abundant taxa

Tables of differentially abundant taxa overpresented in the groups in stool and biopsy can be found in the paired analysis report public URL


### Cladogram of differences

Tree-like summary of the taxa differentially abundant in two groups constructed using LefSe.

Cladogram

![image](https://user-images.githubusercontent.com/58364462/208784580-3d52f391-ef72-4fb1-9f33-802c3fdff973.png)

Cladogram of differences

Tree-like summary of the taxa differentially abundant in two groups constructed using LefSe.

Cladogram

![image](https://user-images.githubusercontent.com/58364462/208784948-03d1da83-efe3-4471-9d16-730874cec486.png)


For more information about paired analysis report, check this public URL: https://biota.knomics.ru/public-report?key=z_3FdAdX0G7x_8ch9wkiz5iKjoh85UVj

The link to the whole project can be found here: https://biota.knomics.ru/public-project?key=_7jLYG7-JzpHrM9HAGgeIb2Xhtu-xhAn


### References

1. Efimova D, Tyakht A, Popenko A, Vasilyev A, Altukhov I, Dovidchenko N, Odintsova V, Klimenko N, Loshkarev R, Pashkova M, Elizarova A, Voroshilova V, Slavskii S, Pekov Y, Filippova E, Shashkova T, Levin E, Alexeev D. Knomics-Biota - a system for exploratory analysis of human gut microbiota data. BioData Min. 2018 Nov 6;11:25. doi: 10.1186/s13040-018-0187-3. PMID: 30450127; PMCID: PMC6220475.

2. Yarygin KS, et al. Resistomap — online visualization of human gut microbiota antibiotic resistome. Bioinformatics. 2017;33(14):2205–6.

3. Yarygin K, Tyakht A, Larin A, Kostryukova E, Kolchenko S, Bitner V, Alexeev D. Abundance profiling of specific gene groups using precomputed gut metagenomes yields novel biological hypotheses. PLoS One. 2017;12(4):e0176154.

4. Klimenko N, et al. Microbiome responses to an uncontrolled short-term diet intervention in the frame of the citizen science project. Nutrients. 2018;10(5):576.
 
5. Odintsova V, Tyakht A, Alexeev D. Guidelines to statistical analysis of microbial composition data inferred from metagenomic sequencing. Curr Issues Mol Biol. 2017;24:17–36.

6. Sudarikov K, Tyakht A, Alexeev D. Methods for the metagenomic data visualization and analysis. Curr. Issues Mol. Biol. 2017;24:37–58.

7. Caporaso JG, et al. QIIME allows analysis of high-throughput community sequencing data. Nat Methods. 2010;7(5):335–6.
 
8. Langille MGI, et al. Predictive functional profiling of microbial communities using 16S rRNA marker gene sequences. Nat Biotechnol. 2013;8:1–10.

9. Abubucker S, Segata N, Goll J, et al. Metabolic Reconstruction for Metagenomic Data and Its Application to the Human Microbiome. Eisen JA, ed. PLoS Computat Biol. 2012;8(6):e1002358.

10. Arumugam M, et al. Enterotypes of the human gut microbiome. Nature. 2011;473(7346):174–80.

11. Kurtz ZD, et al. Sparse and compositionally robust inference of microbial ecological networks. PLoS Comput Biol. 2015;11(5):e1004226.

12. Wilke A, et al. The MG-RAST metagenomics database and portal in 2015. Nucleic Acids Res. 2016;44(Database issue):D590–4.

13. Weber N, et al. Nephele: a cloud platform for simplified, standardized and reproducible microbiome data analysis. Bioinformatics. 2017; 8(2017):1411–3.

14. Zeller G, Tap J, Voigt AY, et al. Potential of fecal microbiota for early-stage detection of colorectal cancer. Mol Syst Biol. 2014;10(11):766.

15. Halfvarson J, Brislawn CJ, Lamendella R, et al. Dynamics of the human gut microbiome in inflammatory bowel disease. Nature Microbiol. 2017;2:17004.

16. Smith MI, Yatsunenko T, Manary MJ, et al. Gut microbiomes of Malawian twin pairs discordant for kwashiorkor. Science (New York, NY). 2013;339(6119):548–54.

17. NIH HMP Working group. The NIH human microbiome project. Genome Res. 2009;19:2317–23.


