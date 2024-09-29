
# Docking and Pipeline Implementation

**Authors (@slack)**:  
- Samreen Raza (@samRaza)  
- Lwethu Twana (@Lwethu23)  
- Tanvi Thakur (@Jerry)

---

## Phase 1: Docking Implementation

### Introduction

Ovarian cancer has become one of the main causes of death in women globally, primarily due to its late-stage diagnosis and constrained treatment choices. Although advances in medication, long-term survival rates have not increased considerably. The latest study emphasizes the role of epigenetic regulation, such as histone changes, in cancer growth. Epigenetic alterations, such as histone modification and degradation, have an important impact on gene expression and have been identified as possible targets for therapy. 

Histone Deacetylase 4 (HDAC4) deacetylates lysine residues on core histones (H2A, H2B, H3, and H4) to control transcription, cell cycle progression, and maturation. It creates multiprotein complexes and acts with MEF2 factors to help in muscle maturity. HDAC4 epigenetically controls ESR1 in breast cancer and deacetylates HSPA1A/B proteins [1]. Increased levels of HDAC4 in malignancies such as ovarian and non-small cell lung cancer (NSCLC) are connected to active tumor characteristics as a negative prognosis, among those exhibiting decreased longevity [2].

Using PubChem [3] we selected 50 phytochemicals from Camellia sinensis, a widely used beverage recognized for its cancer prevention benefits [4]. 

### Methodology

#### 1. Protein Preparation

- Download the 6fyz structure from PDB [5], process it in Discovery Studio [6] by eliminating heteroatoms and water molecules, subsequently integrating polar hydrogens, and save it in PDB format

#### 2. Library Creation

- Curate 50 phytochemicals using PubChem, convert them into PDBQT format

#### 3. Docking Setup
- Load the protein and ligands from the library in PyRx [7], select key residues for active/binding sites, and set up a grid box.

#### 4. Docking Process
- Assess the interactions within the receptor protein (6fyz) and the phytochemical library, including the docking parameters and settings outlined in Table 1. 
- PrankWeb [8] discovered more pockets that help to comprehend binding interactions. Details are included in the supplementary file, which improves the docking analysis.

| **Parameter**      | **Value**                                    |
|--------------------|----------------------------------------------|
| **Active site**     | 803                                          |
| **Binding sites**   | 667, 669, 675, 751                          |
| **Receptor**        | 6FYZ.pdbqt                                   |
| **Exhaustiveness**  | 8                                            |
| **Grid Box Center** | X: -22.8026, Y: 21.8574, Z: -8.2483          |
| **Grid Box Size**   | X: 52.8871, Y: 67.2849, Z: 25               |

**Table 1:** Docking parameters and active site information.

#### 5. Molecular docking

- Dock the phytochemical library with 6FYZ in PyRx (or AutoDock Vina), noting binding affinities and interactions.
#### 6. Results

- Compile all docking-generated tables and images.

### 3. Results

Includes visuals of protein active sites, grid selection, top two ligand-protein interactions, and other input/output files. A phytochemical library listing 50 compounds' structures and action mechanisms is also provided. All these resources are accessible via our GitHub repository for further review. 


| **Ligand**                          | **Binding Affinity (kcal/mol)** | **RMSD/ub** | **RMSD/lb** |
|-------------------------------------|---------------------------------|-------------|-------------|
| Zeaxanthin (6FYZ_5280899)           | -9.2                            | 0           | 0           |
| Zeaxanthin (6FYZ_5280899)           | -9.0                            | 1.596       | 0.595       |
| Leutin (6FYZ_5281243)               | -8.8                            | 0.502       | 0.217       |

**Table 2:**  Top three ligands, based on binding affinity.

### 4. Conclusion
Our docking analysis found Zeaxanthin and Leutin are the most significant phytochemicals with high binding affinities to 6fyz, particularly at active sites. Zeaxanthin showed the best potential (-9.2 kcal/mol) as an HDAC4 inhibitor in ovarian cancer.

### 5. References

