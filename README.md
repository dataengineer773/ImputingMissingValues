We have missing values in your data and want to impute them via some generic method or prediction, You can impute missing values using k-means nearest neighbors (KNN) or scikit-learn’s Simple
Imputer class. If you have a small amount of data, predict and impute the missing values using k-nearest
neighbors (KNN), Alternatively, we can use scikit-learn’s SimpleImputer class from the imputer module to fill in
missing values with the feature’s mean, median, or most frequent value. However, we will typically get
worse results than KNN, There are two main strategies for replacing missing data with substitute values, each of which has
strengths and weaknesses. First, we can use machine learning to predict the values of the missing data.
To do this we treat the feature with missing values as a target vector and use the remaining subset of
features to predict missing values. While we can use a wide range of machine learning algorithms to
impute values, a popular choice is KNN. KNN is addressed in depth later in [Link to Come], but the
short explanation is that the algorithm uses the k nearest observations (according to some distance
metric) to predict the missing value. In our solution we predicted the missing value using the five
closest observations.
The downside to KNN is that in order to know which observations are the closest to the missing value,
it needs to calculate the distance between the missing value and every single observation. This is
reasonable in smaller datasets, but quickly becomes problematic if a dataset has millions of
observations. In such cases, approximate nearest-neighbors (ANN) is a more feasible approach. We will
discuss ANN later in the book.
An alternative and more scalable strategy than KNN is to fill in the missing values of numerical data
with the mean, median or mode. For example, in our solution we used scikit-learn to fill in missing
values with a feature’s mean value. The imputed value is often not as close to the true value as when we
used KNN, but we can scale mean-filling to data containing millions of observations more easily.
If we use imputation, it is a good idea to create a binary feature indicating whether or not the
observation contains an imputed value
