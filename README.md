Neural Signatures of Physical Effort Valuation


This repository contains the full analysis pipeline for the study “Behavioral tendencies toward physical effort shape neural encoding of effort signals in sensory and cingulate cortices” by Diego-Martin Lombardo, Florian Marchand, Florian Malaussena, Alexandre Krainik, Emilie Cousin, Boris Cheval, Matthieu Boisgontier, Benjamin Pageaux, Aurélien Delphin, Johan Pietras, and Florian Monjo.

The project investigates how subjective perception of physical effort, quantified as Perceived Effort Scores (PES), relates to task-based fMRI activity. The main objective is to determine whether stable, trait-like neural signatures of effort vaulation can be identified, and whether these signals are independent from confounding factors such as head motion and actual force production.

All raw neuroimaging and behavioral data used in this study are publicly available on Zenodo at https://doi.org/10.5281/zenodo.17238287
In addition to this dataset, the repository requires the file behavioral_fMRIFD_data.mat, which contains Perceived Effort Scores, framewise displacement (head motion), and behavioral metadata for 44 participants.

The analysis pipeline is implemented in MATLAB and R and covers behavioral processing, ROI-based fMRI signal extraction, statistical modeling, and figure generation. The workflow begins with preprocessing and extraction of region-specific BOLD signals, followed by linear regression models where PES is the main outcome variable. Head motion is included as a covariate in all relevant analyses to ensure that results are not driven by movement-related artifacts. Across scripts, statistical inference relies on permutation testing, Holm–Bonferroni correction for multiple comparisons, and partial Spearman correlations to isolate the unique contribution of each brain region while accounting for other ROIs and motion parameters.

Download the file “behavioral_fMRIFD_data.mat”, which contains PES scores, head movement data, and the full fMRI BOLD timeseries in .mat files (data structure explained in the Zenodo repository), from: https://doi.org/10.5281/zenodo.17238287
Then, run the MATLAB scripts from the main (home) directory using the subject-specific fMRI dataset, having the behavioral measures of PES and head motion data already loaded into the workspace

The main regression analyses are implemented in the scripts "RegressionModel_INB_Control_together" table S5, Model_Control_task, and Model_Experimental_task. The first script runs the full multivariate regression framework combining all ROIs and conditions and produces the main brain–behavior association results reported in the manuscript. The control and experimental task scripts apply the same modeling strategy separately for each condition. Statistical significance is assessed using permutation testing and corrected using Holm–Bonferroni procedures.

Effect sizes are computed in the script Effect_sizes using Cohen’s f². This is done by comparing a full model including all ROIs and head motion against reduced models where individual ROI groups are removed. Head motion is always retained in both models to avoid inflation of neural effects due to movement-related variance.

Generalization performance is assessed using leave-one-subject-out cross-validation in the script LOSO_cross_validation. In each iteration, the model is trained on all participants except one and used to predict the left-out participant’s perceived effort score. The procedure provides estimates of predictive accuracy, including Pearson correlation and root mean squared error, as well as variability in regression coefficients across folds.

Force data are processed using the Force_processing script. This script detects peaks and troughs in force signals, computes peak-to-peak differences, and normalizes force values relative to each participant’s maximal voluntary contraction. It also includes subject exclusion criteria, outlier detection, and group comparisons between conditions.

Descriptive statistics and group-level summaries are generated in the Table_S1 script. This script organizes participant information such as age, head motion, perceived effort, muscle strength, and ROI-based brain activity measures, and groups participants according to physical activity level.

How to do?:

downolad the "behavioral_fMRIFD_data.mat"  and the .mat files in the Zenondo pubished in Sept 30 2025 https://doi.org/10.5281/zenodo.17238287 then copy and paste in the command window of matlab in the home folder witht the un-ziped data "matfiles_fMRI_Effort_Less.zip"  

The essential scripts required to reproduce the main results are Model_Experimental_task_Fig3, which reproduces the regression analyses presented in Figure 2, and Model_Control_task_Fig4, which reproduces the statistical model for the Control condition analyses shown in Figure 3. After running these regression and partial correlation models, the script plot_figs3_4_Main_Manuscript can be executed (copy and paste in the command Matlab window after run each model INB and Control) to generate Figures 2 and 3 of the manuscript, corresponding to the INB (Figure 2) and Control (Figure 3) conditions, as well as produce the partial correlations reported in Table 1.

Additional scripts include LOSO cross validation "Figure_S1", which performs the leave-one-subject-out cross-validation analyses; Fig_S3, which runs partial correlation analyses with permutation testing and bootstrap confidence intervals while controlling for force; Fig_3_Main_Manuscript_ACC_Vs_PCC, which dissociates the contributions of the anterior cingulate cortex (ACC) and posterior cingulate cortex (PCC) beyond the cingulate cortex Meta-ROI. RegressionModel_INB_Control_Table_S5 tests the full combined model and computes variance inflation factors (VIFs) to assess multicollinearity.

The "Fig_S2" script specifically examines whether brain–behavior relationships could be explained by differences in actual force production. It evaluates correlations between BOLD activity in regions such as the primary somatosensory cortex and cingulate cortex and multiple force-related measures using permutation-based Spearman correlations with 10,000 iterations. Results are corrected for multiple comparisons using the Holm–Bonferroni adjustment.

Overall, this repository provides a fully reproducible analysis pipeline linking subjective physical effort valuation to brain activity measured with BOLD fMRI. The analyses carefully control for motor output and motion-related confounds and combine regression modeling, permutation-based statistics, and cross-validation to ensure robust inference about the neural basis of perceived valuation.

Author

Diego Lombardo
Université Savoie Mont-Blanc
