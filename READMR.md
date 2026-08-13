Supplementary Tables: Cross-Trait Genetic Architecture of Fat-Free Mass
This repository contains the full supplementary tables for the cross-trait GWAS analysis of four fat-free mass (FFM) traits: Arm FFM, Trunk FFM, Leg FFM, and Whole-body FFM.

Files
table1_lead_snps_sharing.csv — Lead SNPs per trait with cross-trait sharing status
All 1,609 lead SNP records (997 unique SNPs) across the four traits.

Column	Description
SNP	rsID of the lead SNP
CHR, BP	Chromosome and base-pair position (GRCh37/hg19)
A1, A2	Effect allele and other allele
EAF	Effect allele frequency
BETA, SE, P	Effect size, standard error, and p-value from the GWAS
Trait	FFM trait in which this SNP is a lead SNP
Locus_ID	Locus identifier within the trait
Nearest_Gene	Nearest gene to the lead SNP
Gene_Distance_bp	Distance (bp) from the SNP to the nearest gene (0 = intragenic)
N_Traits_Shared	Number of traits (1–4) in which this SNP is a lead SNP
Sharing_Category	Trait-specific (n=1), Shared (2 traits), Shared (3 traits), or Shared (all 4 traits)
Shared_With_Traits	Semicolon-separated list of all traits in which this SNP is a lead SNP
Summary: Of 997 unique SNPs, 616 (61.8%) are trait-specific, 206 (20.7%) are shared by 2 traits, 119 (11.9%) by 3 traits, and 56 (5.6%) are shared across all 4 traits. All shared SNPs show directionally concordant effects across traits.

table2_pathway_enrichment_full.csv — Full pathway enrichment results
Over-representation analysis (ORA) of genes mapped from all lead SNPs per trait (no sharing-based partitioning), tested against five pathway databases. 12,104 pathway–trait test results in total.

Column	Description
Trait	FFM trait
Database	Pathway database: GO Biological Process, GO Molecular Function, GO Cellular Component, KEGG, or Reactome
Pathway_ID	Pathway identifier (GO/KEGG/Reactome accession)
Pathway_Name	Pathway description
GeneRatio	Fraction of input genes in the pathway (k/n)
BgRatio	Fraction of background genes in the pathway (K/N)
Gene_Count	Number of input genes in the pathway (k)
P_value	Hypergeometric test p-value
FDR	Benjamini–Hochberg adjusted p-value
Q_value	q-value
FDR_Significant_0.05	Whether the pathway passes FDR < 0.05 in this trait
N_Traits_FDR_Significant	Number of traits (0–4) in which this pathway is FDR < 0.05
Traits_FDR_Significant	Semicolon-separated list of traits in which this pathway is FDR < 0.05
Entrez_Gene_IDs	Entrez gene IDs of input genes in the pathway (slash-separated)
Summary: 349 unique pathways reach FDR < 0.05 in at least one trait: 174 are significant in exactly one trait (Trunk FFM: 86, Leg FFM: 57, Arm FFM: 15, Whole-body FFM: 16), 129 are shared by 2–3 traits, and 46 are shared across all four traits.

Methods
Gene mapping. Each lead SNP was mapped to its nearest gene (provided in the GWAS locus definition). Gene symbols were mapped to Entrez IDs; 100% of genes were successfully mapped. Input gene sets: Arm FFM 363 genes (371 SNPs), Trunk FFM 422 (428), Leg FFM 375 (382), Whole-body FFM 418 (428).

Enrichment analysis. ORA was performed with clusterProfiler (v4.x) in R, using all human protein-coding genes as the background. GO terms were tested with enrichGO (BP, MF, CC ontologies separately), KEGG with enrichKEGG, and Reactome with ReactomePA::enrichPathway. P-values were adjusted per trait per database using Benjamini–Hochberg FDR. GO BP results were simplified with clusterProfiler::simplify (similarity cutoff 0.7) to reduce redundancy.

Sharing definitions. A SNP is "shared" if it is a lead SNP in more than one trait. A pathway is "shared" if it reaches FDR < 0.05 in more than one trait. Note that sharing defined by significance thresholds is conservative: pathways just below the threshold in one trait are classified as trait-specific even if the true enrichment is similar across traits.

