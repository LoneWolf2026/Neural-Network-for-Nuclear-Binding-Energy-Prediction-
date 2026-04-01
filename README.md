# Neural-Network-for-Nuclear-Binding-Energy-Prediction-
This project is a neural network trained to predict the nuclear binding energy of every element on the periodic table. The results of this neural network will be compared with the results of the Semi-Empirical Mass Formula as a bench mark for accuracy. 


## Methodology
This project uses the following Python scripts (file type ommited):
1. _Data_Processor_
2. _Semi-Empirical_Mass_Formula_
3. _Nuclear_Binding_Energy_NeuralNet_

_Data_Processor_ is the data processor custom built to process the data from both AME 2016 and AME 2020. _Semi-Empirical_Mass_Formula_ is the script encoding the Semi-Empirical Mass Formula.  Binding energy calculations for data from both AME 2016 and AME 2020 are included in this script. _Nuclear_Binding_Energy_NeuralNet_ is the neural network itself. It is trained and tested on the AME 2020 data set.

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

## References
- Huang W.J., et al. "The AME 2016 atomic mass evaluation (I). Evaluation of input data; and adjustment procedures" *Chinese Physics C*, vol. 41, no. 3, 2017, article 030002.
- Benzaid D., et al. "Bethe–Weizsäcker semi-empirical mass formula coefficients: 2019 update based on AME2016" *Nuclear Science and Techniques*, vol. 31, 2020, article 9. https://doi.org/10.1007/s41365-019-0718-8
- Huang W.J., et al. “The AME 2020 Atomic Mass Evaluation (I). Evaluation of Input Data, and Adjustment Procedures” *Chinese Physics C*, vol. 45, no. 3, 2021, article 030002.
- Gjorgievska S., et al. "Revision of the semi-empirical mass formula coefficients using the AME2020 database" *Nuclear Engineering and Design*, vol. 426, 2024, article 113403. https://doi.org/10.1016/j.nucengdes.2024.113403
