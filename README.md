# Neural-Network-for-Nuclear-Binding-Energy-Prediction

## Set Up:
The Set Up will involve Google Colab as PyTorch is preinstalled and every line of code was written under this assumption. Google Drive is used to store the files as well.

**Step 0: (Only if you do not have a Google Colab Account)**  
Search Google Colab on your browser and click on the corresponding link. Sign up with any account you have available that Google accepts.

**Step 1:**  
Download _AME_Dataset(2016).txt_, _AME_Dataset(2020).txt_, _Data_Processor_, _Nuclear_Binding_Energy_NeuralNet_, and _Semi_Empirical_Mass_Formula_ from this repository and save them into the same Google Drive folder.

**Step 2:**  
Open _Data_Processor_ and change file paths for _AME_Dataset(2016).txt_ and _AME_Dataset(2020).txt_ to the current file path (unless your file path is the same). At the bottom of _Data_Processor_ is code to save the processed data into CSV files, change the file path to where you want to store the CSV files.

**Step 3:**  
Open _Semi_Empirical_Mass_Formula_ and change the file path in both read_csv() functions to the current respective paths of your CSV files. Open _Nuclear_Binding_Energy_NeuralNet_ and do the same (there's only one read_csv() function in this file)

(ReadMe in progress)

## Background
Measuring the binding energy of elements and their isotopes is a core mission of Nuclear Physics. However, the experimental determination of binding energy is a costly process: involving expensive measurement equipment and particle accelerators. Additionally, as the number of nucleons increase in the nucleus, binding energy becomes much harder to determine due to a variety of factors including, but not limited to, short half-lives or highly stable nuclei. Hence, measuring binding energy for heavier elements and finding new elements all together are likely equally if not more expensive.
Neural Networks can help predict the binding energy of existing and unknown isotopes without costly trial and error experiments. A similar approach was already demonstrated in 2022, with the creation of AlphaFold by Google Deepmind to predict the structure of proteins. Whereas 150,000 protein structures were determined through pure experimentation, AlphaFold predicted over 200 million protein structures in a matter of months. This project aims to explore a similar application of neural networks for predicting Nuclear Binding Energy.


## Methodology

### The Neural Network
The neural network found in _Nuclear_Binding_Energy_NeuralNet_ is a simple, two hidden layer, standard neural network. The only benchmark for quality of this neural network is the size of the loss function at the end of training.

To test the accuracy of this neural network, we will compare its predictions to the Semi-Empirical Mass Formula. The formula encodes the Liquid Drop Model of a nucleus, one of the first models of the atom's nucleus. First developed in 1935 by german physicist Carl Frederich von Weizsäcker, the formula's coefficients have been updated multiple times since the formula was first created as new experimental data was collected. We will use coefficients derived in 2020 and 2024 from the _AME 2016_ and _AME 2020_ data sets respectively. Additionally, the formula has multiple versions, two of which are displayed below.

### Semi Empirical Mass Formulas (SEMFs)

$\ B(A,Z) = a_v A - a_s A^{2/3} - a_c \frac{Z^2}{A^{1/3}} - a_\text{sym} \frac{(A-2Z)^2}{A} + \delta \, a_p \frac{1}{A^{1/2}}\$  (1)

Source: Benzaid D., et al. (2020)

$\ B(A,Z) = a_v A - a_s A^{2/3} - a_c \frac{Z(Z-1)}{A^{1/3}} - a_\text{sym} \frac{(A-2Z)^2}{A} + \delta \, a_p \frac{1}{\sqrt{A}}\$  (2)

Source: Gjorgievska S., et al. (2024)

**Notes**
- N = Number of Neutrons
- Z = Atomic Number/Number of Protons
- A = Mass Number
- $\delta$ = ±1 depending on nucleon parity

### Modeling Assumptions
- All coefficients provided by both Benzaid D., et al. (2020) and Gjorgievska S., et al. (2024) are calculated using nuclei with A $\geq$ 50. The original authors of both papers found that doing so allowed their respective SEMFs to best fit experimental data at time of publishing.
- Each paper used slightly different SEMFs, therefore both are encoded in _Semi-Empirical Mass Formula_ to ensure accurate reproductions of binding energy predictions from both papers.
- Gjorgievska S., et al. (2024) explicitly listed how the sign of the parity term was determined, namely $\delta$ is either 1, -1, or 0 based on the value of N and Z. This concept is invariant across all variations of the SEMF, therefore the same is assumed for Benzaid D., et al. (2020) even though it does not explicitly state this.
- Percent Errors in Prediction larger than 2% are omitted from final graphs. This is purely for presentation, as percent errors larger than 2% skew the graphs such that any errors smaller than 2% are effectively indistinguishable from one another.


## References
- Huang W.J., et al. "The AME 2016 atomic mass evaluation (I). Evaluation of input data; and adjustment procedures" *Chinese Physics C*, vol. 41, no. 3, 2017, article 030002.
- Benzaid D., et al. "Bethe–Weizsäcker semi-empirical mass formula coefficients: 2019 update based on AME2016" *Nuclear Science and Techniques*, vol. 31, 2020, article 9. https://doi.org/10.1007/s41365-019-0718-8
- Huang W.J., et al. “The AME 2020 Atomic Mass Evaluation (I). Evaluation of Input Data, and Adjustment Procedures” *Chinese Physics C*, vol. 45, no. 3, 2021, article 030002.
- Gjorgievska S., et al. "Revision of the semi-empirical mass formula coefficients using the AME2020 database" *Nuclear Engineering and Design*, vol. 426, 2024, article 113403. https://doi.org/10.1016/j.nucengdes.2024.113403
