<p align="center">
  <img src="https://github.com/EnriqManComp/Efficient-Automation-of-Recipe-Selection-Boosting-Traffic-with-Machine-Learning/blob/master/Recipe_Website_Image.png?raw=true" alt="Logo">
</p>


# Efficient-Automation-of-Recipe-Selection-Boosting-Traffic-with-Machine-Learning 🍽️📈
This project automates the recipe selection process to increase traffic on a fictional recipe website by implementing a machine learning solution. 

## About Tasty Bytes 🫛
Tasty Bytes was founded in 2020 in the midst of the Covid Pandemic. The world wanted
inspiration so we decided to provide it. We started life as a search engine for recipes, helping
people to find ways to use up the limited supplies they had at home.

Now, over two years on, we are a fully fledged business. For a monthly subscription we will put
together a full meal plan to ensure you and your family are getting a healthy, balanced diet
whatever your budget. Subscribe to our premium plan and we will also deliver the ingredients
to your door.

### Problem Statment 🧾:
Currently, the product manager manually selects his favorite recipe from a list and features it on the homepage. He has observed that website traffic increases by as much as 40% when a popular recipe is chosen. However, he lacks a systematic method for determining which recipes will be popular. As more traffic translates to increased subscriptions, solving this challenge is crucial for the company's success.
 #### Business Requirement:
  * Predict which recipes will lead to high traffic.
  * Correctly predict high traffic recipes 80% of the time.

### Objective:
Automate the recipe selection process to boost website traffic.

# Report Summary 📑

This overview is intended to offer a comprehensive perspective on the strategy employed to address the problem. The approach is organized into steps in accordance with the grading rubric and clarity requirements. For a more detailed and confirmed understanding, please refer to the accompanying code sections below.

1. **Data Validation ✅** 
In this section, an initial data cleaning process is performed. The operations conducted on the data are described as follows:
 * Recipe column: No duplicated recipes were found, and the recipe identifiers were set as the index of the dataframe.
 * Numeric fields (calories, carbohydrate, sugar, and protein): No out-of-range recipes were found for any of the fields. Additionally, 52 missing values were identified, corresponding to the same 52 recipes.
 * Category column: Eleven categories were identified and converted into ten categories (Chicken Breast converted to Chicken).
 * Servings column: Three recipes were corrected due to additional information ('4 as a snack' to 4, and '6 as a snack' to '6'), and the column was set to int type.
 * High Traffic column: 373 missing values were identified and replaced with 'Not-High' traffic.

2. **Exploratory Data Analysis (EDA)** 🔍
In this section, analyses were conducted on the data with the aim of extracting valuable insights about the data and determining the appropriate approach for handling missing values. The procedures were carried out as follows:
 * Created a distribution of nutritional components by category to observe the trends. This helps determine the appropriate method for later imputing the missing values.
 * Analyzed the quantity of recipes per category and those causing higher traffic overall. Also, examined the categories with higher traffic within each serving category.
 * Plotted a pairplot to analyze the relationship between nutritional components. The same analysis was extended by category using scatterplots and regression lines.
 * Plotted boxplots of nutritional components by category to analyze outliers.
 * A comparison between nutritional components and high traffic was performed to determine customer interest, specifically in certain nutritional component content.
 * An analysis of the kernel density estimate (KDE) distribution of the servings column was performed to determine customer interest.

3. **Handling missing values** 🧩
After the analyses conducted in the EDA section, two methods for estimating missing values were identified. The first involved estimating missing values by the mean of the distribution for categories and nutritional components that exhibited a no well-defined skewed distribution. The second method, as the rest of the distributions displayed a right-skewed distribution, involved estimation using the median by category.

4. **Preprocessing Data** 🔄
 * **Outliers:** Due to the significant presence of outliers, it is necessary to scale the values of nutritional components using a robust method. For this reason, RobustScaler was employed.
 * **Category variables:** The category column was converted to dummy variables to be used in the models that will be subsequently fitted.

5. **Fitting and Evaluating the models** 📊
 * **Baseline model:** Gradient Boosting Classifier was chosen as the baseline model, and a grid search for hyperparameters was conducted. Subsequently, the baseline model was fitted with the training data and evaluated using the test data. Evaluation considered various metrics, including accuracy, F1 score, recall, precision, and confusion matrix. However, the decisive metrics taken into account were accuracy, recall, and the confusion matrix.
 * **Comparison models:** As a comparison, four models were selected: Random Forest, Logistic Regression, KNN, and Support Vector Machine. The same fitting and evaluation process as the baseline model was applied to all four. The metrics of all models were compared, and two models were selected as the best performing based on their accuracy and recall score values. The first is the Gradient Boosting Classifier model with a recall of 0.86 and accuracy of 0.74. The second is the Logistic Regression model with a recall of 0.82 and accuracy of 0.77.

6. **Recommendations** 💡
 * Increase the number of recipes in the dataset following the observations clarified in this section to achieve higher traffic.
 * Increase the descriptive variables for each recipe to identify customer preference trends. These variables will also be used as new features to enhance the performance of the Logistic Regression model.
 * Implement targeted marketing as user preference trends are identified.
 * Establish a routine for continuous monitoring of the set thresholds for KPIs and the ROC curve to observe the performance variation of the Logistic Regression model as it is updated with new data.
 * Simultaneously update the Gradient Boosting Classifier Model with new data to compare the performance behavior of both models in the future.
