# Neural-Network-for-Nuclear-Binding-Energy-Prediction-
This project is a neural network trained to predict the nuclear binding energy of every element on the periodic table. The results of this neural network will be compared with the results of the Semi-Empirical Mass Formula as a bench mark for accuracy. 


## Methodology
This project uses the following Python scripts (file type ommited):
1. _Data_Processor_
2. _Semi-Empirical_Mass_Formula_
3. _Nuclear_Binding_Energy_NeuralNet_

_Data_Processor_ is the data processor custom built to process the data from both AME 2016 and AME 2020. _Semi-Empirical_Mass_Formula_ is the script encoding the Semi-Empirical Mass Formula.  Binding energy calculations for data from both AME 2016 and AME 2020 are included in this script. _Nuclear_Binding_Energy_NeuralNet_ is the neural network itself. It is trained on the AME 2020 data set.

## References
This project uses data sets from: 
- Huang W.J., et al. "The AME 2016 atomic mass evaluation (I). Evaluation of input data; and adjustment procedures." *Chinese Physics C*, vol. 41, no. 3, 2017, article 030002. 
- Huang W.J., et al. “The AME 2020 Atomic Mass Evaluation (I). Evaluation of Input Data, and Adjustment Procedures.” *Chinese Physics C*, vol. 45, no. 3, 2021, article 030002.


