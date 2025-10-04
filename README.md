# Effort_Perception

Raw data files (.mat) are available on Zenodo: 10.5281/zenodo.17238287

Portions of this code were developed with assistance from ChatGPT (OpenAI). The AI was used to help draft and refine code, but all outputs were reviewed and edited by the author to ensure accuracy and appropriateness.

The codes contains the analysis code for the  study " Trait-like neural signatures of physical effort perception dissociated from motor execution in humans" lead by Diego Lombardo and supervised by Florian Monjo, which investigates the relationship between brain activity and perceived effort during a cognitive task. The codes () loads fMRI data from a group of participants, extracts average BOLD signal from predefined regions of interest (ROIs), and performs linear regression to predict perceived effort scores while controlling for head motion. It includes procedures for outlier removal, permutation testing to assess statistical significance, and Holm-Bonferroni correction for multiple comparisons. The analysis also computes partial Spearman correlations to examine the unique contribution of each ROI, controlling for all other ROIs and motion artifacts. Finally, the code generates high-quality visualizations with shaded confidence intervals to illustrate the results.

A detailed README with code explanations will be added soon.
