You cant know everything, its ok if you dont have previous experience. Do the labs, review the interesting things you can pick-up from the course, the time for completion is mostly a lie, it takes less than half of the time. Do the challenge labs, read the statement before starting them.
For the Voucher to take the exam, complete: Build and Deploy ML solutions on VertexAI.
Books: Official GCP ML engineer guide by Wiley, Low Code AI: A practical project-driven Intro to ML. 
The cheatsheet is in the glossary in the ML developers site, read it its really useful.
Do the ML Crash Course its free.
Good Data Analysis, the Google guys went through all of these courses.

What is Logistic Regression?

Regression helps with numbers, clustering puts in groups, but what is a Classification problem?

Not much linear algebra, or calculus in the exam. But for understanding the fundamental ideas or proofs they back up using them, but most knowledge is covered with Discrete Maths. It is intimidating to think of the Math concepts when learning ML.

Read the Rules of ML in developers webiste, being a good software engineer is key for ML. ML Systems require data, lots of it.
historical data + objective goes into ML system = Policy
Most of the code is in gathering the data
Stochastic method for thinking.

To build a ML model, 1-Identify problem 2- Develop hypothesis 3- Acquire + explore data 4- Build a model 5- Train the model 6- Apply and scale

Document Assumptions, Decision trade-offs, the model has a complete different lifecycle, apart from the application lifecycle and the system lifecycle

What is Semantic Versioning?

The Reality with Working with ML is that most of the time is spent on: Defining KPIs, gathering data, system integration and infrastructure. Building models and optimizing actually is the minority of the time spent on. But mainly is about collecting data, quality data.
The ultimate goal is did the tool built have an impact.

What is Feature Engineering?

DeepEval for LLM evaluation

ML Algorithms: Classification types 
-outputs percentages
-Binary: is or isnt , probability of each more realistically
-Multiclass: What type?
How many categories for a single example
-Multiclass single and multiple label

Regression: 
-Numeric predictions on any type of input data, gives you an amount non- probability
-Unidimensional regression: total views, price, number of items, etc
-Multidimensional regression: Longitude and latitude

Computer Vision tasks:
-Image classification
-Object detection
-Image Segmentation

NLP: Question answering, Entity recognition, image2text, textClassification.
Basically convert non-structured to structured

ML Models business use cases
-Supervised Learning: Task driven and identifies a goal .Past data to predict future trends, classification and regression.
-Unsupervised Data-driven and identifies a pattern: Clustering, Association, 

Example for supervised tagging new baby geese, looking at datapoints labeling the type of goose, establish a trend for example more adults more babies, this would be a linear regression ideal example.
Unsupervised we look to find useful patterns in unclassified data

The right algorithm depends on wether your data is labeled and the output you'd like

Linear Regression
In linear regression an error is a deviation of the line of best fit. Used with continous values
Trains quickly, its all based on linear algebra, comes from the y = mx + b, m is w , b is the bias
every input variable is a feature, a feature that describes the condition, but wait how does the model calculate the w and the bias? w *x = feature, but why does the weights differ in value?

Logistic Regression
Used with categorical values, interpretable baseline model, its either class A or not, like a true false type of thing, non linear function
Linear model under sigmoid
In logistic regression we classify results under the Confussion Matrix not based on how far from the curve it fell.

What is Support Vector Machines?

Classification with K-Nearest Neighbots(KNN)
K  the number of cluster is a hyperparameter. Mechanism to know which K is closest to

Decision Trees
Method to divide data, is this relevant or is this not? Based on that we branch our tress to fall into a conclusion. Loans at banks use decision trees. Explainability of decision trees is extremely high.

Random forest is a collection of multiple decision trees, allow us to evaluate parallel. You lose explainability, but gain accuarcy.

Neural networks, more data more complex. Matrix Multiplication, with the w randomized multiplied with the input layer and output layer

Neural Networks: Multilayer perceptron, why does it multiply the weights then sum and then place into a sigmoid function? 

 Inputs, Features, Weights and Output do they constitute parameters?

Neural Networks solve non-linear problems.



