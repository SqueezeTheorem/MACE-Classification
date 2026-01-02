# MACE-Classification
Population Classification Using SNPs 


# SNP Analysis Report: Additive, Dominant, Recessive (ADR) Modeling
Findings of a "Deep SNP Analysis" performed on the uncorrelated dataset. The dataset is first cleaned by filtering out highly correlation features. Not all the SNP behave in the ideal  and categorize each SNP based on its most likely biological mode of inheritance: **Additive**, **Dominant**, or **Recessive**.

## Methodology

For every Single Nucleotide Polymorphism (SNP) in the dataset, we tested three competing logistic regression models against the `OUTCOME SEVERITY` variable:

1. **Additive Model**: Assumes a linear increase in risk with each additional copy of the minor allele.
   - _Encoding_: 0 (Homozygous Major) -> 1 (Heterozygous) -> 2 (Homozygous Minor).
2. **Dominant Model**: Assumes that having at least one copy of the minor allele is sufficient to confer risk.
   - _Encoding_: 0 -> 0; 1 & 2 -> 1.
3. **Recessive Model**: Assumes that two copies of the minor allele are required to see the effect.
   - _Encoding_: 0 & 1 -> 0; 2 -> 1.

**Model Selection:** We used the **Akaike Information Criterion (AIC)** to select the best model for each SNP.

> _The model with the lowest AIC is considered the best fit as it balances goodness-of-fit with model simplicity._
