## KidneyInCHRIS part of TrainCKDis Horizon 2020 EU Project
Genetic determinants of Kidney function in The **C**orporative **H**ealth **R**esearch **I**n **S**outh Tyrol (CHRIS) study

Several issues have been created to track the progress in the project. Here is the list of the issues in chronological order:

* [1- Picking the discovery Loci](#1-picking-the-discovery-loci)
* [2- Subtracting CHRIS from CKDGen](#2-subtracting-chris-from-ckdgen)
* [3- Phenotype creation](#3-phenotype-creation)
* [4- Conducting GWAS on renal function](#4-conducting-gwas-on-renal-function)
* [5- Comparing replicated variants effect magnitude with discovery studies](#)
* [6- Comparing the 147 CKDGen Loci in CHRIS](#)
* [7- Excluding batch effects from the health traits using transformation](#)
* [8- Extracting dosage level of the replicated SNPs from VCF file](#)
* [9- Phenome-wide mediation analysis](#)
* [10- Kidney interaction with Thyroid](#10.kidney-interaction-with-thyroid)
* [11- Sensitivity Analyses](#11-sensitivity-analyses)
* [12- Interrogating SNPs in Phenoscanner](#12-interrogating-snps-in-phenoscanner)
___________________________________________________________________________________________________________


## 1. Picking the discovery Loci

## 2. Subtracting CHRIS from CKDGen
- We were going to indipendentizing CKDGen results by subtracting CHRIS 5K from CKDGen Meta-GWAS on European ancestry.

## 3. Phenotype creation

## 4. Conducting GWAS on renal function
- We mapped the genotypes of CHRIS 10K participants to our interested phenotype, __ln(eGFR)__, by conducting genome-wide association study (GWAS) analysis.

## 5. Comparing replicated variants effect magnitude with discovery studies

## 6. Comparing the 147 CKDGen Loci in CHRIS

## 7. Excluding batch effects from the health traits using transformation

## 8. Extracting dosage level of the replicated SNPs from VCF file

## 9. Phenome-wide mediation analysis

## 10. Kidney interaction with Thyroid



## 11. Sensitivity Analyses
### Sensitivity of SNPs' dosage to having missing in FT3/4
- Here we test if there is any difference between the dosage level for the replicated SNPs for those cases having missing in FT3 or FT4 due to the artifacts resulted from using a two-sided Wilcoxon test (alpha = 0.05):
```R
#Sensitivity test for missing in FT3:
wilcox.test(SNP ~ FT3_indicator, data = vcfReg)

#Sensitivity test for missing in FT4:
wilcox.test(SNP ~ FT4_indicator, data = vcfReg)
```
### Sensitivity of the FT3/4-adjusted association of SNPs on log(eGFR) to Municipality
- Here we test how the association of SNPs on log(eGFR) changes when we adjust the LR model both for FT3/4 and municipality. This variable indicates the unmeasured differences in allele frequency of the SNPs between different villages in the region where CHRIS study was conducted. Truly, this idea is coming from where we thought adding municipality could affect the SNP-Kidney adjusted association FT3 or FT4, and in this way we might capture the batch effects in order to have an unbiased idea of the interaction between the kidney and thyroid traits.
- Thus, we tested the association of the SNP and kidney adjusted for FT3/4 once without adjusting for municipality and once with adjusting for it as below:
```R
#Sensitivity test for FT3:
log(eGFR) ~ SNP +FT3 + Sex + Age vs. log(eGFR) ~ SNP +FT3 + Sex + Age + Municipality

#Sensitivity test for FT4:
log(eGFR) ~ SNP +FT4 + Sex + Age vs. log(eGFR) ~ SNP +FT4 + Sex + Age + Municipality
```

## 12. Interrogating 163 replicated SNPs in Phenoscanner

