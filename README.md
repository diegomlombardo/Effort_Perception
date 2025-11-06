# Neural Signatures of Physical Effort Perception

This repository contains analysis code for the study:  
**"Trait-like neural signatures of physical effort perception dissociated from motor execution in humans"**  
Led by **Diego Lombardo**

Raw data files (.mat) are available on Zenodo: https://doi.org/10.5281/zenodo.17238287 and are needed to use this scripts along with the PES and head movement data inside of the .mat file in this attached this GitHub "behavioral_fMRIFD_data.mat"

This repository contains the analysis code for the study titled "Trait-like neural signatures of physical effort perception dissociated from motor execution in humans", led by Diego Lombardo and supervised by Florian Monjo. The study explores the relationship between brain activity and perceived effort. The scripts (Model_Control_task and Model_Experimental_task) load fMRI data from a group of participants, using Perceived Effort Scores (PES) as input. They extract the average BOLD signal from predefined regions of interest (ROIs) and perform linear regression analyses to predict perceived effort while controlling for head motion. The pipeline includes outlier removal, permutation testing to assess statistical significance, and Holm-Bonferroni correction for multiple comparisons. Additionally, the analysis computes partial Spearman correlations to assess the unique contribution of each ROI, controlling for other ROIs and motion artifacts. High-quality visualizations with shaded confidence intervals are generated to illustrate the results. These regression and partial correlation analyses correspond to Figure 1, Figure 2, and Table 1 in the Results section of the manuscript. To use these codes fist has to be uploaded the file " behavioral_fMRIFD_data.mat" containing for 44 subjects framewise displacement in fMRI (head movement) and PES scores form original data bases

This script "Effect_sizes" computes the effect size (Cohen’s f²) for each brain region of interest (ROI) used as a predictor in a multiple linear regression model. The model predicts a behavioral outcome based on BOLD activity from different ROI groups, while controlling for head motion. For each ROI group, the script calculates how much variance in the outcome is uniquely explained by that group, by comparing the R² of the full model (including all predictors) with the R² of a reduced model where that specific ROI group is removed. Head motion is kept in both the full and reduced models to control for confounding effects. The result is a set of f² values that quantify the individual contribution of each ROI group to the model.

This " Table_S1" R script processes a master Excel dataset to prepare and summarize participant data across three physical activity groups: Sedentary, Average, and Sportif. It loads relevant libraries, cleans and converts variables (including PES and MVC) to proper numeric formats, and applies descriptive labels to key behavioral and neuroimaging measures. Finally, it generates a Table 1 summary using the table1 package, presenting group-wise statistics for age, head motion (FD), perceived effort, muscle strength (MVC), and task-based fMRI BOLD responses across several brain regions for both control and ischemia conditions.

This MATLAB script "LOSO_cross_validation" implements a Leave-One-Subject-Out (LOSO) cross-validation procedure to evaluate the predictive power of task-based fMRI ROI activity and head motion metrics in predicting behavioral outcomes (e.g., perceived effort scores). For each subject, the model is trained on the remaining data and used to predict the held-out response, storing predictions and regression coefficients. After cross-validation, the script reports overall performance metrics (Pearson’s r, RMSE), summarizes beta coefficients across folds, and fits a full cohort model with p-values. It also generates publication-quality plots of LOSO predictions and ROI-specific beta trajectories across folds Fig S3.

This MATLAB script "Force_processing" in Fig S1 processes raw force data collected during MVC and two task conditions (Task 1 and Task 2) for a cohort of subjects. For each condition, it detects local maxima and minima (peaks and troughs) in the force signal, computes the average absolute difference between successive peaks, and derives a mean peak difference per subject. These values are then scaled as a percentage of the subject's MVC, providing normalized force metrics across conditions. The script includes subject exclusion, outlier detection, and a paired t-test to assess whether Task 1 and Task 2 differ significantly in scaled force output. A publication-ready boxplot is generated to visualize within-subject comparisons between task conditions.

Script: "Fig S2" This R script evaluates whether individual differences in BOLD activity within the primary somatosensory cortex (S1), previously associated with perceived effort (PES), could instead be explained by differences in physical force output during the fMRI scanning session. The goal of this analysis is to test whether the observed neural correlates of effort perception are confounded by actual exerted force. The script loads and preprocesses data from Master_Data_Base.xlsx, converting key columns to numeric format and removing outliers beyond three standard deviations. It then performs permutation-based Spearman correlation tests (10,000 iterations) between BOLD activity in S1 (under both control and ischemia conditions) and three force-related measures: force during Task 1, force during Task 2, and maximum voluntary contraction (MVC). P-values from the permutation tests are adjusted using Holmes-Bonferroni method for mutiple comparisson correcction. Finally, the script generates a series of scatter plots showing the relationship between BOLD activity and each force metric, including regression lines and annotations for Spearman’s rho and adjusted significance levels. These visualizations help determine whether neural signals linked to perceived effort are independent of actual force production

The most important scripts that contain the main results are:

"RegressionModel_INB_Control_together"

"Model_Control_task"

"Model_Experimental_task"

The first script runs the regression model and partial correlations, and also generates figures for the brain–behavior associations reported in the working manuscript. This includes the ROIs in the same model for both the experimental and control tasks. The last two scripts run the analyses separately for the control and experimental tasks. Regression betas and Spearman’s rho (r) are reported, along with p-values corrected using the Holm–Bonferroni method.


Still in progress — I’ll complete it soon. Doing my best as I go!

% Some parts of this code were developed with assistance from ChatGPT by OpenAI.

