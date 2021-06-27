# KNN-of-CKD

## Author Information

Author: Zacks Shen
Github: https://github.com/ZacksAmber/KNN-of-CKD
Blog: https://zacks.one
LinkedIn: https://www.linkedin.com/in/zacks-shen/

---

## Introduction

### Chronic Kidney Disease

> [One in Seven American Adults Estimated to Have Chronic Kidney Disease](https://www.kidney.org/news/one-seven-american-adults-estimated-to-have-chronic-kidney-disease)

This is a Machine Learning project for predicting [Chronic Kidney Disease (CKD)](https://www.cdc.gov/kidneydisease/basics.html) by using [K-Nearest Neighbors (KNN)](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm).

The project is about forecasting if a person has CKD based on two or three attributes from `Hemoglobin`, `Glucose`, and `White Blood Cell Count`. If the one has CKD the `Class` is `1`.

---

### Package Introduction

The module I developed is `KNN`, which is included in the package [datascientists](https://pypi.org/project/datascientists/). The minimum version of `datascientists` must greater than or equal to `0.0.5`.
`KNN` can predict the `Class` or any category marked as `1` and `0`. It accepts at least 2 attributes (the columns of your pandas DataFrame) and returns the following results: 
- Pandas DataFrame: The predicted class of test.
    - The validation method for the predictions.
- Plotly graph object: A static 2 dimensional scatter plot with train data or predictions or [Decision Boundary](https://en.wikipedia.org/wiki/Decision_boundary).
- Plotly graph object: A static 3 dimensional scatter plot with train data or predictions.
- Plotly graph object: An animated 2 dimensional scatter plot to present the process that how KNN algorithm finds the neareast neighbor. (`k=1`, or `k>1`).
- Pandas DataFrame: The best k, the mean of k calculated by default 100 times from random train-test datasets, based on the user-specified attributes.

---

## Dataset

[ckd.csv](https://github.com/ZacksAmber/Code/raw/master/Data%20Science/Data8/Data%20Sets/ckd.csv)

### Original Dataset

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th></th>
      <th>Age</th>
      <th>Blood Pressure</th>
      <th>Specific Gravity</th>
      <th>Albumin</th>
      <th>Sugar</th>
      <th>Red Blood Cells</th>
      <th>Pus Cell</th>
      <th>Pus Cell clumps</th>
      <th>Bacteria</th>
      <th>Blood Glucose Random</th>
      <th>...</th>
      <th>Packed Cell Volume</th>
      <th>White Blood Cell Count</th>
      <th>Red Blood Cell Count</th>
      <th>Hypertension</th>
      <th>Diabetes Mellitus</th>
      <th>Coronary Artery Disease</th>
      <th>Appetite</th>
      <th>Pedal Edema</th>
      <th>Anemia</th>
      <th>Class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>48</td>
      <td>70</td>
      <td>1.005</td>
      <td>4</td>
      <td>0</td>
      <td>normal</td>
      <td>abnormal</td>
      <td>present</td>
      <td>notpresent</td>
      <td>117</td>
      <td>...</td>
      <td>32</td>
      <td>6700</td>
      <td>3.9</td>
      <td>yes</td>
      <td>no</td>
      <td>no</td>
      <td>poor</td>
      <td>yes</td>
      <td>yes</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>53</td>
      <td>90</td>
      <td>1.020</td>
      <td>2</td>
      <td>0</td>
      <td>abnormal</td>
      <td>abnormal</td>
      <td>present</td>
      <td>notpresent</td>
      <td>70</td>
      <td>...</td>
      <td>29</td>
      <td>12100</td>
      <td>3.7</td>
      <td>yes</td>
      <td>yes</td>
      <td>no</td>
      <td>poor</td>
      <td>no</td>
      <td>yes</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>63</td>
      <td>70</td>
      <td>1.010</td>
      <td>3</td>
      <td>0</td>
      <td>abnormal</td>
      <td>abnormal</td>
      <td>present</td>
      <td>notpresent</td>
      <td>380</td>
      <td>...</td>
      <td>32</td>
      <td>4500</td>
      <td>3.8</td>
      <td>yes</td>
      <td>yes</td>
      <td>no</td>
      <td>poor</td>
      <td>yes</td>
      <td>no</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>68</td>
      <td>80</td>
      <td>1.010</td>
      <td>3</td>
      <td>2</td>
      <td>normal</td>
      <td>abnormal</td>
      <td>present</td>
      <td>present</td>
      <td>157</td>
      <td>...</td>
      <td>16</td>
      <td>11000</td>
      <td>2.6</td>
      <td>yes</td>
      <td>yes</td>
      <td>yes</td>
      <td>poor</td>
      <td>yes</td>
      <td>no</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>61</td>
      <td>80</td>
      <td>1.015</td>
      <td>2</td>
      <td>0</td>
      <td>abnormal</td>
      <td>abnormal</td>
      <td>notpresent</td>
      <td>notpresent</td>
      <td>173</td>
      <td>...</td>
      <td>24</td>
      <td>9200</td>
      <td>3.2</td>
      <td>yes</td>
      <td>yes</td>
      <td>yes</td>
      <td>poor</td>
      <td>yes</td>
      <td>yes</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>153</th>
      <td>55</td>
      <td>80</td>
      <td>1.020</td>
      <td>0</td>
      <td>0</td>
      <td>normal</td>
      <td>normal</td>
      <td>notpresent</td>
      <td>notpresent</td>
      <td>140</td>
      <td>...</td>
      <td>47</td>
      <td>6700</td>
      <td>4.9</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>good</td>
      <td>no</td>
      <td>no</td>
      <td>0</td>
    </tr>
    <tr>
      <th>154</th>
      <td>42</td>
      <td>70</td>
      <td>1.025</td>
      <td>0</td>
      <td>0</td>
      <td>normal</td>
      <td>normal</td>
      <td>notpresent</td>
      <td>notpresent</td>
      <td>75</td>
      <td>...</td>
      <td>54</td>
      <td>7800</td>
      <td>6.2</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>good</td>
      <td>no</td>
      <td>no</td>
      <td>0</td>
    </tr>
    <tr>
      <th>155</th>
      <td>12</td>
      <td>80</td>
      <td>1.020</td>
      <td>0</td>
      <td>0</td>
      <td>normal</td>
      <td>normal</td>
      <td>notpresent</td>
      <td>notpresent</td>
      <td>100</td>
      <td>...</td>
      <td>49</td>
      <td>6600</td>
      <td>5.4</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>good</td>
      <td>no</td>
      <td>no</td>
      <td>0</td>
    </tr>
    <tr>
      <th>156</th>
      <td>17</td>
      <td>60</td>
      <td>1.025</td>
      <td>0</td>
      <td>0</td>
      <td>normal</td>
      <td>normal</td>
      <td>notpresent</td>
      <td>notpresent</td>
      <td>114</td>
      <td>...</td>
      <td>51</td>
      <td>7200</td>
      <td>5.9</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>good</td>
      <td>no</td>
      <td>no</td>
      <td>0</td>
    </tr>
    <tr>
      <th>157</th>
      <td>58</td>
      <td>80</td>
      <td>1.025</td>
      <td>0</td>
      <td>0</td>
      <td>normal</td>
      <td>normal</td>
      <td>notpresent</td>
      <td>notpresent</td>
      <td>131</td>
      <td>...</td>
      <td>53</td>
      <td>6800</td>
      <td>6.1</td>
      <td>no</td>
      <td>no</td>
      <td>no</td>
      <td>good</td>
      <td>no</td>
      <td>no</td>
      <td>0</td>
    </tr>
  </tbody>
</table>

---

### Selected Columns and Standardized Dataset

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th></th>
      <th>Hemoglobin</th>
      <th>Glucose</th>
      <th>White Blood Cell Count</th>
      <th>Class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-0.865744</td>
      <td>-0.221549</td>
      <td>-0.569768</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-1.457446</td>
      <td>-0.947597</td>
      <td>1.162684</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-1.004968</td>
      <td>3.841231</td>
      <td>-1.275582</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-2.814879</td>
      <td>0.396364</td>
      <td>0.809777</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-2.083954</td>
      <td>0.643529</td>
      <td>0.232293</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>153</th>
      <td>0.700526</td>
      <td>0.133751</td>
      <td>-0.569768</td>
      <td>0</td>
    </tr>
    <tr>
      <th>154</th>
      <td>0.978974</td>
      <td>-0.870358</td>
      <td>-0.216861</td>
      <td>0</td>
    </tr>
    <tr>
      <th>155</th>
      <td>0.735332</td>
      <td>-0.484162</td>
      <td>-0.601850</td>
      <td>0</td>
    </tr>
    <tr>
      <th>156</th>
      <td>0.178436</td>
      <td>-0.267893</td>
      <td>-0.409356</td>
      <td>0</td>
    </tr>
    <tr>
      <th>157</th>
      <td>0.735332</td>
      <td>-0.005280</td>
      <td>-0.537686</td>
      <td>0</td>
    </tr>
  </tbody>
</table>

The last step of data preprocessing is randomly and evenly split dataset ckd into two DataFrames: train and test.

We will use the train to build the KNN model. Module KNN can forecast the class of the test based on the KNN model. Because we already know the class of test. We can compare the class and predicted class to evaluate the accuracy of the model.

---

## Visualizations

### 2D Static Scatter

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625171142.svg)

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625171248.svg)

`Hemoglobin` vs. `Glucose` has higher accuracy than `White Blood Cell Count` vs. `Glucose` for predicting `Class` of CKD.

Because the latter plot shows that the separation between the two attributes is not so clean. 

---

### 3D Static Scatter

Although we already know which two attributes have better accuracy, how about three of them?

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625024709.svg)

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625104628.svg)

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625104717.svg)

