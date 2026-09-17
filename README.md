# **Stratifying the Schizophrenia–Diabetes Comorbidity: Shared-Sign Genes, Opposite-Sign Nodes, and Trait-Private Extremes**

## **Abstract**

**Background.** Type 2 diabetes is substantially more common in people with schizophrenia, with recent observational evidence indicating approximately a two-fold increase in risk. Importantly, abnormalities in glucose regulation are detectable in first-episode, antipsychotic-naive illness, although antipsychotic treatment, reduced activity, smoking, diet, and social disadvantage can further increase metabolic burden. The clinical problem is therefore not simply whether schizophrenia and diabetes co-occur, but which patients carry intrinsic metabolic liability before treatment exposure and which biological mechanisms are shared, disease-specific, or locally opposed. NAD+ and nicotinamide mononucleotide biology provides a plausible metabolic framework, but it does not establish a causal bridge between the disorders or justify treatment with NMN.

**Methods.** We performed transcriptome-wide association analyses using S-PrediXcan gene-level association estimates for schizophrenia and a T2D/cardiometabolic dataset labelled `dm_cvs`. The gene-set library was derived from the 088HvA NMN aging transcriptomic analysis of GSE85718, which examined genes whose age-associated expression changes were modified by long-term NMN administration in mouse skeletal muscle, liver, and white adipose tissue. Gene-set enrichment was assessed with Stouffer Z statistics, Wilcoxon tests, permutation testing, bootstrap intervals, and robust sensitivity procedures. Leave-one-out influence analysis, family-wise false-discovery-rate testing, gene-level sign classification, module polarity indices, locus grouping, and Stage 4 claim-robustness audits were then applied.

**Results.** Within the 109 robust NMN-derived biological-process sets, 376 genes significant in both traits showed the same sign and 358 showed opposite signs. The divergent fraction was 0.49, with a bootstrap 95% interval of approximately 0.45–0.53, compatible with equal numbers of convergent and divergent genes. This result remained stable across thresholds from absolute Z of 1.64 to 6.0 and across median, mean, and signed-maximum aggregation. Top-25, top-50, and top-100 gene-list Jaccard values were 0.042, 0.053, and 0.042, respectively. The overall polarity index was only modestly negative, at −0.042, and crossed zero after removal of the proteasome scaffold or genes with absolute Z greater than 8\. The largest opposite-sign effects were enriched at MHC class III, 16p11.2, and 4q24, but locus collapse left 344 independent divergent units, 341 of which lay outside those hubs. Named genes meeting the publication rule were *MAPK3*, *UBE2D3*, *AGER*, *CENPE*, *BTRC*, and *KCTD13*. Shared-sign genes included *C4A*, *MARK3*, *MED1*, *TM6SF2*, *MOV10*, *MAP1LC3A*, *AKT1*, and *HLA-C*. Fatty-acid oxidation remained a T2D-side set-level signal, whereas MHC was mixed at the gene level.

**Conclusions.** The clinically usable interpretation is a three-layer architecture: a shared-sign mid-list that may provide a substrate for comorbidity, a smaller layer of opposite-sign high-leverage nodes concentrated partly in complex loci, and trait-private extremes that preserve disease identity. The analysis does not support a reversed NMN program, a library-wide inversion of metabolic pathways, or NMN treatment for schizophrenia–diabetes comorbidity. It supports targeted follow-up of a short list of genes and loci, beginning with colocalization, fine-mapping, tissue-specific replication, and experimental perturbation.

## **1\. Introduction**

### **1.1 The clinical problem the genetics must answer**

The excess burden of type 2 diabetes in schizophrenia is clinically established but mechanistically unresolved. A 2024 systematic review and meta-analysis of 32 observational studies, including more than two million people with schizophrenia and nearly 36 million comparison participants, estimated an odds ratio of 2.15 for type 2 diabetes in schizophrenia. The analysis also suggested that risk increased with longer follow-up, although the very high heterogeneity across studies indicates that the estimate should not be treated as a fixed individual-level risk \[1\].

The timing of metabolic abnormalities makes the problem more difficult. In first-episode schizophrenia, before substantial antipsychotic exposure, meta-analytic studies have reported higher fasting glucose, higher glucose after an oral glucose-tolerance test, higher fasting insulin, and greater insulin resistance. Differences in glycated haemoglobin have been less consistent and, in several analyses, were not statistically significant. These findings suggest that glucose handling can be abnormal near illness onset rather than emerging only after years of treatment \[2-4\].

This creates two practical difficulties. First, clinical monitoring often treats diabetes risk primarily as a medication adverse effect. Antipsychotics, especially agents with higher metabolic liability, can worsen weight, insulin resistance, dyslipidaemia, and glycaemic control, but they do not fully account for the abnormalities observed in some patients before medication. The resulting clinical question is not whether antipsychotics matter; they clearly do. The question is whether a patient also carries an intrinsic metabolic susceptibility that should change the intensity and timing of metabolic surveillance.

Second, proposed metabolic interventions increasingly invoke inflammation, mitochondrial function, autophagy, or NAD+ biology without specifying which components are shared between schizophrenia and diabetes and which belong to one disease only. A patient with schizophrenia and early dysglycaemia may carry a biological profile that is neither a simple schizophrenia profile nor a simple type 2 diabetes profile. First-episode studies also show substantial inter-individual variability in glucose measures, which makes stratification more relevant than an assumption that all patients share the same metabolic mechanism.

The present analysis was designed around that problem. It does not attempt to explain every metabolic complication of schizophrenia. Instead, it asks whether a gene-set library derived from an NMN aging transcriptomic study can separate three categories of signal: genes that point in the same direction in schizophrenia and T2D, genes that point in opposite directions, and genes that are strong in one trait but not the other.

### **1.2 What genetics has already said, and why it is not enough**

Schizophrenia is highly polygenic, with risk loci implicating synaptic biology, immune regulation, chromatin, neuronal development, and constrained genes. The Psychiatric Genomics Consortium’s large schizophrenia analysis established that common risk is distributed across many loci rather than concentrated in a small number of classical psychiatric genes. It also provided a framework for moving from associated regions to plausible effector genes and biological processes \[5\].

Type 2 diabetes is similarly polygenic but mechanistically heterogeneous. Recent multi-ancestry work identified multiple genetic clusters associated with different combinations of glycaemic, adiposity, lipid, vascular, and insulin-related phenotypes. These clusters implicate pancreatic islets, adipocytes, endothelial cells, liver-related processes, and other tissues rather than a single diabetes pathway \[6\].

The literature on schizophrenia–T2D overlap therefore supports a mixed model. One study found that people with comorbid schizophrenia and T2D carried higher polygenic liability for both traits and identified a limited number of regions with evidence of shared association. The results support shared mechanisms but do not imply that the two disorders use the same biological program in the same direction \[7\].

