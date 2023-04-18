# Practical-Application-Bank

This repo contains the Practical Application submission - including the Jupyter Notebook analysis report (link to notebook: https://github.com/ChristineNoelle/Practical-Application-Bank/blob/b9fd6fd5a60ab43e085f16234bb1dde0faaaecfc/Practical-Application-Bank.ipynb) and data set (link to data set: https://github.com/ChristineNoelle/Practical-Application-Bank/blob/b9fd6fd5a60ab43e085f16234bb1dde0faaaecfc/bank-additional-full.csv)

Summary Description

1) Business Understanding:

The analyzed data set is from a Portuguese retail bank, and was initially gathered to observe the effects of financial crisis. Currently, the data set will be used for classification purposes in order to understand relevant features to long-term bank subscriptions.


2) Data Understanding:

Examining the Materials and Methods section of the paper, it appears the dataset is related to 17 campaigns that occurred between May 2008 and November 2010. It also appears that 20 attributes are included, in the categories of bank client data, social and economic attributes, and additional campaign attributes.

The main question is one of predicting whether or not a client will subscribe to a long-term bank deposit. The business goal is to increase campaign efficiency via finding a model that can explain if the client subscribes the deposit. Identifying the main characteristics that affect success can help management of human effort, phone calls, time, and other available resources. In addition, this can aid in selection of a high quality and an affordable set of potential buying customers.


3) Data Preparation

Data exploration and analysis included 20 initial attributes. While carefully examining the data features, the following actions occurred:

- 'Unknown' values for categorical variables 'loan', 'housing', 'education', 'marital', 'job' were removed for lack of contribution to meaningful results

- Created new column for ‘pdays’ - coerced column for ‘pdays’ column into a new, dummy variable column (Yes/No). According to "Attribute Information",'pdays' column is number of days that passed by after client was last contacted from a previous campaign ("999" means client was not previously contacted, all other numerical values means client was previously contacted)

- Euribor_3Month_Daily feature was retained while highly correlated features (> 0.90) were removed to reduce dimensionality


4) Modeling:

All remaining features were dummy coded if not continuous, and evaluated though Logistic Regression. Priority features were determined through L1 regularization.
The top two features were whether the client was contacted in a prior campaign and the numerical inter-bank interest rate (Euribor).

Data were properly balanced and accuracy was chosen as comparison metric for model comparison. The reason was accuracy might best capture prediction in a binary classification problem.


5) Evaluation

In this model, the feature that had the most explanatory values in the outcome variable were the 'No Prior Contact' variable and the 'Prior Contact' variables. One can interpret that for the target of subscription, it might be best to contact targeted groups multiple times across campaigns.

The decision tree, and parameters found through GridSearchCV, performed best - with a test accuracy of 73.8%. Training accuracy was lower than test accuracy (73.3%), which was an indication that the training model was not overfit.


6) Deployment

From this particular analysis, it appears that if the client was contacted in a prior campaign, and the current Euribor rate was below 2%, the client was more likely to subscribe to a long-term bank deposit. 

Interestingly, it appears the inter-bank interest rate (Euribor), rather than characteristics of clients, contribute more to the agreement to subscribe to a long-term bank deposit. 

Proceeding forward, it seems telemarketing calls should be made when the Euribor is low. Any target or priority individuals should also be called across campaigns to increase likelihood of subscription. The next step is to determine which priority clients need to be called across campaigns. In addition, methods need to be devised to make calls according to the fluctuating Euribor.
