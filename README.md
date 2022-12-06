# ESILV_PythonforDataAnalysis_Project2023
Here is the report of project of HIEN Victor, LUTTENBACHER Léa and MENU Victor (DIA1)

It contains: 
- A README file, summarizing the content of the project and our approach  
- A Jupyter file (ipynb), to see our code, our results and our research  
- A PowerPoint/PDF file, containing our presentation
- An API file, to implement the API we chose  

Enjoy the reading and feel free to contact us if you have any question/issue ! :)

## 0) The Database

- Estimation of obesity levels based on eating habits and physical condition Data Set  
- Link to the Data set : https://archive.ics.uci.edu/ml/datasets/Estimation+of+obesity+levels+based+on+eating+habits+and+physical+condition+  
- Information : This dataset include data for the estimation of obesity levels in individuals from the countries of Mexico, Peru and Colombia, based on their eating habits and physical condition. 77% of the data was generated synthetically using the Weka tool and the SMOTE filter, 23% of the data was collected directly from users through a web platform.  
- Link to the study : https://www.sciencedirect.com/science/article/pii/S2352340919306985?via%3Dihub  

## 1) Exploration of the data set and data
- In this first part, our objective will be to explore the data set, to understand its data as well as its variables, and the link between each of them. This step is necessary to be able to carry out an effective data preparation: the data pre-processing.  
- Through exploration, we answer questions like:
  - How many data and variables make up our data set ?
  - Are they missing values ?  
There isn't missing values, it can be explained simply: Indeed, 77% of the data was generated synthetically using the Weka tool and the SMOTE filter, and the other 23% of the data was collected directly from users through a web platform.    
  - What are the variables and what do they correspond to?    
Here we can observe the 17 variables present in our dataset. We will now explain the correspondence of each of these variables, according to their type (quantitative or qualitative). We can see that in the quantitative variables, some have already been encoded according to the answers to the questionnaire which can be seen here: https://www.sciencedirect.com/science/article/pii/S2352340919306985?via%3Dihub We will therefore use this for the rest and for our understanding of the data set. 
 
- Our 8 quantitative variables (float64 type):  
  - Age: The person's age in years  
  - Height: The height of the person in meters  
  - Weight: The person's weight in kilograms  
  - FCVC: Frequency of consumption of vegetables by scale  
  - NCP: Number of main meals daily  
  - CH2O: Consumption of water daily  
  - FAF: Physical activity frequency weekly  
  - TUE: Time using technology devices daily    
 
- Our 9 qualitative variables (type object):  
  - Gender: The gender of the person  
  - Family_history_with_overweight: Whether or not there is a family history of obesity  
  - FAVC: Frequent consumption of high caloric food  
  - CAEC: Consumption of food between meals  
  - SMOKE: Is the person a smoker or not  
  - SCC: Calories consumption monitoring daily  
  - CALC: Consumption of alcohol  
  - MTRANS: Transportation used  
  - NObeyesdad: Obesity category  
  
- Finally, to get a general overview of our qualitative variables, we also see all the answer possibilities present in the data set and their repartition.  

## 2) Data pre-processing
- In this second part, we prepare the data so that they can then be used. Thanks to the previous part, we were able to see and understand our data. Now, we are going to prepare the data set so that it can be easily used later.  
- By observing the variables and the data present, we have decided to make some 'modifications' to allow us to better exploit the data: round some values,...
- Moreover, as we are studying weight and obesity, an interesting element to exploit may be the BMI (IMC in French), a universally used variable which makes it possible to categorize the degree of obesity. So we decided to do an insert feature.  
  The BMI is calculated with the following formula: BMI = Weight / Height^2  
  After that, we were able to make a connection between BMI and the level of obesity:  
  - Under Weight: less than 18.5  
  - Normal Weight: 18.5 & 24.9  
  - Over Weight: between 25.0 & 29.9  
  - Obesity I: between 30.0 & 34.9  
  - Obesity II: between 35.0 & 39.9  
  - Obesity III: higher than 40  
- Finally, in order to prepare the data for future graphs and operations, we found it relevant to do some encoding for our qualitative variables. We also do a decoding from the basic data to get in results two data, one completely encoded and one totally decoded.  

