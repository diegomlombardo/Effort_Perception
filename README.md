Neural Signatures of Physical Effort Perception

This repository contains the analysis code for the study "Behavioral tendencies toward physical effort shape neural encoding of effort signals in sensory and cingulate cortices"
Diego-Martin Lombardo, Florian Marchand, Florian Malaussena, Alexandre Krainik, Emilie Cousin, Boris Cheval, Matthieu Boisgontier, Benjamin Pageaux, Aurélien Delphin, Johan Pietras, Florian Monjo

The project investigates how brain activity relates to perceived physical effort and whether stable, trait-like neural signatures can be identified that are independent of motor execution. In particular, the analyses focus on understanding how individual differences in perceived effort (quantified using Perceived Effort Scores, PES) relate to task-based fMRI activity, while carefully controlling for confounding factors such as head motion and actual force production.

Data availability

The raw neuroimaging and behavioral data used in this study are publicly available on Zenodo at https://doi.org/10.5281/zenodo.17238287
. In addition to the Zenodo dataset, this repository also requires the file behavioral_fMRIFD_data.mat, which contains Perceived Effort Scores, framewise displacement (head motion), and behavioral metadata for 44 participants.

General structure of the analysis

The analysis pipeline combines MATLAB and R scripts to process behavioral and fMRI data, extract ROI-based BOLD signals, and model their relationship with perceived effort. The workflow begins with preprocessing and extraction of region-specific signals, followed by statistical modeling using linear regression frameworks where PES is the primary outcome variable. Head motion is included as a covariate in all relevant models to ensure that results are not driven by movement-related artifacts.

Across the different scripts, the analyses include multiple regression models, permutation-based significance testing, Holm–Bonferroni correction for multiple comparisons, and partial Spearman correlations to isolate the unique contribution of each brain region while accounting for the influence of other ROIs and motion parameters. The results of these analyses are used to generate the main figures and tables in the manuscript, including Figures 1 and 2 and Table 1.

Main analysis scripts

The core statistical results of the manuscript are produced by the scripts RegressionModel_INB_Control_together, Model_Control_task, and Model_Experimental_task. The first of these implements the full regression framework, combining ROIs within a unified model and estimating both regression coefficients and partial correlations across experimental conditions. It is also responsible for generating the main brain–behavior association figures reported in the manuscript. The other two scripts apply the same modeling approach separately to the control and experimental tasks, allowing condition-specific effects to be examined. In all cases, statistical significance is assessed using permutation testing and corrected using the Holm–Bonferroni method.

Effect size estimation

The script Effect_sizes quantifies the contribution of each region of interest using Cohen’s f². This is done by comparing the explanatory power of a full regression model, which includes all ROIs and head motion, against reduced models in which each ROI group is removed one at a time. Head motion is always retained in both models to ensure that variance associated with movement does not inflate the contribution of neural predictors. The resulting f² values provide a measure of how strongly each ROI uniquely contributes to explaining variability in perceived effort.

Cross-validation analysis

The LOSO_cross_validation script implements a leave-one-subject-out validation procedure to evaluate how well fMRI-derived predictors generalize across participants. In each iteration, the model is trained on all but one subject and then used to predict the left-out participant’s perceived effort score. The procedure yields estimates of predictive accuracy, including Pearson correlation and root mean squared error, as well as distributions of regression coefficients across folds. These results are used to assess the stability and generalizability of the neural predictors.

Force processing

The Force_processing script handles preprocessing of raw force signals collected during maximal voluntary contraction (MVC) and task conditions. It detects peaks and troughs in the force time series, computes average peak-to-peak differences, and normalizes these values relative to each participant’s MVC. This allows force output to be compared across individuals. The script also includes subject exclusion procedures, outlier detection, and statistical comparison between task conditions using paired t-tests, with results visualized through publication-quality boxplots.

Force–brain relationship control analysis

The Fig S2 script evaluates whether observed relationships between brain activity and perceived effort could instead be explained by differences in actual force production. It does this by testing correlations between BOLD activity in regions such as primary somatosensory cortex and cingulate cortex and multiple force-related measures, including task force and MVC. These relationships are assessed using permutation-based Spearman correlations with 10,000 iterations, and p-values are corrected using Holm–Bonferroni adjustment. The resulting figures visualize whether neural signals related to effort remain significant after accounting for physical force.

Group-level statistics and table generation

The Table_S1 script prepares the dataset for descriptive statistical reporting. It loads a master Excel file, formats behavioral and neuroimaging variables, and assigns participants to groups based on physical activity level (Sedentary, Average, Sportif). It then generates a structured summary table including age, head motion, perceived effort, muscle strength, and ROI-based BOLD measures under both control and experimental conditions.

Summary

Overall, this repository provides a complete and reproducible analysis pipeline linking brain activity to subjective effort perception while rigorously controlling for motor output and motion-related confounds. The combination of regression modeling, cross-validation, and permutation-based statistics ensures robust inference about the neural basis of perceived physical effort.

Essential scripts:

Model_Experimental_task_Fig2 reproduces the regression analyses presented in Figure 2 of the manuscript, examining the prediction of PES scores from BOLD fMRI activity during the experimental task. Model_Control_task_Fig3 reproduces the predictive models for the control conditions presented in Figure 3.

"plot_figs2_3_Main_Manuscritp" make the plots for both coditions

"LOSO_cross_validation_Figure_S4" run the LOSSO cross-validation and the code

Author

Diego Lombardo
Université Savoie Mont-Blanc
