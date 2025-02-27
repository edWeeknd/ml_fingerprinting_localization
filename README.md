# Machine learning fingerprinting localization

This is the repository for the machine-learning-based fingerprinting localization project.
In the project, 3 machine learning algorithms were used as matching algorithms for the fingerprinting dataset. The results are shown below.

## Results

| XGBoost           |             |             |             |  | Random Forest | n_estimators=10, | random_state=10 |  | SVM         |             |             |
|-------------------|-------------|-------------|-------------|--|---------------|------------------|-----------------|--|-------------|-------------|-------------|
| Technology        | 5G NSA      | Cat-M       | NB-IoT      |  | 5G NSA        | Cat-M            | NB-IoT          |  | 5G NSA      | Cat-M       | NB-IoT      |
| Average error [m] | 401.03993   | 826.48999   | 570.22508   |  | 57.08174      | 131.92023        | 133.50993       |  | 293.24933   | 277.46583   | 280.95731   |
| Max error [m]     | 4131.679124 | 7058.248764 | 2886.519097 |  | 3122.097525   | 7893.39568       | 2666.914154     |  | 5795.870015 | 6403.985885 | 3807.681173 |
| Min error [m]     | 2.390409724 | 11.25814159 | 17.34044608 |  | 0             | 0                | 0               |  | 0.134258786 | 3.552153589 | 2.941462624 |
| R^2 score         | 96.90%      | 90.70%      | 95.76%      |  | 99.74%        | 99.23%           | 99.38%          |  | 97.78%      | 97.91%      | 98.46%      |
| MSE               | 2.34E-05    | 7.15E-05    | 3.02E-05    |  | 1.89E-06      | 5.24E-06         | 3.95E-06        |  | 1.85E-05    | 1.76E-05    | 1.03E-05    |
| RMSE              | 0.004567539 | 0.007960617 | 0.005248164 |  | 0.001303205   | 0.002203977      | 0.001934819     |  | 0.003982097 | 0.003875206 | 0.003113045 |
|       |             |             |             |  |               |        Cross check           |                 |  |             |             |             |
| Average error [m] | 552.11701   | 947.91549   | 584.36394   |  | 230.9503      | 381.6071         | 133.50993       |  | 991.41841   | 1221.72296  | 1094.58948  |
| Max error [m]     | 3468.489059 | 12211.05018 | 3032.756208 |  | 7092.641901   | 6596.359272      | 2666.914154     |  | 5544.686106 | 4806.752374 | 4807.132142 |
| Min error [m]     | 7.173742306 | 19.79896067 | 30.90840208 |  | 0.636845339   | 1.554157809      | 0               |  | 11.23530273 | 18.66124681 | 19.20886202 |
| R^2 score         | 90.72%      | 73.95%      | 91.70%      |  | 95.01%        | 88.84%           | 93.71%          |  | 74.51%      | 66.45%      | 73.32%      |
| MSE               | 3.79E-05    | 0.00010481  | 3.40E-05    |  | 2.05E-05      | 4.51E-05         | 2.65E-05        |  | 0.000106328 | 0.000135    | 0.000110048 |
| RMSE              | 0.006078826 | 0.010046011 | 0.005732563 |  | 0.004454816   | 0.006456062      | 0.004887234     |  | 0.00994489  | 0.011400124 | 0.010250576 |


## Summary
From the acquired results, Random Forest gives the best performance for all three technologies, and that is in both self validation and cross check. XGBoost performs solidly, but has slightly worse results than Random Forest. SVM performs well for the self validation data, but doesn't do so well in the cross check.

**Note:** The fully connected NN was also implemented with various network architectures and hyperparameter, namely: Number of layer, number of nodes in a layer, activation functions, and number of epochs (see result.xlsx/Fully connected NN). However, the NN performed very poorly and the results it produced proved to be unusable (negative R^2 score). The reason could be the large number of features in the dataset, and the fact that most of the features have the same "0.0" value for most of the time. This makes the neurons in the NN unable to learn from the data effectively.
