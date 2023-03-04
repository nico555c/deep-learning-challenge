# Report

Alphabet Soup is a nonprofit foundation that provides funding to various ventures to promote innovation and social development. The foundation has been operating successfully for many years and has helped numerous organizations achieve their goals. However, as the number of applications for funding has increased over time, it has become increasingly challenging for Alphabet Soup to evaluate each application thoroughly.

In response to Alphabet Soup's need for a tool that can help it select the applicants for funding with the best chance of success in their ventures, we created a neural network model that could analyze the applications and provide insights into the potential success of each venture.

In this report, we will discuss the development of the neural network model and its performance in selecting successful applicants. We will begin by describing the dataset used to train the model and the preprocessing steps applied to it. Next, we will explain the architecture of the neural network model and the hyperparameters used to train it. We will then discuss the results of the model and evaluate its performance on a test dataset. Finally, we will conclude by discussing the limitations of the model and suggestions for future improvements.

# Dataset

From Alphabet Soup’s business team, we have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

EIN and NAME—Identification columns<br />
APPLICATION_TYPE—Alphabet Soup application type<br />
AFFILIATION—Affiliated sector of industry<br />
CLASSIFICATION—Government organization classification<br />
USE_CASE—Use case for funding<br />
ORGANIZATION—Organization type<br />
STATUS—Active status<br />
INCOME_AMT—Income classification<br />
SPECIAL_CONSIDERATIONS—Special considerations for application<br />
ASK_AMT—Funding amount requested<br />
IS_SUCCESSFUL—Was the money used effectively<br />

We studied this data and identified the target varaible for the model to be the IS_SUCCESSFUL column.
The main features of the model are considered to be APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT and ASK_AMT.
The columns that we can ignore in our analysis are EIN, NAME and SPECIAL_CONSIDERATIONS.

The next step in building out tool, was to compile, train, and evaluating the model.
In our first model, we removed the EIN and NAME columns and subcategorized the APPLICATION_TYPE and CLASSIFICATION. We then used one hot encoding to create a data frame with 34k+ rows and 45 columns/features. 
We trained the modeel on the target column IS_SUCCESSFUL using a standard scaler.
For the neural network model we used 8 layers and 6 nodes and obtained 421 parameters.<br />
[![ScreenShot](1stacc.JPG)](https://github.com/nico555c/deep-learning-challenge/blob/main/Starter_Code/1stacc.JPG)

The resuls were very promising in our first attempt but did not reach our target accuracy of 0.75.
pic2

In order to optimize the model further we made several changes and compiled, trained, and evaluated the model to study the results.
We made the following changes that did not increase the accuracy of our model:
* changed the binning parameters used on APPLICATION_TYPE and CLASSIFICATION
* picked new features for binning paired with eachother or in combnation with the original parameteres: AFFILIATION, ASK_AMT, INCOME_AMT
* changed the layers to 3, 5, 10 and 15 as well as the nodes to 1, 2, 8 and 10

None of these changes made and remarkable changes to our original accuracy.

We then decided a more radical change was needed and evaluated the data from the scratch.
We noticed that we dropped EIN and NAME because we considered them irelevant for the model. We decided the add back the NAME and check for unique values. We noticed that quite a few compaines were repeated in the data, so we decided to include the NAME in our model and used binning to subcategorize it.

With this new bin and the classification bin, we used 10 layers and 6 nodes for the modeling and our results did not disappoing.
We created a model with 0.77 accuracy that exceeded our original target.
pic 3
pic 4


The neural network model we developed will improve the way Alphabet Soup selects applicants for funding. By using this tool, the foundation can save time and resources and ensure that they are investing in ventures that have a high probability of success.

We recommend that Alphabet Soup continues to explore other machine learing modles such as logistic regression (supervised) that, with the data provided can yeld even higher accuracy levels.



