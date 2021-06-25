# KNN-of-CKD

## Author Information

Author: Zacks Shen
Github: https://github.com/ZacksAmber/KNN-of-CKD
Blog: https://zacks.one
LinkedIn: https://www.linkedin.com/in/zacks-shen/

---

## Introduction

### Chronic Kidney Disease

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

---

## Visualizations

### 2D Static Scatter

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625021417.svg)

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625021526.svg)

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

For `k=1`, `KNN` will find 1 nearest train point from the test point. Then assign the same `Class` as the 1 nearest train point to the test point.

For `k>1`, `KNN` will find `k` nearest train points from the test point. Then assign the most frequent `Class` of the `k` nearest points to the test point.

For higher resolution, please run [KNN-of-CKD.ipynb](https://github.com/ZacksAmber/KNN-of-CKD/blob/main/KNN-of-CKD.ipynb) on your local machine. 

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625105743.gif)

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625110058.gif)

---

### 2D Static Scatter with [Decision Boundary](https://en.wikipedia.org/wiki/Decision_boundary)

What if all of the points on the plot are available for predicting?

Assume we have unlimited data from patients and the data have huge variations. The Decision Boundary can simulate this scenario.

![](https://raw.githubusercontent.com/ZacksAmber/PicGo/master/img/20210625025702.svg)

---

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
      <td>0.909362</td>
      <td>-0.314236</td>
      <td>-0.152696</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.239236</td>
      <td>-0.221549</td>
      <td>-0.345191</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.735332</td>
      <td>-0.484162</td>
      <td>-0.601850</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.865744</td>
      <td>-0.221549</td>
      <td>-0.569768</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-0.970162</td>
      <td>1.276890</td>
      <td>-0.345191</td>
      <td>1.0</td>
      <td>1.0</td>
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
      <td>0.004406</td>
      <td>0.025616</td>
      <td>0.232293</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>75</th>
      <td>0.387272</td>
      <td>0.118303</td>
      <td>-0.922675</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>76</th>
      <td>-2.014342</td>
      <td>0.489051</td>
      <td>-0.313108</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>77</th>
      <td>1.153004</td>
      <td>-0.298788</td>
      <td>-0.409356</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>78</th>
      <td>-2.814879</td>
      <td>0.396364</td>
      <td>0.809777</td>
      <td>1.0</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>

---

The 1st row of DataFrame `ckd`.

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
  </tbody>
</table>

---

The top k(k=5) nearest neighbors from the 1st row in `ckd`.

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
      <th>11</th>
      <td>-1.178998</td>
      <td>0.025616</td>
      <td>-0.730180</td>
      <td>1</td>
      <td>0.399022</td>
    </tr>
    <tr>
      <th>24</th>
      <td>-0.378460</td>
      <td>-0.144310</td>
      <td>-0.184779</td>
      <td>1</td>
      <td>0.493367</td>
    </tr>
    <tr>
      <th>30</th>
      <td>-1.318222</td>
      <td>-0.576849</td>
      <td>2.638477</td>
      <td>1</td>
      <td>0.575304</td>
    </tr>
    <tr>
      <th>86</th>
      <td>-0.169624</td>
      <td>-0.453267</td>
      <td>0.809777</td>
      <td>0</td>
      <td>0.733673</td>
    </tr>
    <tr>
      <th>59</th>
      <td>-0.169624</td>
      <td>0.025616</td>
      <td>-0.537686</td>
      <td>0</td>
      <td>0.738697</td>
    </tr>
  </tbody>
</table>

Therefore, the `Predicted Class` of row 0 in ckd is 1 because 3/5 nearest neighbors of row 0 are `Class = 1`. 

It's time to calculate the best k.

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

With `k=1` and the attributes of `Hemoglobin` and `Glucose`, We have 98.37% accuracy for predicting if a person has CKD by applying the `KNN` algorithm.

The CKD dataset has a clear separation in `Hemoglobin` and `Glucose`. Thus we only need these two attributes with `k=1` to make a accurate prediction. For more complicated datasets, we can use more than two attributes and let the `KNN` module find the best k for prediction.