The 3D Scatter: KNN of CKD shows that the accuracy of three attributes seems not better than `Hemoglobin` vs. `Glucose`. Therefore, for resource-saving, we will focus on `Hemoglobin` vs. `Glucose`.

---

### 2D Animated Scatter

Let's see how module `KNN` works.

For `k=1`, `KNN` will find 1 nearest train point to the test point. Then assign the same `Class` as the 1 nearest train point to the test point.

For `k>1`, `KNN` will find `k` nearest train points to the test point. Then assign the most frequent `Class` of the `k` nearest points to the test point.

For higher resolution, please run [KNN-of-CKD.ipynb](https://github.com/ZacksAmber/KNN-of-CKD/blob/main/KNN-of-CKD.ipynb) on your local machine. 

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625105743.gif)

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625110058.gif)

---

### 2D Static Scatter with [Decision Boundary](https://en.wikipedia.org/wiki/Decision_boundary)

What if all of the points on the plot are available for predicting?
Assume we have unlimited data from patients and the data have huge variations. The Decision Boundary can simulate this scenario.
You can see the transparent dots and opaque dots on the scatter plot.
The boundary between them is Decision Boundary.
Any new point that more close to the side of blue will be classified as CKD; vice versa, Any new point that more close to the side of gold will be classified as healthy.

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625202811.svg)

