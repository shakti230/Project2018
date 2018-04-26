# Project2018
Programming and Scripting - Mary McDonagh

## Table of Contents
## 1.0 Problem statement	
### 1.1 Project Plan	
## 2.0 Research	
## 3.0 References	
## 4.0 Investigation	
## 5.0 Calculations	
### 5.1 Why use Python?	
## 6.0 Summary of Investigation	






## 1.0 Problem statement
The following project concerns the well-known Fisher’s Iris data set [3]. The project
entails you researching the data set, and then writing documentation and code in the
Python programming language [1] based on that research.

## 1.1 Project Plan
![image](https://user-images.githubusercontent.com/36244887/39327184-348b3070-498f-11e8-8b6a-dfc27271ecf2.png)
*Figure 1*


## 2.0 Research
Research background information about the data set and write a summary about it.

According to Hoey the Iris Flower Dataset is a popular multivariate dataset that was introduced by R.A. Fisher as an example for discriminant analysis. This data set was introduced by the British statistician and biologist Ronald Fisher in his 1936 paper “The use of multiple measurements in taxonomic problems” as an example of linear discriminant analysis . It is sometimes called Anderson’s Iris data set because Edgar Anderson collected the data to quantify the morphologic variation of Iris flowers of three related species. The data set was originally published at UCI Machine Learning Repository: Iris Data Set, this small dataset from 1936 is often used for testing out machine learning algorithms and visualizations. Each row of the table represents an iris flower, including its species and dimensions of its botanical parts, sepal and petal, in centimeters. It is one of the first modern examples of statistical classification.

Sir Ronald Aylmer Fisher (17 February 1890 – 29 July 1962), who published as R. A. Fisher, was a British statistician and geneticist. For his work in statistics, he has been described as "a genius who almost single-handedly created the foundations for modern statistical science" and "the single most important figure in 20th century statistics". In genetics, his work used mathematics to combine Mendelian genetics and natural selection; this contributed to the revival of Darwinism in the early 20th century revision of the theory of evolution known as the modern synthesis. Fisher also did experimental agricultural research, which has saved millions from starvation. 

The iris data set refers to the length and width of sepal and petal for three northern american species of iris. The data on iris setosa canadensis and iris versicolor has been used by R. A. Fisher to illustrate linear discriminance analysis. The data on iris virginica have been added as an extension.

![
](https://user-images.githubusercontent.com/36244887/39327253-6c8846e8-498f-11e8-9498-6f4e8067d3db.png)

Figure 2: Iris setosa, Iris versicolor, Iris virginica

The iris dataset contains four measurements for 150 flowers representing three species of iris (Iris setosa, versicolor and virginica). 
We can inspect the data in python like this:

This data sets consists of 3 different types of irises' (Setosa, Versicolour, and Virginica) petal and sepal length, stored in a 150x4 numpy.ndarray

The rows being the samples and the columns being: Sepal Length, Sepal Width, Petal Length and Petal Width. The below plot uses the first two features.

![image](https://user-images.githubusercontent.com/36244887/39327332-a066064e-498f-11e8-8963-2ebc12a3df8e.png)

Figure 3

![image](https://user-images.githubusercontent.com/36244887/39330130-82c7a968-4998-11e8-8204-f21892267960.png)

Figure 4

#Code source: Gaël Varoquaux
#Modified for documentation by Jaques Grobler
#License: BSD 3 clause

import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
from sklearn import datasets
from sklearn.decomposition import PCA

#import some data to play with
iris = datasets.load_iris()
X = iris.data[:, :2]  # we only take the first two features.
y = iris.target

x_min, x_max = X[:, 0].min() - .5, X[:, 0].max() + .5
y_min, y_max = X[:, 1].min() - .5, X[:, 1].max() + .5

plt.figure(2, figsize=(8, 6))
plt.clf()

#Plot the training points
plt.scatter(X[:, 0], X[:, 1], c=y, cmap=plt.cm.Set1,
            edgecolor='k')
plt.xlabel('Sepal length')
plt.ylabel('Sepal width')

plt.xlim(x_min, x_max)
plt.ylim(y_min, y_max)
plt.xticks(())
plt.yticks(())

#To getter a better understanding of interaction of the dimensions
#plot the first three PCA dimensions
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

## 3. References

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
https://machinelearningmastery.com/machine-learning-in-python-step-by-step/
https://www.kaggle.com/



## 4. Investigation
Download the data set and write some Python code to investigate it.
Download iris data
import required libraries 
#### Analysis 1 - print out iris data on screen, display without headers and comma separated
![analysis 1](https://user-images.githubusercontent.com/36244887/39323956-13556514-4986-11e8-9a54-df584528423c.JPG)
Figure 5

Displays all rows 150 rows x 5 columns
![analysis 1 1](https://user-images.githubusercontent.com/36244887/39324063-63b1c106-4986-11e8-8eba-e45eb0d04651.JPG)
Figure 6

#### Analysis 2 - Assign column names to the data set using class - sepal-length', 'sepal-width', 'petal-length', 'petal-width'
![analysis 2](https://user-images.githubusercontent.com/36244887/39324464-7a7444a8-4987-11e8-86b5-f210aa0c22b7.JPG)
Figure 7

#### Analysis 3 - Find out the number of rows and columns in the dataset
![image](https://user-images.githubusercontent.com/36244887/39324632-e3bc87ea-4987-11e8-9a09-c81b1b42156a.png)
Figure 8

#### Analysis 4 - Using the  describe function allows me to compile summary statistics such as mean, count, min, max and percentages
![image](https://user-images.githubusercontent.com/36244887/39324990-f355326e-4988-11e8-8672-9c90613c4a0f.png)
Figure 9

#### Analysis 5 - Group data sets by class size
![image](https://user-images.githubusercontent.com/36244887/39325169-6acfa91e-4989-11e8-88ba-0dd0d08fedc8.png)
Figure 10

#### Analysis 6 - Use the describe function to describe each class individually
![image](https://user-images.githubusercontent.com/36244887/39325318-c91e885a-4989-11e8-9ea6-84d0085cff94.png)
Figure 11

![image](https://user-images.githubusercontent.com/36244887/39325470-2c9068ae-498a-11e8-8b22-7031610eb43f.png)
Figure 12

![image](https://user-images.githubusercontent.com/36244887/39325553-6e0a5970-498a-11e8-9cb2-1f167c3396b2.png)
Figure 13

#### Analysis 7 - Use a box plot graph to display the sepal and petal length and width
![image](https://user-images.githubusercontent.com/36244887/39325674-b71aa962-498a-11e8-9257-576e31c0b32f.png)
Figure 14

#### Analysis 8 - Using the seaborn library display a scatter graph to find the relationship between each class (sepal and petal)
![image](https://user-images.githubusercontent.com/36244887/39325898-4dc48716-498b-11e8-9335-aca29a1780ff.png)
Figure 15

![image](https://user-images.githubusercontent.com/36244887/39325979-91542428-498b-11e8-9682-60795b0c82f8.png)
Figure 16

#### Analysis 9 - Plot a matrix to display the correlation between the attributes
![image](https://user-images.githubusercontent.com/36244887/39326103-e5b8864e-498b-11e8-9136-fddd929b8f85.png)
Figure 17

#### Analysis 10 - Display scatter plot matrix to investigate the relationship and dependency
![image](https://user-images.githubusercontent.com/36244887/39326204-2658892e-498c-11e8-8548-ddc3eded8d62.png)
Figure 18

#### Analysis 11 -  Display data in histograms to show petal and sepal width and length 
![image](https://user-images.githubusercontent.com/36244887/39326352-9c1f5dc2-498c-11e8-9230-20c28afe2b6d.png)
Figure 19


## 5. Calculations
Summarise the data set by, for example, calculating the maximum, minimum and mean of each column of the data set. A Python script will quickly do this for you.

![image](https://user-images.githubusercontent.com/36244887/39326435-d817a3de-498c-11e8-9666-dcab21b8576b.png)
Figure 20

#### Analysis 4 above - use the describe function to calculate the mean.

## 6 Summary of Investigation
