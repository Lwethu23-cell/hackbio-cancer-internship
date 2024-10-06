---
Scientific paper reproduction: Machine Learning Prediction of Cancer Cell Sensitivity to Drugs Based on Genomic and Chemical Properties
---

**Authors: Ntsieni Midalo Shaka, Twana Lwethu, Owoloye Babatunde Henry**

**INTRODUCTION:**

The study \"Machine Learning Prediction of Cancer Cell Sensitivity to
Drugs Based on Genomic and Chemical Properties\" investigates the use of
machine learning to forecast how pharmaceuticals would affect cancer
cells. The approach seeks to improve tailored treatment techniques by
identifying drug sensitivity patterns through the integration of genetic
and chemical features. It shows how the chemical characteristics of
medications in conjunction with genomic data, including gene expression,
might enhance forecasts of therapeutic success in cancer therapy.

**METHODOLOGY:**

The study tested machine learning algorithms like Support Vector
Machines (SVM), Random Forests, and Neural Networks for classification
tasks. The models were evaluated using metrics like MAE and R-squared,
and cross-validation techniques were used to ensure robustness. The
authors also integrated genomic and chemical features to enhance
predictive power, recognizing the influence of drug and cancer cell
molecular and biological characteristics on drug response.

**KEY FINDINGS:**

Neural networks and random forests have been used to predict missing log
(IC50) values across 111 drugs, with an averaged Pearson correlation
coefficient (Rp), coefficient of determination (R Squared), and root
mean square error (RMSE) of 0.85, 0.72, and 0.83, respectively. The
models\' predictive power did not fall off in quality even with fewer
IC50 values. They also demonstrated the accuracy of their model for
unknown cell lines, with an Rp of 0.82, R2 of 0.68, and an RMSE of 0.89.
The predictive power of these models is expected to increase as larger
drug sensitivity and genomic datasets become available. The predictive
ability of individual values is limited and could be improved by
extending the set of input features with additional layers of molecular
characterization of cell lines. The models can estimate the accuracy of
prediction for different degrees of sparseness in the data, which may be
useful in designing experiments with balanced coverage and accuracy.

**ML METHODOLOGY:**

To begin training the model onto the data, we need to import the xlsx
file named “GDSC1_fitted_dose_response_27Oct23”and make a dataframe of the information. It is important to clean and curate data by removing missing values by dropping NaN, removing duplicate rows, and converting columns to appropriate data types. To select the cell line name of interest which in this instance is “SK-MEL-2” due to 378 entries, it is important to choose a cell line name with many entries for better performance and results from the model. The data frame is then manipulated to show the four important columns: CELL_LINE_NAME, TCGA_DESC, DRUG_NAME, and LN_IC50. SMILES of the drug names were generated from the PubChem database and further cleaned with the function .dropna.The sorted dataframe and the SMILES dataframe were concatenated and descriptors were generated to yield “df_final” data frame.Test data is then generated from the whole data for model evaluation purposes.

To identify a model that would work well with our data, we trained the Pycaret model.Ridge Regression. It provides the best performance in MSE and RMSE, with a solid balance of accuracy and efficiency.The model  balances the bias-variance trade-off while minimising significant errors (MSE and RMSE). It prevents overfitting and lessens the effect of extreme values by adding a regularisation component to the loss function. Ridge also prevents overfitting by shrinking the coefficients of less significant features. Because of its rapid computing efficiency, it can be used for frequent retraining or with big datasets. Because its  regularisation stabilises the model against little fluctuations in the data, it works well in ill-conditioned situations like multicollinearity. Ridge Regression strikes a balance between error minimization and model simplicity, resulting in smoother and easier-to-understand output—even though it does not have the lowest error for every statistic.

The ridge regression model was then evaluated using the test data set yielding the output:
Mean Squared Error (MSE): 8.5540
R-squared (R2): -0.0182
Mean Absolute Error (MAE): 2.2066