1. Shen YF, Wei AM, Kou Q, Zhu QY, Zhang L. Histone deacetylase 4 increases progressive epithelial ovarian cancer cells via repression of p21 on fibrillar collagen matrices. *Oncol Rep*. 2016 Feb;35(2):948-54. doi: 10.3892/or.2015.4423. PMID: 26572940.
2. Ahn MY, Kang DO, Na YJ, et al. Histone deacetylase inhibitor, apicidin, inhibits human ovarian cancer cell migration via class II histone deacetylase 4 silencing. *Cancer Lett*. 2012 Dec 28;325(2):189-99. doi: 10.1016/j.canlet.2012.06.017. PMID: 22781396.
3. Kim S, Chen J, Cheng T, et al. PubChem 2023 update. *Nucleic Acids Research*, 2023 Jan;51(D1):D1373–D1380. doi: 10.1093/nar/gkac956.
4. Wang Y, Ren N, Rankin GO, Li B, et al. Anti-proliferative effect and cell cycle arrest induced by saponins extracted from tea (Camellia sinensis) flower in human ovarian cancer cells. *J Funct Foods*. 2017;37:310-321. doi: 10.1016/j.jff.2017.08.001.
5. H.M. Berman, J. Westbrook, Z. Feng, et al. The Protein Data Bank (2000) *Nucleic Acids Res*. 28(1):235-242. doi: 10.1093/nar/28.1.235.
6. Discovery Studio, version 24.1.0.23298, Accelrys, 2024.
7. Dallakyan S, Olson AJ. Small-Molecule Library Screening by Docking with PyRx. *Methods Mol Biol.* 2015;1263:243-50. doi: 10.1007/978-1-4939-2269-7_19.
8. Jendele L, Krivak R, Skoda P, Novotny M, Hoksza D. PrankWeb: a web server for ligand binding site prediction and visualization. *Nucleic Acids Res*. 2019 Jul 2;47(W1):W345-W349. doi: 10.1093/nar/gkz424.

---

## Phase 2

### Introduction

The report involves using  machine learning and cheminformatics libraries to analyze bioactivity data for the target "Histone Deacetylase 4" (HDAC4), a known therapeutic target for cancer and other diseases.

---
## Methods

### Imports from Libraries

- Utilized to obtain bioactivity information from the ChEMBL database is the chemical-web resource-client.
- Rdkit is used as a cheminformatics toolkit, specifically for the creation and management of molecular descriptors.
- mordred: A molecular descriptor generation tool.

---

### Target Search

The script looks for and retrieves the bioactivity data for "Histone Deacetylase 4" using chembl-webresource-client.


---

### Descriptor Calculation

The script looks for and retrieves the bioactivity data for "Histone Deacetylase 4" using chembl-webresource-client.


---

### Bioactivity Data Retrieval

The script retrieves bioactivity data after determining the target, most likely to build a dataset that connects molecular characteristics to bioactivity.

---

### Preprocessing and Model Development

The script contains code to prepare molecular data for machine learning models by preprocessing it using techniques like descriptor creation.

---

### Machine Learning Phases

Consists of a training and testing stage for creating models that use molecular descriptors to predict bioactivity.

---

## Results

### 1. Codes and Output of Preprocessing Steps

The preprocessing process involves searching for the target protein Histone Deacetylase 4 on the chembl database, filtering bioactivity data, and removing duplicate entries using SMILES. The data is then classified into three categories: Inactive (IC50 ≥ 10,000 nM), Active (IC50 ≤ 1,000 nM), and Intermediate (IC50 < 10,000 nM). A new column class is added to represent these categories. A code scripted calculates molecular descriptors based on Lipinski's rule of five to assess drug-likeness. We introduced code that sets up molecular descriptor calculations using RDKit.The data is then converted to pIC50 to ensure uniform distribution. The figure below describes the pIC50 column.

