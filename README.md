# KNN-of-CKD

This is a Machine Learning project for predicting [Chronic Kidney Disease (CKD)](https://www.cdc.gov/kidneydisease/basics.html) by using [K-Nearest Neighbors (KNN)](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm).

The method I defined is `KNN`, which accepts multiple attributes, such as `Hemoglobin` and `Glucose`, to predict or visualize CKD in scatter plot. `KNN` also supports showing the [Decision Boundary](https://en.wikipedia.org/wiki/Decision_boundary). 
- For visualization, it can only present 2 or 3 attributes.
- For prediction, there is no restriction.

The sample visualization is here:

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210618090811.svg)

The sample predictions is here:

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th></th>
      <th>Hemoglobin</th>
      <th>Glucose</th>
      <th>predicted Class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-2.715890</td>
      <td>0.836556</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.127458</td>
      <td>-0.995676</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.656825</td>
      <td>3.048459</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-2.620390</td>
      <td>0.387159</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-1.270467</td>
      <td>4.441628</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>995</th>
      <td>-0.616869</td>
      <td>3.181657</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>996</th>
      <td>2.316167</td>
      <td>0.706823</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>997</th>
      <td>-2.669035</td>
      <td>3.128607</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>998</th>
      <td>2.396666</td>
      <td>2.410810</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>999</th>
      <td>-3.330692</td>
      <td>0.146513</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>

---

Required packages:
- Pandas
- NumPy
- Plotly
- Scikit-Learn (for splitting  train and test)
- datascientists (for standardization)

---

## More examples

### 2 Dimensional KNN

#### KNN of test

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210619232645.svg)

---

#### KNN of prediction (1000 random samples)

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210619233051.svg)

---

### 3 Dimensional KNN

#### KNN of test

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210619233214.svg)

---

#### KNN of prediction (1000 random samples)

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210619233309.svg)