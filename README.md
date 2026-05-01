![](UTA-DataScience-Logo.png)

# Predicting Lead Contamination in Water Using Quantified Physical and Chemical Characterizations

* This repository holds an attempt to apply a Neural Network Model to predict high or low levels of Lead contamination based on EPA threshold of lead contamination in drinking water on the Kaggle
* dataset: https://www.kaggle.com/datasets/khushikyad001/water-pollution-and-disease 

## Overview

The task is to use 19 features to predict if the water would have a higher contamination of lead, greater than or equal to 15.0 ppm versus low contamination of lead, lower than 15.0 ppm. The approach in this repository formulates the problem as a classification task, using deep sequential neural networks as the model with 19 numerical input features. We compared the performance of 4 different network architectures, and 5 different learning rates. Our best model was able to correctly classify high versus low lead contaminated water 77.3% of the time. The overall accuracy of this classifier, after running 5 repeats of 5 randomized batches (kf split) is 74.8%.

## Summary of Workdone

### Data

* Data: https://www.kaggle.com/datasets/khushikyad001/water-pollution-and-disease 
  * Type: numeric and categorical
    * Input: CSV file of features (19 numerical features, 5 categorical features)
    * output: 1 feature selected from CSV file of features that would be a good indicator of good versus poor water quality
  * Size:
    * Number of Rows: 2,000
    * Number of Columns: 24
  * Instances (Train, Test, Validation Split): Train/Test/Validation split used was 70/10/20 1400 water samples for training, 200 samples for testing, and 400 samples for validation

#### Preprocessing / Clean up

* NaN values for water treatment type were equivalent to no treatment to water were conducted, thus we needed to impute these NaN values in this feature (column) to none

#### Data Visualization

<img width="823" height="799" alt="image" src="https://github.com/user-attachments/assets/a0fff5bb-4a6c-4c7d-aba4-9e1c09829401" />
* Comparing features with each other with the two populations of high and low concentrations of lead in the water samples revealed that none of the features would directly indicate differences in distribution of data within these populations. This is why we went with a neural network model.

<img width="442" height="393" alt="image" src="https://github.com/user-attachments/assets/833886c1-2a53-4066-8f99-b5aed8fb17b1" />
<img width="448" height="394" alt="image" src="https://github.com/user-attachments/assets/8b359f5a-b079-4e1f-880e-a45bae9a4933" />
* These correlation and covariance matrices also indicate that all of the features are nearly unique, meaning that one feature does not directly compare to another. All features are important.

### Problem Formulation

* Define: Can we predict high and low lead contamination levels in water given that no features clearly indicate similarities with other features? 
  * Input / Output
   * Input: Numerical features that were normalized using Sklearn's MinMaxScaler()
   * Output: 0 = low concentration and 1 = high concentration
  * Models
    * We tried a deep neural network model because all features were deemed important (more specifically none could be eliminated without losing some information) and there was no reason to select features because there were only 19 total variables (not too large as to slow down computation significantly)
  * Loss, Optimizer, other Hyperparameters
   * f1_score
   * network structure
   * learning rate
   * model.score --> accuracy to the ground truth

### Training

  * Training took around 20-30 minutes to complete
  * Based on previous literature and the robustness of my local machine, 5 repeats of the model were deemed appropriate to get decent performance

### Performance Comparison

* Key performance metrics: f1_score, model.score()
* f1_score indicated ... accuracy of the model
* model.score() is an internal method in the defined model that compares predicted value with ground truth value, this indicated that ... of the data were correctly classified

### Conclusions

* The best learning rate for this dataset is 0.05 and the best network structure was (64, 32). The network was not incredibly complicated to get a decent result of 74% accuracy. Based on the complexity of environmental contamination, it is incredibly difficult to quantify, thus machine learning techniques are optimal to investigate environmental problems that may lead to negative health outcomes.

### Future Work

* The next step that can be made would be to try a regression neural network model to predict more specific levels of contamination rather than a simple binary classification. Additionally, it would be interesting to investigate the features further, because 74% accuracy for environmental contamination models indicates strong potential that there are major physical or chemical charactersitics that can help predict severity of water contamination.

## How to reproduce results

* Packages used:
 * pandas
 * numpy
 * matplotlib (for visualization)
 * sklearn (for machine learning)
   * MinMaxScalar from sklearn
   * shuffle from sklearn
   * MLPClassifier from sklearn
   * KFold from sklearn
   * f1_score from sklearn
  
* Documentation for pandas: https://pandas.pydata.org/docs/ 
* Documentation for numpy: https://numpy.org/doc/
* Documentation for matplotlib: https://matplotlib.org/stable/index.html
* Documentation for sklearn: https://scikit-learn.org/stable/

### Overview of files in repository

* Dataset csv file: water_pollution_disease.csv
* Jupyter notebook with steps: Kaggle Tabular Data.ipynb


### Data

* Where to download the data: https://www.kaggle.com/datasets/khushikyad001/water-pollution-and-disease 


## Citations

* All relevant information is contained in the Kaggle Dataset: https://www.kaggle.com/datasets/khushikyad001/water-pollution-and-disease
* Information on how to develop a neural network model: https://scikit-learn.org/stable/modules/neural_networks_supervised.html#multi-layer-perceptron
* EPA guidelines: https://www.epa.gov/lead/lead-policy-and-guidance







