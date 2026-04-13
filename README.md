# Neural-Network-for-Nuclear-Binding-Energy-Prediction

## Set Up:
Set up will assume the following:
- Google Colab is being used
- Google Drive for storing files

(ReadMe In Progress)

## Methodology


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

## File Structure
### Data Sets
The _AME 2016_ and _AME 2020_ data sets used in this project are stored in this folder.

### Python Scripts:
**Data_Processor**  
The custom, data pre-processing script built for this project. It was designed based on the structure of _AME 2016_ and _AME 2020_.

**Semi-Empirical_Mass_Formula**  
The script encoding the two Semi-Empirical Mass Formulas used by Benzaid D., et al. (2020) and Gjorgievska S., et al. (2024) respectively. Binding energy calculations for data from both _AME 2016_ and _AME 2020_ are included in this script.

**Nuclear_Binding_Energy_NeuralNet**  
The neural network itself, trained and tested using the _AME 2020_ data set.

### Other
**Drafts**  
This folder is used to store old files that were renamed in the process of completing this project and were subsequently treated as separate files by GitHub
- _Nuclear_Binding_Energy_ResNet_ is the old name for _Nuclear_Binding_Energy_NeuralNet_

## References
- Huang W.J., et al. "The AME 2016 atomic mass evaluation (I). Evaluation of input data; and adjustment procedures" *Chinese Physics C*, vol. 41, no. 3, 2017, article 030002.
- Benzaid D., et al. "Bethe–Weizsäcker semi-empirical mass formula coefficients: 2019 update based on AME2016" *Nuclear Science and Techniques*, vol. 31, 2020, article 9. https://doi.org/10.1007/s41365-019-0718-8
- Huang W.J., et al. “The AME 2020 Atomic Mass Evaluation (I). Evaluation of Input Data, and Adjustment Procedures” *Chinese Physics C*, vol. 45, no. 3, 2021, article 030002.
- Gjorgievska S., et al. "Revision of the semi-empirical mass formula coefficients using the AME2020 database" *Nuclear Engineering and Design*, vol. 426, 2024, article 113403. https://doi.org/10.1016/j.nucengdes.2024.113403