---

## Predictions and Best k

Now we have the best attributes. And we know how `KNN` works.

But what `k` is proper to forecast the `Class`?

`KNN` has a method `best_k` to help the user make a decision.

Let's see the current `predictions`.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th></th>
      <th>Hemoglobin</th>
      <th>Glucose</th>
      <th>White Blood Cell Count</th>
      <th>Class</th>
      <th>Predicted Class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-0.030400</td>
      <td>-0.376028</td>
      <td>0.809777</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.213242</td>
      <td>-0.484162</td>
      <td>-0.569768</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-3.685029</td>
      <td>0.689873</td>
      <td>-0.986840</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.700526</td>
      <td>-0.406923</td>
      <td>0.617283</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.292227</td>
      <td>-0.175206</td>
      <td>-0.473521</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>74</th>
      <td>-1.283416</td>
      <td>-0.221549</td>
      <td>3.408455</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>75</th>
      <td>-2.223178</td>
      <td>1.910252</td>
      <td>0.424788</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>76</th>
      <td>0.282854</td>
      <td>-0.298788</td>
      <td>0.296458</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>77</th>
      <td>-2.083954</td>
      <td>0.643529</td>
      <td>0.232293</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>78</th>
      <td>-1.283416</td>
      <td>-0.947597</td>
      <td>3.344290</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>

