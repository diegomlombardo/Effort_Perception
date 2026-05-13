Neural Signatures of Physical Effort Valuation


This repository contains the full analysis pipeline for the study “Behavioral tendencies toward physical effort shape neural encoding of effort signals in sensory and cingulate cortices” by Diego-Martin Lombardo, Florian Marchand, Florian Malaussena, Alexandre Krainik, Emilie Cousin, Boris Cheval, Matthieu Boisgontier, Benjamin Pageaux, Aurélien Delphin, Johan Pietras, and Florian Monjo.

The project investigates how subjective perception of physical effort, quantified as Perceived Effort Scores (PES), relates to task-based fMRI activity. The main objective is to determine whether stable, trait-like neural signatures of perceived effort can be identified, and whether these signals are independent from confounding factors such as head motion and actual force production.

All raw neuroimaging and behavioral data used in this study are publicly available on Zenodo at https://doi.org/10.5281/zenodo.17238287
. In addition to this dataset, the repository requires the file behavioral_fMRIFD_data.mat, which contains Perceived Effort Scores, framewise displacement (head motion), and behavioral metadata for 44 participants.

The analysis pipeline is implemented in MATLAB and R and covers behavioral processing, ROI-based fMRI signal extraction, statistical modeling, and figure generation. The workflow begins with preprocessing and extraction of region-specific BOLD signals, followed by linear regression models where PES is the main outcome variable. Head motion is included as a covariate in all relevant analyses to ensure that results are not driven by movement-related artifacts. Across scripts, statistical inference relies on permutation testing, Holm–Bonferroni correction for multiple comparisons, and partial Spearman correlations to isolate the unique contribution of each brain region while accounting for other ROIs and motion parameters.

Download the file “behavioral_fMRIFD_data.mat”, which contains PES scores, head movement data, and the full dataset, from: https://doi.org/10.5281/zenodo.17238287
Then, run the MATLAB scripts from the main (home) directory using the subject-specific fMRI dataset, which includes behavioral measures and head motion data loaded into the workspace

The main regression analyses are implemented in the scripts RegressionModel_INB_Control_together, Model_Control_task, and Model_Experimental_task. The first script runs the full multivariate regression framework combining all ROIs and conditions and produces the main brain–behavior association results reported in the manuscript. The control and experimental task scripts apply the same modeling strategy separately for each condition. Statistical significance is assessed using permutation testing and corrected using Holm–Bonferroni procedures.

Effect sizes are computed in the script Effect_sizes using Cohen’s f². This is done by comparing a full model including all ROIs and head motion against reduced models where individual ROI groups are removed. Head motion is always retained in both models to avoid inflation of neural effects due to movement-related variance.

Generalization performance is assessed using leave-one-subject-out cross-validation in the script LOSO_cross_validation. In each iteration, the model is trained on all participants except one and used to predict the left-out participant’s perceived effort score. The procedure provides estimates of predictive accuracy, including Pearson correlation and root mean squared error, as well as variability in regression coefficients across folds.

Force data are processed using the Force_processing script. This script detects peaks and troughs in force signals, computes peak-to-peak differences, and normalizes force values relative to each participant’s maximal voluntary contraction. It also includes subject exclusion criteria, outlier detection, and group comparisons between conditions.

The Fig_S2 script tests whether brain–behavior relationships could be explained by differences in actual force production. It evaluates correlations between BOLD activity in regions such as primary somatosensory cortex and cingulate cortex and multiple force-related measures using permutation-based Spearman correlations with 10,000 iterations. Results are corrected for multiple comparisons using Holm–Bonferroni adjustment.

Descriptive statistics and group-level summaries are generated in the Table_S1 script. This script organizes participant information such as age, head motion, perceived effort, muscle strength, and ROI-based brain activity measures, and groups participants according to physical activity level.

The essential scripts to reproduce the main results are Model_Experimental_task_Fig2, which reproduces the regression analyses for Figure 2, Model_Control_task_Fig3, which reproduces the control condition analyses for Figure 3, plot_figs2_3_Main_Manuscript, which generates the main figures for both conditions, LOSO_cross_validation_Figure_S4, which performs cross-validation analyses, Fig_S3, which runs partial correlation analyses with permutation testing and bootstrap confidence intervals while controlling for force, Fig_S2_ACC_Vs_PCC, which dissociates ACC and PCC contributions within the cingulate model, and RegressionModel_INB_Control_Table_S5, which tests the full combined model and computes variance inflation factors to assess multicollinearity.

Overall, this repository provides a fully reproducible analysis pipeline linking subjective physical effort perception to brain activity measured with fMRI. The analyses carefully control for motor output and motion-related confounds and combine regression modeling, permutation-based statistics, and cross-validation to ensure robust inference about the neural basis of perceived valuation.

Author

Diego Lombardo
Université Savoie Mont-Blanc