## 3) Data vizualisation
- Now that our data is prepared, we will visualize this data to understand and observe the relationships and importance of the different variables, the distribution of the data and the general overview of our data set.The objective of this part is therefore to determine which variables we will keep for the modeling part.   
- First, we will try to get an overview of the data set. The objective is to understand what is the composition in our dataset and to start to see correlations between some variables, which could be useful later.    
- We got first an overview of the data set, we observe the distribution in our data set with the different variable, it is quite well distributed.  
  The dataset is rather well distributed for most of the variables, so we still have the number of smokers which is very small (less than 3%), as well as the number  of people who control their calorie consumption (- 5%).
  Our dataset includes people between 17 and 25 years old with few people over 40 years old. that diet has an impact and encourages obesity with the consumption of high caloric food, alcohol and snacking between meals.  

- We made also a global heatmap of the different variables to be able to observe the correlations. We are most interested in the obesity level variable, so we look at which variables seem to be most correlated with it (the last line in particular).  
- Following different visualizations we chose the level of obesity as our target.  
  - We conclude that the most important variables that have the greatest impact on the level of obesity (according to our dataset) are: family history with overweight, frequency of consumption of high caloric food, consumption of vegetables, consumption of water daily, consumption of alcohol... So we have thus made further visualizations for these variables.  
- These graphs and our study allow us to conclude a few things:  
  - Having a family history of overweight largely favours obesity. If a person has a family history of overweight he or she has to be even more careful about what he or she does to avoid becoming obese.  
  - Age plays a more or less direct role in the level of obesity, but since getting older does not imply weight gain, we can assume that behind this observation lies other things in lifestyle habits.  
  - Logical link betwen eting high caloric food and level of obesity  
  - Transportation used doesn’t really impact but walking is obviously advantageous for people  

## 4) Modeling
- After we are done visualizing our data, it is time to see the correlations and accurency of different models to optimize and better understand our data set. To do this, we will use Machine Learning concepts to try to understand which model is the best and allows us to understand and exploit our data.  
- First, we need to separate our data set into two sub-data sets: the training set and the testing set, which we will then use to test our models.  
- Then, we create an evaluation function that will allow us to obtain for each model 3 elements that will allow us to analyze the reliability of our model:  
  - The confusion matrix: It will not only highlight the correct and incorrect predictions but will also give us a clue about the type of errors made.  
  - The classification report: It is used to measure the quality of predictions from a classification algorithm.    
  - The accuracy : Model accuracy, the most important general indicator  
- Third, we apply this evaluation to our data set, with all the following classifiers:: 'KNN','SVC', 'DECISION TREE', 'RANDOM FOREST', 'ADA BOOST', 'GRADIENT BOOSTING', 'SGD', 'XBOOST'
- We have thus obtained our results for each model. In order to make it more visual, we draw 2 graphs to allow to understand and observe an overview of our results, so please check them.   

## 4.2) Modeling trials, optimization and to go further
- Here we will list/explain all the alternatives, trials, optimization and research done to get the best possible results.    
 - Trial 1: Variable modifications -> We noticed that some of our modifications in the data pre-processing part improved the efficiency of our models:  
    - Rounding the data values of the variables Age, Height, Weight, Frequency of Consumption of Vegetables, Number of Main Meals, Consumption of Water Daily, Physical Activity Frequency, Time using Technology Devices. This significantly improved our results.  
    - Creating a BMI variable greatly improved our accuracy, because BMI is another indicator more accurate than the level of Obesity. We therefore gained accuracy in our models.     
 - Trial 2: Remove the columns of variables that do not have much influence on the models. Using the heatmap, we saw that some variables were not specifically representative, and by studying the weight of some variables in our models, we thought that we could remove these columns to try to improve our model. However, after various tests, we saw that this was inconclusive as the accuracy remained about the same but the precision dropped significantly. So we decided not to continue in this way.  
 - Trial 3: Change the hyper parameters and do a grid search: this is the last optimization we tried and we detail it at the end of our notebook.  

## Thank you for taking the time to read our report
HIEN Victor - LUTTENBACHER Léa - MENU Victor  
DIA 1