Other studies have reported weak negative genome-wide genetic correlation between schizophrenia and T2D, while more recent colocalization analyses have identified a subset of loci in which the likely causal directions may be opposed. This is not a contradiction. Genome-wide correlation is an average across the genome, whereas comorbidity may arise from a mixture of shared-sign mechanisms, opposing local effects, and disease-specific mechanisms \[8,9\].

The complement component C4A illustrates why a gene can be shared without representing an inverted disease mechanism. Structural variation at the C4 locus contributes to schizophrenia risk in proportion to the predicted expression of C4A, linking complement biology to synaptic pruning. That observation does not imply that every MHC-linked gene has the same direction, nor that an MHC-derived transcriptomic signature can be counted as a single independent biological finding \[10\].

### **1.3 Why an NMN-derived library, and why that is a constraint**

The gene-set library used here was derived from the 088HvA analysis of GSE85718, a mouse aging microarray study rather than a human intervention study. Investigators administered NMN chronically to aging mice and reported improvements in metabolic physiology, energy metabolism, insulin sensitivity, and age-associated transcriptional changes in skeletal muscle, liver, and white adipose tissue. Those data provide a biologically coherent source for a rescue-oriented gene library, but they do not establish that the same genes mediate human schizophrenia–diabetes comorbidity \[11\].

NAD+ biology is relevant because NAD+-dependent enzymes regulate energy balance, mitochondrial function, chromatin, inflammation, and protein quality control. NMN can improve glucose intolerance and insulin sensitivity in mouse models, and SIRT3-dependent deacetylation has been linked to mitochondrial fatty-acid oxidation. These observations make NAD+ biology a plausible metabolic hinge, but they do not convert the present analysis into a test of NMN efficacy \[12-15\].

The NMN-derived library should therefore be understood as a biologically informed filter. It enriches for processes related to metabolic resilience, proteostasis, fatty-acid oxidation, cell-cycle regulation, membrane biology, Wnt signalling, inflammatory response, and autophagy. It does not demonstrate that schizophrenia and T2D are both NAD diseases, and it cannot show that NMN would prevent diabetes in people with schizophrenia.

### **1.4 TWAS as a gene-level lens, with known failure modes**

S-PrediXcan and related transcriptome-wide association methods estimate the component of gene expression predictable from inherited genetic variation and test whether that predicted expression is associated with a trait. The approach is useful because it moves analysis from millions of variants toward genes and tissues, but the resulting gene signal is not automatically causal. Predicted expression can capture linkage disequilibrium, shared regulatory effects, or neighbouring genes whose expression is correlated with the true effector \[16-18\].

This limitation is particularly important in MHC and 16p11.2. Both regions contain multiple genes, structural variation, complex linkage disequilibrium, and regulatory relationships that are difficult to separate with a standard TWAS. TWAS can prioritize biologically relevant genes while also co-prioritizing LD neighbours. Colocalization and fine-mapping are therefore needed before an imputed expression direction is treated as a mechanistic assignment \[19-22\].

The aim of this study was consequently narrow. We mapped predicted expression of NMN-derived biological-process genes across schizophrenia and T2D, then retained only statements that survived driver removal, extreme-Z audits, locus collapse, hub sensitivity, and named-gene fragility testing.

## **2\. Methods**

### **2.1 GWAS inputs**

The schizophrenia input was based on the Psychiatric Genomics Consortium schizophrenia analysis reported in the literature. The diabetes-related input was derived from the S-PrediXcan folder labelled dm\_cvs, based on the T2D/cardiometabolic GWAS framework used in the 088HvI pipeline. The multi-ancestry diabetes study was used as the external framework for interpreting diabetes heterogeneity, but the present analysis itself used the EUR-labelled S-PrediXcan folder rather than reproducing the full multi-ancestry GWAS \[5,6\].

The label dm\_cvs is important. It represents a T2D and cardiometabolic context rather than a narrowly defined glycaemic phenotype. The results should therefore not be read as if every association reflects fasting glucose, insulin secretion, or beta-cell failure alone. Depending on the contributing GWAS and prediction models, the signal may also reflect adiposity, lipid handling, vascular risk, or broader cardiometabolic biology.

### **2.2 Transcriptome prediction**

The analysis used S-PrediXcan-style gene-level association estimates across multiple tissue prediction panels. These included metabolic and peripheral tissues such as pancreas, adipose tissue, liver, skeletal muscle, and whole blood, together with other available panels in the underlying folders. Gene-level meta-Z values were computed across tissue files using Stouffer’s method.

The use of several tissues was deliberate. The clinical phenotype of early dysglycaemia in schizophrenia is systemic and cannot be represented by a brain-only model. At the same time, peripheral prediction models should not be interpreted as direct measurements of cortical expression. Brain-specific models, cell-type-resolved data, and developmental tissue panels are required next steps. The GTEx resource demonstrates that regulatory effects are strongly tissue-dependent, which is precisely why a cross-tissue meta-Z is useful for screening but insufficient for causal tissue assignment \[23\].

### **2.3 Gene-set construction**

The gene-set library originated from the 088HvA NMN aging transcriptomic analysis of GSE85718. That analysis identified genes whose age-associated expression changes were modified by long-term NMN administration in mouse skeletal muscle, liver, and white adipose tissue. The resulting rescue-oriented genes were linked to Gene Ontology biological processes and assembled into a restricted GOBP library.

Gene symbols and Ensembl identifiers were harmonized against the S-PrediXcan output. The library was then reduced through robust-set filtering, enrichment ranking, and overlap reduction so that heavily redundant GO terms did not dominate the downstream analysis. The final Stage 4 audit evaluated 109 robust kept sets. This process was intended to reduce pathway redundancy, not to create independent biological experiments. Related GO terms often share large fractions of genes, particularly in proteasome, ubiquitin, immune, and cell-cycle categories.

The mouse study is therefore the biological origin of the library, not evidence that the present human associations are caused by NMN or that NMN has been tested for schizophrenia–T2D comorbidity \[11\].

### **2.4 Statistical pipeline**

For each disease and gene set, enrichment was quantified with Stouffer Z, mean Z, mean absolute Z, median Z, a trimmed mean, and a winsorized Stouffer statistic. Wilcoxon signed-rank testing compared the gene-level Z distribution with zero. Competitive permutation testing used 10,000 random draws where applicable, and bootstrap resampling provided percentile confidence intervals for enrichment statistics. Robust analyses winsorized extreme values before selected parametric tests.

Cross-trait comparisons included Kruskal–Wallis testing, pairwise Mann–Whitney testing, paired Wilcoxon testing, Kolmogorov–Smirnov testing, Welch tests, Levene tests, Brunner–Munzel tests, Cohen’s d, sign concordance, Kendall’s tau, and Lin’s concordance correlation coefficient. Family-wise false-discovery-rate correction pooled all in-run p values across enrichment, differential, proximity, pairwise, concordance, and related tests.