![pIC50 table](https://github.com/user-attachments/assets/2b5792f8-6dcd-45ab-925d-098085068854)

Exploratory Data Analysis via lipinski descriptors

![pfht1_plot_bioactivity_class](https://github.com/user-attachments/assets/b347b594-2813-41c0-91f8-90a34fedebb5)

![plot_MW_vs_LogP](https://github.com/user-attachments/assets/0e9f3c79-d2ee-4764-a8f3-3d0a55445936)

Functions were imported  from the RDKit library to handle SMILES strings and visualize molecular structures.The list of SMILES strings are standardized  into their canonical form, including the docked ligands Zeaxanthin and Lutein. Lipinski and Descriptor function were ran on the smiles of the docked ligands including the chembl molecules with 200 descriptors for each molecule. The pIC50 column was added to the ligand table, the cleaning process consisted of removing duplicated columns, removing NaN,removal of the ‘Ipc’ table to ensure no Infinity values are detected during modeling.

The information was then concatenated forming the “final_ligand_combine” table for the docked ligands and the “fp_pIC” table for the chembl molecules.

### 2. Training and Testing Phase

To perform modeling with Random Forest Regressor, we began with importing the necessary library.We define X as all other columns on the dataframe and Y as the pIC50 column. The data was split into training (80%) and testing (20%) sets prior to modeling and splitting.The Random Forest Regressor Model was fitted on the X and Y training set.”y_pred” variable was a result of model prediction on the X test set. 

Random Forest Regressor was also used to model the pIC50 of the docked ligands (Zeaxanthin and Lutein)generated from the SMILES on PubChem.The figure below gives better visualization of the pIC50 frequency distribution for the docked ligands,with the output:array([4.47204827, 5.68563597]

![Predicted value for Ligands](https://github.com/user-attachments/assets/a2e16eeb-9a36-427b-a492-6ea40c15797f)


After training, we evaluate the model using **MSE**, **MAE**, and **R-squared**. The output for the evaluation was as follows:
MSE: 1.434448392089781, MAE: 0.9173858303675583, R-squared: 0.2674666489747807

The evaluation on the ligand prediction was:MSE_Ligand: 0.3159101952201985, MAE_Ligand: 0.560117402174473, R-squared_Ligand: 0.7679999999999972

Also, cross-validation was performed on the data set  to assess generalization.Yielding the output:
Cross-validation scores: [-0.52565608 -0.15397229 -0.51313287 -3.09446009 -0.24337113]
Mean cross-validation score: -0.906118493479025

## Importance of features and bioactivity influence 

LogP and Molecular Weight were quite predictive, probably because they affect how well a chemical interacts with the target protein.For example, LogP value of 1,4296 indicates that the compound with chemical id :CHEMBL343448 is expected to show better bioactivity as they can balance between solubility and membrane permeability which is further validates by the bioactivity_class being active.

The model showed better prediction of the ligands than the chembl molecules, better model performance is indicated by a lower MSE and the MSE of the ligand was 0,315.The MAE value indicates better performance and a low value indicates a model's competence in prediction.The model has a better performance with modeling of the docked ligands.he R-squared represents how well the model's predictions fit the actual data, with a value of 0.768 indicating 76.8% of the variance in ligand-related predictions being explained by the model.While R-squared value of 0.267, the model is able to explain 26.7% of the variability in the data, indicating a pretty weak fit.

In regards to cross validation,a negative value nearer zero denotes a smaller prediction error because the mean square error is often positive.. A mean score of -0.906 in this instance indicates that the model is functioning reasonably, if not flawlessly, as it is not too far from zero.
We can note a variance between folds which indicates that the model may not generalize equally well across all subsets of our data, as evidenced by the variability between the folds, particularly the -3.09 score.

## Conclusion

The model's performance showed modest predictive power, with weak fit and challenges in generalization. Improvements are needed for better performance and generalization. Future steps may include refining feature selection, testing alternative algorithms, or increasing the training dataset's size and diversity. The model's predictive capacity is primarily related to LogP and Molecular Weight properties.

**Note:** All images related to this phase of the task are present in the supplementary file folder for Phase 2, Stage 3.

**References:**
1. Mendez D, Gaulton A, Bento AP, Chambers J, et al. ChEMBL: towards direct deposition of bioassay data. Nucleic Acids Res. 2019 Jan;47(D1):D930–D940. doi: 10.1093/nar/gky1075.
2. Landrum, G., et al. RDKit documentation. Available at: https://www.rdkit.org/docs/.


**Supplementaryfiles**:  
[Suplementary_files_phase1&phase2_both](https://github.com/samreenraza61/HackBio-Internship/tree/main/Supplementary_files_stage3)
 





