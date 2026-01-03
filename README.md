# SNP Analysis Report: MACE-Classification
Population Classification Using SNPs 

# "Stable" SNP selection using Lasso Bootstrapping
This method essentially fit a Lasso classification model for over few hundered random sample. SNPs are sorted as per weight in the linear model and the top SNPs that appear >= 80-90% of the time in the top order are selected as the "stable" SNPs for classfication task. Lasso algorithm performs automated variable selection by shrinking the coefficients of weak or redundant SNPs to exactly zero. We then calculated a Stability Score for each marker, representing the percentage of times it was selected as a significant predictor across all iterations.

# Additive, Dominant, or Recessive (ADR) Modeling
Findings of a "Deep SNP Analysis" performed on the uncorrelated dataset. The dataset is first cleaned by filtering out highly correlation features. Not all the SNP behave in the ideal  and categorize each SNP based on its most likely biological mode of inheritance: **Additive**, **Dominant**, or **Recessive**.

## Methodology

For every Single Nucleotide Polymorphism (SNP) in the dataset, we tested three competing logistic regression models against the `OUTCOME MACE` variable:

1. **Additive Model**: Assumes a linear increase in risk with each additional copy of the minor allele.
   - _Encoding_: 0 (Homozygous Major) -> 1 (Heterozygous) -> 2 (Homozygous Minor).
2. **Dominant Model**: Assumes that having at least one copy of the minor allele is sufficient to confer risk.
   - _Encoding_: 0 -> 0; 1 & 2 -> 1.
3. **Recessive Model**: Assumes that two copies of the minor allele are required to see the effect.
   - _Encoding_: 0 & 1 -> 0; 2 -> 1.

**Model Selection:** We used the **Akaike Information Criterion (AIC)** to select the best model for each SNP.

> _The model with the lowest AIC is considered the best fit as it balances goodness-of-fit with model simplicity._