Gene-level influence was assessed with leave-one-out recomputation of Stouffer Z. A gene was flagged when its removal changed the absolute Stouffer statistic by more than 20% or changed its sign. Genes with absolute Z greater than 8 were separately audited as extreme candidates because they could dominate a set-level result without representing a stable pathway-wide signal.

The downstream analysis was performed without new TWAS. It collapsed claims across sets, recalculated Stouffer statistics after removal of sign-flip genes, extreme genes, or influential genes, and classified genes using median Z across kept sets. Genes were labelled convergent when both diseases showed significant effects with the same sign, divergent when both were significant with opposite signs, private when only one disease crossed the significance threshold, and weak otherwise.

Module polarity was summarized as the difference between convergent and divergent counts divided by their sum. The analysis also evaluated the effects of removing proteasome scaffold genes, removing genes with absolute Z greater than 8, dropping one GO set at a time, and changing the definition of the kept set. Hub membership was assigned to MHC class III/6p21, 16p11.2, 4q24, or the proteasome scaffold. A size-matched random-drop null was used to test whether apparent hub enrichment exceeded what would be expected from dropping random gene blocks of the same size.

The named-gene publication rule required at least three paired sets and a divergent fraction of at least 0.70 for a gene to enter the main table as a KEEP\_AS\_NODE. Genes with fewer paired sets or lower divergent fractions were assigned caveats or demoted.

### **2.5 What is not claimed from the methods**

The analysis did not perform formal colocalization, fine-mapping, Mendelian randomization, or experimental perturbation. Those methods are required to distinguish shared causal variants from correlated TWAS signals and LD-driven co-prioritization \[20,22\].

The analysis also did not provide per-tissue gene-level Z consistency for the named genes. Stage 4 therefore could not establish whether a named gene had the same direction across brain, pancreas, adipose tissue, liver, muscle, and blood. Finally, transfer of mouse NMN-derived gene sets to human TWAS data is a biological filtering strategy, not a demonstration of one-to-one homology of aging or metabolic mechanisms.

## **3\. Results**

### **3.1 Set-level signals that survive driver removal**

The initial pipeline identified 21 permutation-significant meta-enrichments. After extreme-driver removal and robustness filtering, 109 sets were retained for gene-level analysis. The retained set collection was not equivalent to a list of 109 independent pathways. Many sets shared genes, and the family-wise FDR analysis showed that the largest statistical class was variance heterogeneity rather than simple directional enrichment. Specifically, 26 family-wise FDR-significant rows were Levene-type variance-heterogeneity results. This means that two diseases often activated the same GO label through different genes.

Several schizophrenia-side signals remained after driver removal. TAP-dependent antigen processing and presentation had a Stouffer statistic of approximately −8.9 before removal of extreme genes and approximately −6.3 afterward. Non-canonical Wnt signalling remained negative, changing from approximately −7.5 to −5.7. Regulation of endopeptidase activity, anaphase-promoting-complex-dependent catabolism, and cell-cycle transition also remained detectable after removal of selected extreme or influential genes. Protein localization to membrane showed a positive signal in schizophrenia in the broader analysis. These results identify immune presentation, membrane trafficking, Wnt-related biology, proteolysis, and cell-cycle regulation as recurring labels, but they do not establish that each label represents a single shared molecular program.

Several T2D-side signals were similarly robust. Fatty-acid oxidation remained negative after removal of two absolute-Z greater than 8 genes, changing from approximately −7.6 to approximately −5.0. Cytokine-mediated signalling remained significant after the removal of a larger set of extreme genes, although its Stouffer statistic was attenuated. Regulation of cell division also retained a signal after extreme-driver removal. By contrast, several T2D cell-cycle and haematopoietic-progenitor results were fragile. Regulation of the cell-cycle process, haematopoietic-progenitor differentiation, mitotic sister-chromatid segregation, mitotic spindle organization, and selected Wnt and protein-assembly terms lost significance once absolute-Z greater than 8 genes were removed. These sets were therefore excluded from the main biological narrative.

The family-wise FDR results reinforce the need for this distinction. Levene and related variance-heterogeneity results were abundant, whereas genuine set-level enrichment was more limited. A significant Levene result is not evidence that two diseases share a biological profile. It indicates that the same GO label may be populated by genes with different dispersion or identity across the traits.

The principal driver-robust and driver-dependent set-level results are summarized in **Table 1**.

### **Table 1\. Selected set-level signals before and after extreme-driver removal**

| Trait and gene set | Full or initial Stouffer Z | After removal of ∣Z∣\>8|Z|\>8∣Z∣\>8 genes | Interpretation |  
 |---|---:|---:|---|  
 | SCZ: TAP-dependent antigen processing and presentation | −8.610 | −6.280 | Robust SCZ-side signal |  
 | SCZ: non-canonical Wnt signalling | −7.482 | −5.723 | Robust SCZ-side signal |  
 | SCZ: positive regulation of endopeptidase activity | −8.695 | −4.406 | Robust but attenuated |  
 | T2D: fatty-acid oxidation | −7.527 | −5.044 | Robust T2D-side signal |  
 | T2D: cytokine-mediated signalling | −7.418 | −3.781 | Retained but attenuated |  
 | T2D: regulation of cell division | 7.056 | 4.144 | Retained after driver removal |  
 | T2D: regulation of cell-cycle process | 8.546 | 1.266 | Fragile; lost significance |  
 | T2D: haematopoietic-progenitor differentiation | −7.768 | −1.375 | Fragile; lost significance |

### **3.2 The three-layer architecture**

At the gene level, the robust library separated into three layers. At an absolute-Z threshold of 1.96, 376 genes were convergent and 358 were divergent among genes significant in both traits. The divergent fraction was therefore 0.49. Stage 4 bootstrap resampling produced a 95% interval of approximately 0.45–0.53, which includes 0.50. The correct wording is consequently that the data are compatible with equal numbers of convergent and divergent genes. They do not justify describing the library as dominated by discordance, nor do they establish a global sign inversion.

This balance remained stable across thresholds. At cutoffs of 1.64, 1.96, 2.58, 3.0, 4.0, and 6.0, the divergent fraction remained close to one-half. The same counts were obtained when gene-level effects were aggregated by median, mean, or signed maximum. This agreement matters because it indicates that the central result is not produced by one unusual aggregation rule.

The private layers were substantial. At the absolute-Z threshold of 1.96, 984 genes were T2D-private and 732 were schizophrenia-private. These private layers persisted when the significance threshold moved. The pattern therefore was not simply a contest between shared-sign and opposite-sign genes. Each disease retained a large set of genes that were not significantly represented in the other trait.

The top-ranked genes reinforced this three-layer structure. The Jaccard overlap between the top-25 lists was 0.042, between the top-50 lists 0.053, and between the top-100 lists 0.042. Same-direction overlap was minimal, consisting principally of MED1 among the positively signed genes and MARK3 and MOV10 among the negatively signed genes. These values show that shared GO labels did not translate into shared top-gene identity.

