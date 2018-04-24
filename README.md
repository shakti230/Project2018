# Project2018
Programming and Scripting - Mary McDonagh

##Table of Contents
1.0 Problem statement	2
1.1 Project Plan	2
2.0 Research	3
2. References	7
3. Investigation	7
4. Calculations	7
4.1 Why use Python?	7
5. Summary of Investigation	8

##1.0 Problem statement
The following project concerns the well-known Fisher’s Iris data set [3]. The project
entails you researching the data set, and then writing documentation and code in the
Python programming language [1] based on that research.

##1.1 Project Plan

insert image

2.0 Research
Research background information about the data set and write a summary about
it.

According to Hoey the Iris Flower Dataset is a popular multivariate dataset that was introduced by R.A. Fisher as an example for discriminant analysis. This data set was introduced by the British statistician and biologist Ronald Fisher in his 1936 paper “The use of multiple measurements in taxonomic problems” as an example of linear discriminant analysis . It is sometimes called Anderson’s Iris data set because Edgar Anderson collected the data to quantify the morphologic variation of Iris flowers of three related species. The data set was originally published at UCI Machine Learning Repository: Iris Data Set, this small dataset from 1936 is often used for testing out machine learning algorithms and visualizations. Each row of the table represents an iris flower, including its species and dimensions of its botanical parts, sepal and petal, in centimeters. It is one of the first modern examples of statistical classification.

Sir Ronald Aylmer Fisher (17 February 1890 – 29 July 1962), who published as R. A. Fisher, was a British statistician and geneticist. For his work in statistics, he has been described as "a genius who almost single-handedly created the foundations for modern statistical science" and "the single most important figure in 20th century statistics". In genetics, his work used mathematics to combine Mendelian genetics and natural selection; this contributed to the revival of Darwinism in the early 20th century revision of the theory of evolution known as the modern synthesis. Fisher also did experimental agricultural research, which has saved millions from starvation. 

The iris data set refers to the length and width of sepal and petal for three northern american species of iris. The data on iris setosa canadensis and iris versicolor has been used by R. A. Fisher to illustrate linear discriminance analysis. The data on iris virginica have been added as an extension.




Figure 1: Iris setosa, Iris versicolor, Iris virginica

The iris dataset contains four measurements for 150 flowers representing three species of iris (Iris setosa, versicolor and virginica). 
We can inspect the data in python like this:

This data sets consists of 3 different types of irises' (Setosa, Versicolour, and Virginica) petal and sepal length, stored in a 150x4 numpy.ndarray

The rows being the samples and the columns being: Sepal Length, Sepal Width, Petal Length	and Petal Width. The below plot uses the first two features.




# Code source: Gaël Varoquaux
# Modified for documentation by Jaques Grobler
# License: BSD 3 clause

import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
from sklearn import datasets
from sklearn.decomposition import PCA

# import some data to play with
iris = datasets.load_iris()
X = iris.data[:, :2]  # we only take the first two features.
y = iris.target

x_min, x_max = X[:, 0].min() - .5, X[:, 0].max() + .5
y_min, y_max = X[:, 1].min() - .5, X[:, 1].max() + .5

plt.figure(2, figsize=(8, 6))
plt.clf()

# Plot the training points
plt.scatter(X[:, 0], X[:, 1], c=y, cmap=plt.cm.Set1,
            edgecolor='k')
plt.xlabel('Sepal length')
plt.ylabel('Sepal width')

plt.xlim(x_min, x_max)
plt.ylim(y_min, y_max)
plt.xticks(())
plt.yticks(())

# To getter a better understanding of interaction of the dimensions
# plot the first three PCA dimensions
fig = plt.figure(1, figsize=(8, 6))
ax = Axes3D(fig, elev=-150, azim=110)
X_reduced = PCA(n_components=3).fit_transform(iris.data)
ax.scatter(X_reduced[:, 0], X_reduced[:, 1], X_reduced[:, 2], c=y,
           cmap=plt.cm.Set1, edgecolor='k', s=40)
ax.set_title("First three PCA directions")
ax.set_xlabel("1st eigenvector")
ax.w_xaxis.set_ticklabels([])
ax.set_ylabel("2nd eigenvector")
ax.w_yaxis.set_ticklabels([])
ax.set_zlabel("3rd eigenvector")
ax.w_zaxis.set_ticklabels([])

plt.show()



The IRIS dataset refers to three classes of 50 instances each where each class refers to a type of IRIS plant. The first of the classes is linearly distinguished, with the second two not being linearly separable from each other. The 150 instances, which are equally separated between the three classes, contain the following four numeric attributes: 

1. sepal length – continuous 
2. sepal width - continuous 
3. petal length - continuous 
4. petal width – continuous 

and the fifth attribute is the predictive attributes which is the class attribute that means each instance also includes an identifying class name, each of which is one of the following: IRIS Setosa, IRIS Versicolour, or IRIS Virginica. The expectation from mining IRIS data set would be discovering patterns from examining petal and sepal size of the IRIS plant and how the prediction was made from analyzing the pattern to form the class of IRIS plant. By using this pattern and classification, the unknown data can be predicted more precisely in upcoming years. 

Question 2 - References

http://airccse.org/journal/ijsc/papers/2112ijsc07.pdf
https://www.idosi.org/wasj/wasj29(dmsct)14/5.pdf
http://www.ijrdet.com/files/Volume3Issue2/IJRDET_0814_13.pdf
http://www.cs.odu.edu/~ccartled/Teaching/2017-Fall/DataAnalysis/Presentations/030-iris-dataset.pdf
http://patrickhoey.com/downloads/Computer_Science/03_Patrick_Hoey_Data_Visualization_Dataset_paper.pdf
http://www.statlab.uni-heidelberg.de/data/iris/
https://en.wikipedia.org/wiki/Ronald_Fisher
https://www.packtpub.com/mapt/book/big_data_and_business_intelligence/9781782161400/2/ch02lvl1sec14/the-iris-dataset
https://www.idosi.org/wasj/wasj29(dmsct)14/5.pdf
http://www.ijrdet.com/files/Volume3Issue2/IJRDET_0814_13.pdf
https://pdfs.semanticscholar.org/b58f/395fd0afa3e309ff108247e03ab6c3f15719.pdf
http://sci2s.ugr.es/keel/pdf/algorithm/articulo/CORE.pdf



3. Investigation
Download the data set and write some Python code to investigate it.
Download iris data
Format iris data and print on screen
Analysis 1 - print out iris data on screen
Analysis 2 - compile stats using teh describe function
Analysis 3 - Using labelnames to translate the species names into integers
Analysis 4 - Import the `pandas` library to displate iris data
Analysis 5 - using the  describe function allows me to compile summary statistics
Analysis 6 - calculate the mean

4. Calculations
Summarise the data set by, for example, calculating the maximum, minimum and mean of each column of the data set. A Python script will quickly do this for you.
