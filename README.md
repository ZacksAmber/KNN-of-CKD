# KNN-of-CKD

This project is Machine Learning project for predicting [Chronic Kidney Disease (CKD)](https://www.cdc.gov/kidneydisease/basics.html) by using [K-Nearest Neighbors (KNN)](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm).

The method I defined is KNN, which accepts two arguments, such as `Hemoglobin` and `Glucose`, to predict CKD or visualize the predictions in scatter plot. KNN also supports showing the [Decision Boundary](https://en.wikipedia.org/wiki/Decision_boundary).

The sample chart is here:

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210618090811.svg)

---

Required packages:
- Pandas
- NumPy
- Plotly
- Scikit-Learn (for splitting  train and test)
- datascientists (for standardization)