The library-wide polarity index was only modestly negative, at −0.042. Removing the proteasome scaffold moved the value to \+0.045, and removing genes with absolute Z greater than 8 moved it to \+0.023. The maximum single-set change in jackknife analysis was 0.009. However, restricting the denominator to the 20 permutation-significant sets produced a more negative polarity index of −0.116. That difference is important. The claim-set slice is more discordant than the full robust library, but neither denominator supports a reversed library-wide program. The 20-set estimate should therefore be described as a concentrated claim-slice pattern, not as the polarity of all NMN-linked biology.

The three-layer architecture is summarized in **Table 2**, and threshold, aggregation, and kept-set sensitivity are shown in **Table 3**.

### **Table 2\. Gene-level three-layer architecture**

| Gene-level class | Number of genes | Interpretation |
| ----- | ----- | ----- |
| Convergent | 376 | Both traits significant with the same sign |
| Divergent | 358 | Both traits significant with opposite signs |
| T2D-private | 984 | Significant in dm\_cvs but not SCZ |
| SCZ-private | 732 | Significant in SCZ but not dm\_cvs |
| Weak | 1,729 | Neither robustly classified as shared or private |
| Divergent fraction among both-significant genes | 0.488 | Compatible with equal convergence and divergence |
| Bootstrap 95% CI for divergent fraction | 0.452–0.525 | Includes 0.50 |
| Top-50 gene-list Jaccard overlap | 0.053 | Low profile sharing |

### **Table 3\. Threshold, aggregation, and kept-set sensitivity**