**RESULTS:**

The 3 metrics generated through model evaluation indicate that it has
difficulty explaining the dataset\'s variance and may occasionally
produce predictions that are very different from the actual values due
to the model\'s high MSE and negative R2.

According to MAE, there is a moderate level of error in the model\'s
predictions, with an average deviation of 2.2 units.

![image4](https://github.com/user-attachments/assets/b23295ee-485a-45c0-be56-cdf16a45fa83)


Correlation Coefficient: 0.2679

The model is predicting IC50 rather well for many cases, as evidenced by
the majority of data points falling along a diagonal line (predicted and
actual values are near).

Though forecasts appear less accurate, there is a noticeable spread away
from the diagonal, especially in the lower IC50 ranges (Actual IC50 \<
0).

For **higher Actual IC50 values**, there is a tighter clustering along
the diagonal, indicating better performance.

the model performs very well for moderate to high IC50 values, but as
the considerable departure from the diagonal line in those regions
indicates, it has trouble predicting low or negative IC50
values.Additionally, the prediction variance is larger for LN_IC50
values between -2.5 and 0.

A correlation coefficient of **0.2679** indicates a **positive but weak
correlation** between the actual IC50 values and the predicted IC50
value. The correlation coefficient value is close to 0, suggesting that
while there is some positive relationship , the correlation is not
strong enough to indicate a reliable predictive relationship. a
correlation coefficient of 0.2679 suggests that while there is some
relationship between the actual and predicted values, the predictive
power of your model is limited.

**COMPARISON:**

Our model\'s R-squared (R²) value of -0.0182 indicates a low ability to
explain variance in the data. Menden et al.\'s model exhibits higher R²
values, indicating a major amount of variance in medication response.
Their models have lower MSE values, indicating decreased prediction
error. Their average absolute error (MAE) between the predicted and
actual IC50 values is 2.2066, which is a significant difference. The
models by Menden et al. exhibit reduced absolute errors, with RMSE
values ranging from 0.83 to 0.89. The weak positive association between
the expected and actual IC50 values is indicated by their Pearson
correlation coefficient of 0.2679. The stronger positive connection
between expected and actual values is indicated by Menden et al.\'s
higher correlation coefficient, which is 0.85 for the majority of data
and 0.82 for unknown cell lines.

**CONCLUSION:**
The model's performance is poor in predicting IC50 values, with high error values and weak correlations. Menden et al.'s model, using neural networks and random forests, performed significantly better, showing higher predictive power, strong correlations, lower errors, and better fit, as indicated by a high R².When compared to the findings in Menden et al., our model's predictive performance is noticeably worse, indicating that the model, features, or data size selection may be improved.

**REFERENCE LIST:**

1.  [Menden MP, Iorio F, Garnett M, McDermott U, Benes CH, Ballester PJ,
    > et al. (2013) Machine Learning Prediction of Cancer Cell
    > Sensitivity to Drugs Based on Genomic and Chemical Properties.
    > PLoS ONE 8(4): e61318.
    > [[https://doi.org/10.1371/journal.pone.0061318]{.underline}](https://doi.org/10.1371/journal.pone.0061318)]{.mark}

Phase 2 :

**INTRODUCTION:**

Histone deacetylases (HDACs) are crucial regulators of gene expression
and play a significant role in various cellular processes, including
differentiation, proliferation, and apoptosis. Dysregulation of HDAC
activity has been implicated in several cancers, making them promising
targets for therapeutic intervention. By removing acetyl groups from
histones and non-histone proteins, HDACs can silence tumour suppressor
genes and promote oncogenic pathways, leading to uncontrolled cell
growth and survival.

Selective HDAC inhibitors have gained attention as potential anticancer
agents, as they can restore the expression of silenced genes and induce
cancer cell apoptosis. Different HDAC subtypes have distinct roles in
cancer progression; for instance, HDAC11 is associated with
neuroblastoma and has been identified as a target for selective
inhibition.

Developing drugs that specifically inhibit HDACs can provide more
effective treatment options with reduced side effects compared to
traditional chemotherapy. By utilising advanced techniques such as
structure-based design and computational modelling , researchers aim to
design selective HDAC inhibitors that can target specific cancer types,
ultimately improving therapeutic outcomes in oncology.

**LIGAND LIBRARY:**

A curated library of 50 phytochemicals from *Artemisia afra* and 11 HDAC
subtypes has been established, with each compound documented by chemical
name, SDF structural format, PubChem CID, and scientific
references\[10\]. These 61 compounds will act as ligands in molecular
docking studies, providing a precise dataset for interaction analysis
with HDACs, facilitating the exploration of binding affinities and
potential therapeutic applications.

**PROTEIN PREPARATION** :

The protein structure of HDAC11 was selected as the target for docking
analysis\[2\]. The structure was refined using Biovia Studio, where
water molecules and bound ligands/heteroatoms were removed\[4\].
Hydrogen atoms were then added to the cleaned structure, which was
subsequently saved in PDB format for further analysis\[1\].

![image2](https://github.com/user-attachments/assets/d2462d3f-a94d-4b8b-917e-e7971de62559)


Figure 1: Preparation of the HDAC11 protein structure for docking using
Biovia Studio. The figure shows the cleaned protein with water molecules
and bound ligands removed and polar hydrogen atoms added.

**MOLECULAR DOCKING OF THE 11HDAC SUBTYPES AND 50 *Artemisia afra***

**PHYTOCHEMICALS :**

Active sites of HDAC11 were identified using fpocket. Energy
minimization of the 61 curated ligands was performed in PyRx\[3\], and
both protein and ligand structures were converted to pdbqt format\[11\].
Docking simulations were conducted in triplicates to ensure reliability
and reproducibility of the results, with the mean and standard deviation
of binding affinities calculated from the triplicate runs. A grid box
was applied over the active site, allowing for multiple binding modes to
be generated for each ligand.

The binding affinity analysis revealed that Lupeol demonstrated the
highest affinity for the HDAC11 protein. Its average docking score of
-10.16 indicates strong overall binding affinity. However, the standard
deviation of 4.3878 suggests significant variability in the docking
results. One score (-5.1) differs notably from the others (-12.7,
repeated twice), highlighting the inconsistency\[6\]. This large
standard deviation indicates that Lupeol may not consistently achieve
the high binding affinity observed in some trials.

**VISUALISATION OF THE LUPEOL LIGAND:**

![image1](https://github.com/user-attachments/assets/4ba00cdd-d953-408a-81a6-093dabc3d7c8)


Figure 3: [Visualisation of]{.mark} *Lupeol* [docked within the active
site of HDAC11, generated using Biovia Discovery Studio.]{.mark}

[Biovia Discovery facilitated the visualisation of Lupeol\'s binding
mode to HDAC11, providing valuable understanding of their molecular
interactions.]{.mark}

![image3](https://github.com/user-attachments/assets/e33a998d-f03d-4b60-9edc-818065659f67)


[Figure 4: Interaction diagrams of Lupeol with HDAC11, featuring a 3D
visualisation on the left that illustrates the ligand\'s conformational
orientation within the active site, and a 2D diagram on the right that
highlights key molecular interactions, including hydrogen bonds and
hydrophobic contacts with surrounding amino acid residues.]{.mark}

**[COMPARISON:]{.mark}**

[This study identifies Lupeol as a promising HDAC11 inhibitor with a
high binding affinity (-10.16) and emphasises the significance of
molecular docking simulations conducted in triplicates to ensure
reliability, despite observed variability (standard deviation of
4.3878). In contrast, the article by Baselious et al. utilises an
optimised AlphaFold protein model for structure-based design, likely
leading to enhanced accuracy in identifying selective inhibitors for
HDAC11, especially in relation to anti-neuroblastoma activity. While
this research highlights the potential of natural phytochemicals like
Lupeol, Baselious et al. emphasise advanced computational techniques
that may provide deeper insights into ligand-protein interactions,
ultimately contributing to more effective and selective therapeutic
options in cancer treatment.]{.mark}

**CONCLUSION:**

This research identified several novel compounds with significant
binding interactions with Histone Deacetylase (HDAC), suggesting their
potential as effective therapeutic agents for diseases linked to HDAC
dysfunction\[5\]. The findings also introduced a comprehensive approach
for protein-ligand docking studies, creating a versatile framework for
future drug development initiatives aimed at targeting similar enzymes.

**REFERENCES**

1.  [Berman, H. M., Westbrook, J., Feng, Z., Gilliland, G., Bhat, T. N.,
    > & Weissig, H., 2000. The Protein Data Bank. Nucleic Acids
    > Research, 28(1), pp. 235-242.]{.mark}

2.  [Case, D. A., Cheatham, T. E., Darden, T., Gohlke, H., Luo, R., &
    > Merz, K. M., 2021. The Amber Biomolecular Simulation Programs.
    > Journal of Computational Chemistry, 22(5), pp. 1019-1041.]{.mark}

3.  [Dallakyan, S., & Olson, A. J., 2015. Small-Molecule Library
    > Screening by Docking with PyRx. In: Chemical Biology, New York:
    > Humana Press, pp. 243-250.]{.mark}

4.  [Dassault Systèmes BIOVIA, 2020. Discovery Studio Modeling
    > Environment. San Diego: Dassault Systèmes.]{.mark}

5.  [Dokmanovic, M., Clarke, C., & Marks, P. A., 2007. Histone
    > Deacetylase Inhibitors: Overview and Perspectives. Molecular
    > Cancer Research, 5(10), pp. 981-989.]{.mark}

6.  [Humphrey, W., Dalke, A., & Schulten, K., 1996. VMD: Visual
    > Molecular Dynamics. Journal of Molecular Graphics, 14(1), pp.
    > 33-38.]{.mark}

7.  [Kim, D. E., Choi, J., & Park, S. Y., 2019. Chemical Libraries and
    > Molecular Docking: Key Tools for Structure-Based Virtual
    > Screening. Current Opinion in Chemical Biology, 50, pp.
    > 123-129.]{.mark}

8.  [Le Guilloux, V., Schmidtke, P., & Tuffery, P., 2009. Fpocket: An
    > Open Source Platform for Ligand Pocket Detection. BMC
    > Bioinformatics, 10(1), p. 168.]{.mark}

9.  [Marks, P. A., & Breslow, R., 2007. Dimethyl Sulfoxide to
    > Vorinostat: Development of a Histone Deacetylase Inhibitor. Nature
    > Biotechnology, 25(1), pp. 84-90.]{.mark}

10. [Mmutlane, E. M., Koorbanally, N., & Mulholland, D. A., 2017.
    > Phytochemistry of Artemisia afra and the pharmacological basis of
    > its therapeutic applications. African Journal of Traditional,
    > Complementary, and Alternative Medicines, 14(1), pp. 1-10.]{.mark}

11. [Trott, O., & Olson, A. J., 2010. AutoDock Vina: Improving the Speed
    > and Accuracy of Docking with a New Scoring Function, Efficient
    > Optimization, and Multithreading. Journal of Computational
    > Chemistry, 31(2), pp. 455-461.]{.mark}

12. [Wang, J., Dong, C., Xu, L., Xiong, Y., Li, J., & Tan, Y., 2020.
    > Histone Deacetylases (HDACs) and Their Inhibitors: Molecular
    > Mechanisms and Therapeutic Potential. Journal of Medicinal
    > Chemistry, 63(21), pp. 12458-12482.]{.mark}