We can also calculate the accuracy of the model.

For each row in DataFrame predictions, we can count the number of column Predicted Class that is the same as the column Class. Then let it divided by the length of the DataFrame test. The result is the accuracy under the current train test distribution.

The current `Accuracy` is `0.9746835443037974`.

---

So let's see how KNN makes a prediction for each row.

The 1st row of the DataFrame `test` is the 1st row in the DataFrame `predictions`. The `Class` is 0, and the `Predicted Class` is 0, too.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th></th>
      <th>Hemoglobin</th>
      <th>Glucose</th>
      <th>White Blood Cell Count</th>
      <th>Class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>119</th>
      <td>-0.0304</td>
      <td>-0.376028</td>
      <td>0.809777</td>
      <td>0</td>
    </tr>
  </tbody>
</table>

---

The top k(k=5) nearest neighbors to the 1st row in `test`.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th></th>
      <th>Hemoglobin</th>
      <th>Glucose</th>
      <th>White Blood Cell Count</th>
      <th>Class</th>
      <th>distance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>137</th>
      <td>0.039212</td>
      <td>-0.530506</td>
      <td>-0.666015</td>
      <td>0</td>
      <td>0.169438</td>
    </tr>
    <tr>
      <th>156</th>
      <td>0.178436</td>
      <td>-0.267893</td>
      <td>-0.409356</td>
      <td>0</td>
      <td>0.235171</td>
    </tr>
    <tr>
      <th>78</th>
      <td>-0.065206</td>
      <td>-0.623193</td>
      <td>0.039798</td>
      <td>0</td>
      <td>0.249604</td>
    </tr>
    <tr>
      <th>60</th>
      <td>0.074018</td>
      <td>-0.144310</td>
      <td>0.328540</td>
      <td>0</td>
      <td>0.254158</td>
    </tr>
    <tr>
      <th>120</th>
      <td>-0.239236</td>
      <td>-0.221549</td>
      <td>-1.051005</td>
      <td>0</td>
      <td>0.259761</td>
    </tr>
  </tbody>
</table>

We can call function `_distance` to get the top k nearest neighbors. All of the neighbors are 0, so the `Predicted Class` of this point is 0.

---

The `predict` function works well.

It's time to calculate the best k.

The `best_k` method concatenates `train` and `test` in the `KNN` instance. So `KNN` instance has a complete DataFrame `ckd`. Then it splits the `ckd` into `train` and `test` for 100 times. For each repetition, it stores the current `Accuracy` according to the current `k`. Finally, it returns the average `Accuracy` for each `k`.

For example, I passed `k = 5` to the `best_k` function. Then it returned the average accuracy of 100 repetitions for k from 1 to 5.

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th></th>
      <th>k</th>
      <th>Average Accuracy of 100 Boostrap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0.983671</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>0.982025</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>0.981139</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0.977975</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>0.977468</td>
    </tr>
  </tbody>
</table>

---

## Conclusion

With `k=1` and the attributes of `Hemoglobin` and `Glucose`, We have 98.56% accuracy for predicting if a person has CKD by applying the `KNN` algorithm.

The CKD dataset has a clear separation in `Hemoglobin` and `Glucose`. Thus we only need these two attributes with `k=1` to make an accurate prediction. For more complicated datasets, we can use more than two attributes and let the `KNN` module find the best k for prediction.