| Analysis | Setting | Divergent fraction or polarity index |
| ----- | ----- | ----- |
| Threshold sweep | ( | Z |
| Threshold sweep | ( | Z |
| Threshold sweep | ( | Z |
| Threshold sweep | ( | Z |
| Threshold sweep | ( | Z |
| Threshold sweep | ( | Z |
| Threshold sweep | ( | Z |
| Aggregation at ( | Z | \>1.96) |
| Aggregation at ( | Z | \>1.96) |
| Aggregation at ( | Z | \>1.96) |
| Kept-set definition | Survives extreme | PI \= −0.042 |
| Kept-set definition | All permutation hits | PI \= −0.048 |
| Kept-set definition | Permutation-significant only | PI \= −0.116 |

### **3.3 Hubs are enriched, not explanatory**

MHC class III, 16p11.2, and 4q24 were enriched for divergent genes relative to size-matched random gene drops. The same was true for the broader proteasome scaffold. This result is consistent with the fact that these regions contain several of the largest effects and most recurrent Stouffer-influential genes.

However, hub removal did not eliminate the approximate balance between convergence and divergence. The baseline divergent fraction was 0.488. After dropping MHC genes, it was 0.484; after dropping 16p11.2 genes, 0.484; after dropping 4q24 genes, 0.486; and after dropping the scaffold, 0.485. The scaffold drop was the only intervention that moved the polarity index across zero, to approximately \+0.003. This means that the proteasome scaffold is especially important for the sign of the aggregate statistic, but the number of divergent genes is not confined to the scaffold.

Locus collapse provided the clearest denominator. The analysis counted 358 listed divergent genes but approximately 344 independent divergent units after grouping genes by the predefined hubs. Ten divergent genes were assigned to MHC class III, five to 16p11.2, two to 4q24, and 341 to other genomic regions. The correct sentence is therefore that the largest opposite-sign effects cluster at three intervals, while most independent divergent units lie outside those intervals.

This distinction prevents two opposite errors. The first would be to call all divergent genes independent evidence for a broad anti-correlated pathway. The second would be to claim that three famous loci explain all divergence. The data support neither conclusion. The hubs are where the most visible and extreme effects concentrate, but they are not an explanatory census of all opposite-sign genes.

Hub sensitivity and the effective independent-unit analysis are summarized in **Table 4**.

### **Table 4\. Hub sensitivity and effective independent divergent units**

| Dropped block | Genes dropped | Convergent genes | Divergent genes | Divergent fraction | Set-paired PI | Size-matched null PPP |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| MHC\_6p21 | 26 | 371 | 348 | 0.484 | −0.042 | 0.000 |
| chr16p11.2 | 6 | 376 | 353 | 0.484 | −0.035 | 0.000 |
| chr4q24 | 2 | 376 | 356 | 0.486 | −0.040 | 0.020 |
| Proteasome scaffold | 22 | 370 | 349 | 0.485 | \+0.003 | 0.025 |
| Named six-gene block | 6 | 376 | 352 | 0.484 | −0.034 | NA |

After locus collapse, 358 listed divergent genes corresponded to approximately 344 independent divergent units: 10 in MHC class III, 5 in 16p11.2, 2 in 4q24, and 341 outside those hubs.

### **3.4 Named nodes that survive the publication rule**

The six genes meeting the main-table rule were MAPK3, UBE2D3, AGER, CENPE, BTRC, and KCTD13. They were not treated as causal genes. They were retained as candidate opposite-sign nodes because they had at least three paired sets and a divergent fraction of at least 0.70.

MAPK3, encoding ERK1, was the best-supported named node. It appeared in seven paired sets with a median T2D Z of approximately −15.0 and a median schizophrenia Z of approximately \+12.6. The broader 16p11.2 region is associated with schizophrenia risk and contains dosage-sensitive genes. Functional work has linked a schizophrenia-associated regulatory variant near this region to expression of MAPK3 and other neighbouring genes, including evidence of physical interaction with the MAPK3 promoter \[24,25\].

The present result should not be described as proof that MAPK signalling is globally reversed. It is more precise to say that predicted expression at the MAPK3 node points in opposite directions in the two disease GWAS contexts. The T2D analysis also contained a T2D-private signal for MAP2K1, with a Z of approximately −20.7. Together, these findings suggest a candidate difference in ERK-pathway weighting rather than a disease-wide reversal of the entire pathway.

KCTD13 was present in three paired sets and mapped to 16p11.2. Experimental work has implicated KCTD13 in neuronal morphology and developmental phenotypes associated with 16p11.2 dosage changes. Its opposite sign relative to MAPK3 within the same interval is biologically plausible because a copy-number-sensitive region is a dosage cassette rather than a single-gene switch \[26\].

UBE2D3 was present in four paired sets and showed a T2D-up/SCZ-down pattern. It is an E2 ubiquitin-conjugating enzyme that participates in multiple E3-dependent processes. CENPE, present in three paired sets, showed the opposite disease direction and lies approximately 240 kilobases away in the same broad 4q24 region. The two genes therefore provide a paired 4q24 observation, but shared cis-regulation was not tested.

AGER, encoding the receptor for advanced glycation end products, was a three-set MHC class III node. Its T2D direction was positive, consistent with the biological role of RAGE in advanced-glycation, inflammatory, endothelial, and vascular signalling. The schizophrenia Z was extremely negative, approximately −21.9. That value should be treated as a class-III outlier and not as evidence about diabetic retinopathy, cardiovascular complications, or mortality in schizophrenia. Independent AGER work supports the importance of the rs2070600 Gly82Ser variant for RAGE biology and cardiovascular risk, but it does not validate the direction of the present schizophrenia TWAS signal.

BTRC was present in 21 paired sets and linked the Wnt and ubiquitin narratives. As the beta-TrCP adaptor within SCF ubiquitin-ligase complexes, it participates in turnover of beta-catenin and IκB-family proteins. Its T2D-up/SCZ-down pattern helps explain why Wnt-related and proteostasis-related modules appeared mildly divergent. It also demonstrates how one recurrent gene can make several GO terms appear independently supportive when they are in fact statistically dependent.

Three genes were retained as footnote-level candidates rather than main-table nodes. NOTCH4 showed a T2D-down/SCZ-up effect but was represented in only one paired set. RNF5 appeared in two paired sets and may be relevant to ER-associated degradation and MHC-I quality control. INO80E appeared in two paired sets and lies in the 16p11.2 region near MAPK3. These genes remain biologically interesting, but their present evidence is insufficient for an unqualified publication claim.

The six main-table genes and their fragility classifications are shown in **Table 5**.

### **Table 5\. Named genes meeting the main publication rule**

| Gene | Hub or region | Paired sets | Median dm\_cvs Z | Median SCZ Z | Divergent fraction | Publication verdict |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| UBE2D3 | Other/proteostasis | 4 | \+20.95 | −10.73 | 1.00 | KEEP\_AS\_NODE |
| MAPK3 | chr16p11.2 | 7 | −15.02 | \+12.60 | 1.00 | KEEP\_AS\_NODE |
| AGER | MHC\_6p21 | 3 | \+2.41 | −21.89 | 1.00 | KEEP\_AS\_NODE |
| CENPE | chr4q24 | 3 | −17.87 | \+7.76 | 1.00 | KEEP\_AS\_NODE |
| BTRC | Other/proteostasis | 21 | \+11.03 | −5.75 | 1.00 | KEEP\_AS\_NODE |
| KCTD13 | chr16p11.2 | 3 | \+4.57 | −12.57 | 1.00 | KEEP\_AS\_NODE |

NOTCH4, RNF5, and INO80E were retained only with caveats because they had one or two paired sets. C4A, MED1, and TM6SF2 were demoted from the opposite-sign narrative because their divergent fractions were zero.

### **3.5 Shared-sign genes and trait-private extremes**

The shared-sign layer contained several genes that may be more relevant to comorbidity than the dramatic opposite-sign nodes. C4A was positive in both traits, with a T2D value of approximately \+7.7 and a schizophrenia value of approximately \+23.7. Stage 4 removed it from the opposite-sign table because its divergent fraction was zero. Its appropriate interpretation is therefore a shared complement-related liability signal, not a polarity flip. The result is compatible with the established role of C4A in schizophrenia biology, but it does not show that C4A causes diabetes \[10\].

MED1 was positive in both traits, with values of approximately \+15.6 and \+9.4. TM6SF2 was also positive in both, at approximately \+9.0 and \+9.1, although it had only one paired set and therefore remains a one-set candidate. The TM6SF2 result is biologically interesting because the gene is involved in hepatic lipid handling and VLDL assembly. Its E167K variant has been associated with increased liver fat and altered VLDL triglyceride secretion, illustrating how a shared-sign expression signal could be metabolically meaningful without implying a direct schizophrenia mechanism \[27\].

Other shared-sign candidates included MARK3 and MOV10, both negative in the two traits, as well as MAP1LC3A, AKT1, APH1A, and HLA-C. The pattern suggests that shared liability may involve a broad structural, transcriptional, autophagic, and immune tone rather than a small number of shared top-ranked genes. ATG5 was strongly T2D-private, whereas MAP1LC3A was shared-up. Autophagy therefore appeared reweighted rather than uniformly shared or reversed.

The schizophrenia-private layer contained MDK, FLOT1, VPS29, HLA-DQB2, and CPEB1, among others. These genes and their associated sets were compatible with immune presentation, endosomal trafficking, retromer biology, and RNA localisation. They provide a molecular sketch of schizophrenia-specific biology within the NMN-derived library, but they do not constitute a glucose-resistance phenotype.

The T2D-private layer contained BCAR1, MAP2K1, ATG5, ZWINT, IL27, FTO, PSMD6, and EEF2. Their functions span integrin and insulin-related scaffolding, MEK signalling, autophagy, mitosis, cytokine biology, obesity-linked transcription, proteostasis, and translation. This profile is consistent with the heterogeneity described in recent T2D genetics, in which distinct clusters reflect different combinations of beta-cell, adipose, hepatic, inflammatory, and cardiometabolic biology \[6\].

Fatty-acid oxidation remained a T2D-side set-level survivor. Its meta-level Stouffer statistic was approximately −7.6 and remained approximately −5.0 after removal of two extreme genes. At the gene level, however, the set contained five convergent and four divergent genes, with median Z values of approximately −0.44 in T2D and \+0.20 in schizophrenia. The correct interpretation is therefore a retainable T2D enrichment signal, not a definitive cross-trait fatty-acid-oxidation reversal.

The shared-sign and trait-private layers, together with the FAO and MHC module checks, are summarized in **Table 6**.

### **Table 6\. Shared-sign genes, trait-private extremes, and module checks**

| Layer or module | Representative genes or result | dm\_cvs result | SCZ result | Interpretation |
| ----- | ----- | ----- | ----- | ----- |
| Shared-sign | C4A | \+7.65 | \+23.74 | Shared positive signal; not divergent |
| Shared-sign | MED1 | \+15.64 | \+9.38 | Shared positive transcriptional signal |
| Shared-sign | TM6SF2 | \+8.98 | \+9.13 | Shared positive signal; one paired set |
| Shared-sign | MARK3 | −14.93 | −9.63 | Shared negative signal |
| Shared-sign | MOV10 | −11.26 | −7.91 | Shared negative signal |
| T2D-private | BCAR1 | −27.36 | \+0.10 | T2D-private extreme |
| T2D-private | MAP2K1 | −20.66 | \+1.22 | T2D-private MEK-related signal |
| T2D-private | ATG5 | \+20.18 | −1.89 | T2D-private autophagy-related signal |
| T2D-private | ZWINT | −20.01 | −0.28 | T2D-private mitotic signal |
| SCZ-private | MDK | \+0.37 | −16.83 | SCZ-private extreme |
| SCZ-private | FLOT1 | \+0.44 | −14.78 | SCZ-private trafficking signal |
| SCZ-private | VPS29 | −0.72 | −13.83 | SCZ-private retromer-related signal |
| SCZ-private | CUL9 | −1.73 | \+12.69 | SCZ-private ubiquitin-related signal |
| SCZ-private | HLA-DQB2 | \+1.06 | −11.84 | SCZ-private MHC-related signal |
| FAO module | Convergent/divergent genes | 5 / 4 | — | T2D-side set-level survivor |
| FAO module | Median Z | −0.44 | \+0.20 | Not a definitive gene-wise reversal |
| MHC-I module | Convergent/divergent genes | 10 / 10 | — | Mixed rather than cleanly polarized |

## **4\. Discussion**

### **4.1 Difficulty 1: Comorbidity without a shared lead profile**

The central clinical difficulty is that schizophrenia and T2D can occur together without sharing the same top-ranked genes. In the present analysis, the top-gene Jaccard overlap was approximately 0.05, and the shared-sign/opposite-sign split was compatible with equality. This does not indicate a failed analysis. It is the expected pattern if comorbidity is produced by a shared mid-list of modest effects combined with disease-specific and locally opposed high-leverage effects.

The shared-sign layer is therefore the most plausible substrate for a positive comorbidity model. C4A, MARK3, MED1, TM6SF2, MOV10, MAP1LC3A, AKT1, and HLA-C are not equally secure, but they point in the same direction in both traits. They also illustrate why a top-N approach can miss comorbidity biology. A gene may be consistently aligned across traits without having the largest absolute Z in either one.

C4A is the clearest immune-synaptic example. It belongs to a schizophrenia mechanism already supported by genetic and functional work, but in this analysis it is not a discordant MHC gene. TM6SF2 is the most intuitively metabolic example. Its known role in liver fat and lipoprotein handling provides a bridge to hepatology, but the present one-set result remains insufficient to establish a shared schizophrenia–diabetes mechanism.

The practical consequence is that a “shared pathway” panel built only from the most significant TWAS genes will probably overrepresent MHC, proteasome, and other high-leverage loci while underrepresenting the shared-sign mid-list. A more clinically useful panel would need to separate shared-sign genes from opposite-sign nodes and from trait-private extremes.

### **4.2 Difficulty 2: First-episode dysglycaemia versus antipsychotic toxicity**

The evidence for impaired glucose regulation near schizophrenia onset means that metabolic assessment should not wait until substantial weight gain or prolonged antipsychotic exposure. The cited meta-analyses support the conclusion that glucose handling can be abnormal in first-episode or drug-naive illness, although the magnitude and reproducibility of individual markers vary \[2-4\].

The present gene layers do not replace clinical glucose measurements. Schizophrenia-private signals such as VPS29, FLOT1, and HLA-DQB2, together with schizophrenia-side MHC-I and non-canonical Wnt results, are compatible with an intrinsic disease-associated biological state. They do not encode insulin resistance, and they cannot be used to infer an individual patient’s fasting glucose, HOMA-IR, or oral glucose-tolerance result.

Conversely, the T2D-private layer provides a map of metabolic biology that should not automatically be applied to schizophrenia onset. MAP2K1, BCAR1, ATG5, FTO, PSMD6, and the FAO signal are more naturally interpreted as T2D-side or cardiometabolic signals. Applying them as schizophrenia biomarkers would confuse trait-private biology with comorbidity biology.

This distinction also prevents overinterpretation of MAPK3. Antipsychotic-related changes in ERK and JNK signalling may be relevant to treatment biology, but a MAPK3 TWAS direction should not be treated as evidence that it predicts olanzapine-associated weight gain or determines antipsychotic selection. The present data are not a pharmacogenomic analysis.

The immediate clinical implication is simple: early glucose and lipid surveillance remains necessary regardless of the genetic profile. A genetic or transcriptomic layer may eventually improve stratification, but it should complement rather than replace baseline metabolic assessment.

### **4.3 Difficulty 3: NAD and NMN enthusiasm without a target**

The NMN-derived library is useful because it connects aging, metabolic stress, proteostasis, fatty-acid oxidation, autophagy, and transcriptional regulation. However, the analysis does not show that NMN-linked programs run in opposite directions in schizophrenia and T2D.

What survives is narrower. Ubiquitin–proteasome genes such as UBE2D3, BTRC, RNF5, and several scaffold subunits show disease-specific subunit mixtures. This is not equivalent to “proteasome on” in one disease and “proteasome off” in the other. The library-wide polarity index crosses zero when the scaffold is removed, and 165 genes were influential in both traits. These findings demonstrate statistical dependence, not a reversed proteostasis program.

MED1 provides a plausible shared transcriptional interface, and MAP1LC3A with T2D-private ATG5 suggests autophagic reweighting. Wnt-related divergence is largely connected to BTRC and to schizophrenia-private trafficking genes such as VPS29. Fatty-acid oxidation remains visible on the T2D side. These are useful hypotheses for follow-up, but none is a basis for recommending NMN to people with schizophrenia or for describing schizophrenia and diabetes as opposite NAD states.

The mouse evidence remains valuable as a source of biological plausibility. NMN can improve glucose tolerance and insulin sensitivity in mouse models, and NAD+-dependent enzymes connect mitochondrial metabolism with transcriptional and stress-response pathways. Yet the species, age, perturbation, dose, and phenotype differ from a human TWAS of disease liability \[11-15\].

### **4.4 The most promising translational objects, ranked**

The first priority is the 16p11.2 MAPK3–KCTD13 region. It is already clinically recognizable as a dosage-sensitive interval associated with neurodevelopmental phenotypes, and MAPK3 has functional support as a regulated gene near schizophrenia-associated variation \[24-26\].

The present analysis adds a cardiometabolic contrast. MAPK3 showed schizophrenia-up/T2D-down predicted expression, while MAP2K1 was strongly T2D-private. The most defensible interpretation is that the ERK pathway may be weighted differently in the two disease contexts. The result does not justify an ERK-inhibitor trial, nor does it establish that MAPK3 explains schizophrenia–diabetes comorbidity. The next experiments should include colocalization in cortex, adipose tissue, pancreas, and liver; fine-mapping of the 16p11.2 signal; and isogenic models that measure both neuronal phenotypes and metabolic outputs.

The second priority is the shared-sign pair of C4A and TM6SF2. C4A offers a plausible immune-synaptic liability tone, while TM6SF2 provides a clinically interpretable link to liver fat, lipoprotein secretion, and cardiometabolic phenotype. The two genes should not be merged into one pathway, but they illustrate how the shared-sign layer could be translated into a comorbidity panel. C4A should be interpreted in relation to complement biology, not as a diabetes gene; TM6SF2 should be interpreted in relation to hepatic lipid handling, not as a schizophrenia mechanism \[10,27\].

The third priority is T2D-side FAO biology as an enrichment and monitoring target rather than a schizophrenia target. If a future NAD-intermediate trial is considered in patients with schizophrenia and T2D, enrichment should be based on cardiometabolic or FAO-related liability rather than on a broad schizophrenia MHC score. The biochemical rationale is supported by NAD and SIRT3 biology, but the present data do not establish clinical efficacy \[12,13\].

The fourth priority is AGER as a class-III node. RAGE is biologically serious for diabetic vascular inflammation, advanced-glycation signalling, and cardiovascular risk. The present negative schizophrenia signal is nevertheless embedded in MHC class III and should not be interpreted as a schizophrenia complication or a clean MHC direction. The correct use of AGER is as a candidate node for replication and colocalization, not as evidence for retinopathy, vascular mortality, or treatment response.

NOTCH4 should remain a footnote because it was observed in only one paired set. RNF5 and INO80E should also carry explicit caveats because they had two paired sets and are located in regions containing multiple correlated transcripts. Proteasome inhibitors, claims about olanzapine-specific molecular mechanisms, and late-onset reverse-risk explanations should not be promoted from these results.

### **4.5 How this changes near-term clinical research design**

The immediate research priority is stratification rather than intervention. First-episode metabolic studies should record glucose, insulin, oral glucose-tolerance, glycated haemoglobin, lipid, and body-composition measures before or early in antipsychotic exposure. Genetic stratification could then incorporate 16p11.2 dosage status, complement-related variation or predicted C4A expression, and T2D genetic clusters rather than a single composite NMN score.

Any future NAD-intermediate trial should define the metabolic endpoint separately from psychosis or cognition. A trial could be positive for insulin sensitivity without improving psychotic symptoms, or positive for cognition without changing glucose regulation. Combining those outcomes into one broad “anti-aging” endpoint would make interpretation difficult.

Electronic-health-record studies could test whether the shared-sign layer predicts incident T2D within schizophrenia after antipsychotic class, baseline weight, smoking, activity, socioeconomic status, and early glucose measures are considered. This would extend the polygenic comorbidity logic of earlier disease-level analyses from disease-level scores toward gene-layered, mechanistically separated profiles \[7\].

A 16p11.2-focused study should combine clinical copy-number testing with cortex- and metabolic-tissue colocalization. A C4A/TM6SF2 study should distinguish immune-synaptic burden from hepatic lipid handling. An FAO-focused study should enrich on T2D metabolic phenotypes rather than assume that schizophrenia risk scores define a metabolic responder group.

### **4.6 Limits the discussion must own**

The strongest limitation is the absence of formal colocalization and fine-mapping. A TWAS direction is not a causal direction. This matters most in MHC and 16p11.2, where multiple genes and structural variants share regulatory architecture \[19-22\].

The second limitation is tissue mismatch. Peripheral panels are valuable for a systemic metabolic phenotype, but they cannot stand in for cortical developmental expression. GTEx provides broad regulatory coverage but does not remove the need for disease-relevant brain tissue and cell-type-specific models \[23\].

The third limitation is ancestry. The schizophrenia GWAS is European-enriched, and the analysis used an EUR-labelled diabetes/cardiometabolic S-PrediXcan folder despite the broader multi-ancestry design of the diabetes GWAS. Findings should not be assumed to transport unchanged to East Asian, African, South Asian, Hispanic, or other populations. Ancestry-aware replication is required \[28,29\].

The fourth limitation is the cross-species origin of the gene-set library. The library came from a mouse aging NMN microarray study, whereas the present disease analysis used human GWAS-predicted expression. That combination is appropriate for hypothesis generation but not for causal inference.

Finally, the extreme-Z genes remain vulnerable to influence and LD-related artefacts. The KEEP\_AS\_NODE rule is a publication discipline, not a causal guarantee. The main table should therefore use language such as “candidate discordant node,” “predicted-expression association,” and “requires colocalization,” rather than “driver,” “therapeutic target,” or “causal gene.”

## **5\. Conclusion**

Schizophrenia–T2D comorbidity is not explained by a reversed NMN program, but neither is it refuted by a near-zero or weakly negative genome-wide relationship. The present TWAS of NMN-derived biological-process sets supports a narrower architecture.

The first layer is a shared-sign mid-list that may provide a substrate for comorbidity. C4A, MARK3, MED1, TM6SF2, MOV10, MAP1LC3A, AKT1, and HLA-C point in the same direction in both traits, although several remain limited by the number of paired sets or by extreme values. This layer is more compatible with a shared liability than with disease antagonism.

The second layer consists of opposite-sign, high-leverage nodes. The largest effects are enriched at MHC class III, 16p11.2, and 4q24, but most independent divergent units lie outside those hubs. The admissible main-table candidates are MAPK3, UBE2D3, AGER, CENPE, BTRC, and KCTD13. They should be treated as candidate nodes for colocalization, fine-mapping, and perturbation, not as causal assignments or treatment targets.

The third layer consists of trait-private extremes. Schizophrenia retains an MHC, endosomal, retromer, and RNA-localisation profile, whereas T2D retains MEK, integrin, autophagy, mitotic, cytokine, and FAO-related signals. These private layers preserve disease identity on a gene-set background that is only partly shared.

The practical conclusion is not a prescription. First-episode glucose measurement remains necessary because the schizophrenia-private layer does not encode insulin resistance. NAD-intermediate trials, if pursued, should be designed around T2D-side metabolic phenotypes, particularly FAO-related or cardiometabolic clusters, rather than around a claim of globally reversed NAD biology. The most immediate precision-medicine opportunity is the 16p11.2 region, where MAPK3 and KCTD13 can be studied alongside copy-number status and tissue-specific regulatory data.

Until colocalization, fine-mapping, and experimental validation are completed, these genes remain candidates. The useful claim is therefore not that schizophrenia and T2D use NMN-linked programs in opposite directions. It is that their comorbidity is stratified: shared-sign background, hub-enriched opposite-sign nodes, and trait-private extremes.

## **References**

1. Dong K, Wang S, Qu C, Zheng K, Sun P. Schizophrenia and type 2 diabetes risk: a systematic review and meta-analysis. *Front Endocrinol (Lausanne).* 2024;15:1395771. doi:10.3389/fendo.2024.1395771

2. Perry BI, McIntosh G, Weich S, Singh S, Rees K. The association between first-episode psychosis and abnormal glycaemic control: systematic review and meta-analysis. *Lancet Psychiatry.* 2016;3(11):1049-1058. doi:10.1016/S2215-0366(16)30262-0

3. Pillinger T, Beck K, Gobjila C, Donocik JG, Jauhar S, Howes OD. Impaired glucose homeostasis in first-episode schizophrenia: a systematic review and meta-analysis. *JAMA Psychiatry.* 2017;74(3):261-269. doi:10.1001/jamapsychiatry.2016.3803

4. Yang W, Zheng L, Zheng B, Zeng S, Li J, Liang B, et al. A meta-analysis of abnormal glucose metabolism in first-episode drug-naive schizophrenia. *Psychiatr Danub.* 2020;32(1):46-54. doi:10.24869/psyd.2020.46

5. Trubetskoy V, Pardiñas AF, Qi T, Panagiotaropoulou G, Awasthi S, Bigdeli TB, et al. Mapping genomic loci implicates genes and synaptic biology in schizophrenia. *Nature.* 2022;604(7906):502-508. doi:10.1038/s41586-022-04434-5

6. Suzuki K, Hatzikotoulas K, Southam L, Taylor HJ, Yin X, Lorenz KM, et al. Genetic drivers of heterogeneity in type 2 diabetes pathophysiology. *Nature.* 2024;627(8003):347-357. doi:10.1038/s41586-024-07019-6

7. Perry BI, Bowker N, Burgess S, Wareham NJ, Upthegrove R, Jones PB, et al. Evidence for shared genetic aetiology between schizophrenia, cardiometabolic, and inflammation-related traits: genetic correlation and colocalization analyses. *Schizophr Bull Open.* 2022;3(1):sgac001. doi:10.1093/schizbullopen/sgac001

8. Arruda AL, Khandaker GM, Morris AP, Smith GD, Huckins LM, Zeggini E. Genomic insights into the comorbidity between type 2 diabetes and schizophrenia. *Schizophrenia (Heidelb).* 2024;10:22. doi:10.1038/s41537-024-00445-5

9. Sekar A, Bialas AR, de Rivera H, Davis A, Hammond TR, Kamitaki N, et al. Schizophrenia risk from complex variation of a complement component 4 gene. *Nature.* 2016;530(7589):177-183. doi:10.1038/nature16549

10. Mills KF, Yoshida S, Stein LR, Grodzki ACG, Patterson T, Purpura M, et al. Long-term administration of nicotinamide mononucleotide mitigates age-associated physiological decline in mice. *Cell Metab.* 2016;24(6):795-806. doi:10.1016/j.cmet.2016.09.013

11. Cantó C, Menzies KJ, Auwerx J. NAD+ metabolism and the control of energy homeostasis: a balancing act between mitochondria and the nucleus. *Cell Metab.* 2015;22(1):31-53. doi:10.1016/j.cmet.2015.05.023

12. Hirschey MD, Shimazu T, Goetzman E, Jing E, Schwer B, Lombard DB, et al. SIRT3 regulates mitochondrial fatty-acid oxidation by reversible enzyme deacetylation. *Nature.* 2010;464(7285):121-125. doi:10.1038/nature08778

13. Yoshino J, Mills KF, Yoon MJ, Imai SI. Nicotinamide mononucleotide, a key NAD+ intermediate, treats the pathophysiology of diet- and age-induced diabetes in mice. *Cell Metab.* 2011;14(4):528-536. doi:10.1016/j.cmet.2011.08.014

14. Yoshino J, Baur JA, Imai SI. NAD+ intermediates: the biology and therapeutic potential of NMN and NR. *Cell Metab.* 2018;27(3):513-528. doi:10.1016/j.cmet.2017.11.002

15. Gamazon ER, Wheeler HE, Shah KP, Mozaffari SV, Aquino-Michaels K, Carroll RJ, et al. A gene-based association method for mapping traits using reference transcriptome data. *Nat Genet.* 2015;47(9):1091-1098. doi:10.1038/ng.3367

16. Gusev A, Ko A, Shi H, Bhatia G, Chung W, Penninx BWJH, et al. Integrative approaches for large-scale transcriptome-wide association studies. *Nat Genet.* 2016;48(3):245-252. doi:10.1038/ng.3506

17. Barbeira AN, Dickinson SP, Bonazzola R, Zheng J, Wheeler HE, Torres JM, et al. Exploring the phenotypic consequences of tissue-specific gene expression variation inferred from GWAS summary statistics. *Nat Commun.* 2018;9:1825. doi:10.1038/s41467-018-03621-1

18. Wainberg M, Sinnott-Armstrong N, Mancuso N, Barbeira AN, Knowles DA, Golan D, et al. Opportunities and challenges for transcriptome-wide association studies. *Nat Genet.* 2019;51(4):592-599. doi:10.1038/s41588-019-0385-z

19. Giambartolomei C, Vukcevic D, Schadt EE, Franke L, Hingorani AD, Wallace C, et al. Bayesian test for colocalisation between pairs of genetic association studies using summary statistics. *PLoS Genet.* 2014;10(5):e1004383. doi:10.1371/journal.pgen.1004383

20. Mancuso N, Freund MK, Johnson R, Shi H, Kichaev G, Gusev A, et al. Probabilistic fine-mapping of transcriptome-wide association studies. *Nat Genet.* 2019;51(4):675-682. doi:10.1038/s41588-019-0367-1

21. Wallace C. A more accurate method for colocalisation analysis allowing for multiple causal variants. *PLoS Genet.* 2021;17(9):e1009440. doi:10.1371/journal.pgen.1009440

22. GTEx Consortium. The GTEx Consortium atlas of genetic regulatory effects across human tissues. *Science.* 2020;369(6509):1318-1330. doi:10.1126/science.aaz1776

23. Chang H, Cai X, Li H, Liu W, Zhao L, Zhang C, et al. Functional genomics identify a regulatory risk variation rs4420550 in the 16p11.2 schizophrenia-associated locus. *Biol Psychiatry.* 2021;89(3):246-255. doi:10.1016/j.biopsych.2020.09.016

24. McCarthy SE, Makarov V, Kirov G, Addington AM, McClellan J, Yoon S, et al. Microduplications of 16p11.2 are associated with schizophrenia. *Nat Genet.* 2009;41(11):1223-1227. doi:10.1038/ng.474

25. Golzio C, Willer J, Talkowski ME, Oh EC, Taniguchi Y, Jacquemont S, et al. KCTD13 is a major driver of mirrored neuroanatomical phenotypes of the 16p11.2 copy number variant. *Nature.* 2012;485(7398):363-367. doi:10.1038/nature11091

26. Kozlitina J, Smagris E, Stender S, Nordestgaard BG, Zhou HH, Tybjærg-Hansen A, et al. Exome-wide association study identifies a TM6SF2 variant that confers susceptibility to nonalcoholic fatty liver disease. *Nat Genet.* 2014;46(4):352-356. doi:10.1038/ng.2901

27. Mahajan A, Spracklen CN, Zhang W, Ng MCY, Petty LE, Kitajima H, et al; DIAMANTE Consortium. Multi-ancestry genetic study of type 2 diabetes highlights the power of diverse populations for discovery and translation. *Nat Genet.* 2022;54(5):560-572. doi:10.1038/s41588-022-01058-3

28. Lam M, Chen CY, Li Z, Martin AR, Bryois J, Ma X, et al. Comparative genetic architectures of schizophrenia in East Asian and European populations. *Nat Genet.* 2019;51(12):1670-1678. doi:10.1038/s41588-019-0512-x

29. GTEx Consortium. The GTEx Consortium atlas of genetic regulatory effects across human tissues. *Science.* 2020;369(6509):1318-1330. doi:10.1126/science.aaz1776

30. Zhuo C, Zhang Q, Wang L, Ma X, Li R, Ping J, et al. Insulin resistance/diabetes and schizophrenia: potential shared genetic factors and implications for better management of patients with schizophrenia. *CNS Drugs.* 2024;38:33-44. doi:10.1007/s40263-023-01057-w
