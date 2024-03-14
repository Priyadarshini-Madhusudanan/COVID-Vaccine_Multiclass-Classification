Introduction
The world recently faced the crisis of CoronaVirus Disease (COVID) and millions of lives were lost due to a cure not in place. The invention of COVID vaccines addressed the crisis. However, where there is a cure there are always side effects. We were interested in investigating if there are any adverse effects of covid vaccination in a certain age group or population.
We have leveraged Publicly available United States Federal Drug & Administration (FDA) Vaccine Adverse Event Reporting System (VAERS) dataset to analyze and predict the adverse events of COVID.
The dataset comprises 52 features & about 3 millions data records. It ranges from the 1st to the last quarter of 2021 which accounts for 1 year of continuous adverse events reports. We aimed to analyze COVID's impact by leveraging 2021 data. Given the vast dataset, we chose to focus on the first quarter (Jan - March) for more targeted analysis. This comprises a small population of individuals who experienced an adverse event after taking the covid vaccine (Pfizer, Moderna, Jansen) and reported it to the FDA.

Objective  
The project goals are Predicting the adverse events post COVID-19 vaccination which is any event that leads to a life-threatening outcome. It also includes the case where the patient died. Hence an adverse event might be, Hospitalization, Death.

Data Collection
The data used in the project was acquired from the Federal Drug Authority USA consisting of the data from first quarters of 2021. Data includes patient's information such as, Age, Gender, Medical History, Type of vaccine, Symptoms, Hospitalization, Death etc.

Exploratory Data Analysis
We explored the data by collecting the data from the VAERS website for the year 2021.We obtained three CSV files containing patient demographics, symptoms, and vaccine data and combined them using a left join on the unique identifier VAERS_ID. After filtering for the first quarter of 2021, our dataset comprised 52 features and 292,219 records. Approximately 43% of cells were missing, with 15% duplicate rows identified. The data consisted of 39 categorical and 13 numerical variables.

Data Pre-Processing Methods and Implementation
To prepare our data for predictive modeling, we employed various methods to clean the dataset and address the issues mentioned earlier.
●	Filtering Data to get the first Quarter of 2021
●	Dropping Columns with 90% missing Values
●	Dropping Duplicate rows
●	Fill na (To replace missing Values)
●	Correlation Analysis
●	Box Plot to visualize outliers
●	Summarizing Categorical columns into one column to reduce data dimensionality
●	Use the replace method for binary columns
●	Descriptive Summary statistics by running the describe() function
●	Combining rare categories under a threshold and replacing with a new category to reduce data dimensionality
●	Generated bar plot for every categorical column to be able to visualize the frequency of each category in each column
●	Preprocess for multi class output died and hospitalized as 0,1,2,3
●	Applied SMOTE (synthetic minority over sampling technique) to balance our data and TV.
●	Defining X and Y, train test split, feature scaling, Developed a baseline dummy model
During the data preprocessing stage, we undertook essential actions to ensure our dataset was modeling-ready and of high quality.

Missing Values: Using a combination of imputation and deletion strategies, we first managed the missing values according to the specific characteristics and degree of missingness within each feature. This confirmed that our dataset was completed and prepared for analysis. 

Encoding Categorical Variables: To transform category data into numerical representations compatible with machine learning algorithms, we also encoded them. By doing this, we made it possible for our models to use and comprehend categorical data in the prediction process.

Combining Rare Categories: We also faced the challenge of rare categories within some categorical variables, which could cause our models to become noisy or sparse. To resolve this problem, we combined and simplified our categorical features while maintaining relevant data by combining common categories with a small number of information into a single category. By taking this strategy, we were able to ensure that our models were not disproportionately influenced by uncommon categories, improving their robustness and interpretability.

Target Variable Creation: Defining our target variable was an important step in the modeling process. We categorized patients into distinct classes that represented different adverse outcomes by combining data from the 'Hospital' and 'Died' features: 1 for hospitalization, 2 for death, and 3 for both outcomes. This made it easier to train our classification models because it gave the prediction labels a clear and meaningful meaning.

Feature Selection: We carefully chose a subset of relevant features based on their predictive power and significance to the target variable using RFE (Recursive Feature Elimination). This optimization step aimed to improve model performance while reducing dimensionality and computational complexity. By selecting only the most informative features, we streamlined our modeling pipeline and focused computational resources on the most impactful predictors.

Oversampling using SMOTE: We used the Synthetic Minority Over-sampling Technique (SMOTE) to address the class imbalance because our dataset was extremely imbalanced. SMOTE created synthetic samples of the minority class In order to successfully balance class distributions and lessen bias towards the dominant class . This preprocessing step was necessary to develop unbiased, strong classification models that could correctly predict adverse events.

Hyper-parameter Tuning: Utilizing GridSearch, we obtained the optimal model parameters to ensure maximum optimization. With the best parameters identified through GridSearch, we implemented both LGBM and XGBoost algorithms.

Model performance
We developed  multi class supervised learning predictive models to classify the likelihood of adverse event post Covid vaccination.We evaluated the performance of various algorithms to determine the most effective model for our task. Naive Bayes showed a reasonable accuracy of 84.96%, while logistic regression performed better at 95.82%. Decision tree models achieved an accuracy of 94.81%, while ensemble methods like XGBoost and LightGBM surpassed others, with accuracies of 96.7% and 98.1% respectively. These findings highlight the effectiveness of different classification algorithms in predicting adverse outcomes, with ensemble methods showing potential for achieving high accuracy.

Insights and Conclusions
Our analysis of covid-19 vaccine adverse events has yielded several important insights that can inform healthcare practices and vaccination strategies. 
●	Hospitalization & Death: LightGBM, the most effective model we have obtained as part of our analysis, can predict the adverse events with the following accuracy: 
(i) When a person does not encounter any adverse event: 100% accuracy(sensitivity)
(ii)When a person is hospitalized: 70% accuracy(sensitivity)
(iii) When a person encounters death: 15% accuracy (sensitivity)
(iv)When a person encounters hospitalization and death: 100% accuracy (sensitivity)
As we can observe from the above metrics, we are able to achieve a less significant accuracy for class 3 since the data is highly imbalanced and this class has only about 1% in the entire dataset.
●	Gender: We observed a notable gender disparity in adverse event occurrences, with females exhibiting a higher sensitivity compared to males. This finding underscores the importance of considering gender-specific factors in vaccine administration and monitoring protocols, ensuring tailored healthcare interventions for at-risk populations.
●	Age: Age emerged as a significant predictor of adverse events, with individuals above the age of 40 at much higher risk. Our analysis suggests that individuals in this age group should seek medical consultation before proceeding with vaccination, emphasizing the importance of personalized healthcare recommendations based on age-related factors.
●	Addressing Sickness: Our findings highlight the importance of promptly addressing sickness encounters following vaccination. Early detection and intervention can reduce the severity of adverse events and improve patient outcomes, emphasizing the need for post-vaccination monitoring and healthcare support systems.
●	Vaccine Manufacture: Our analysis revealed inconsistency in adverse event percentages among different vaccine manufacturers. Specifically, the percentage of adverse events associated with Pfizer vaccines was higher compared to Moderna and J&J. This insight underscores the importance of vaccine selection and monitoring.

Our study emphasizes the importance of data-driven approaches in understanding and reducing adverse events associated with vaccination. By identifying demographic and vaccine-related risk factors, we can adjust vaccination strategies to prioritize patient safety and healthcare outcomes. Our findings emphasize the need for proactive healthcare measures, such as gender-sensitive vaccination strategies, age-specific consultations, and careful post-vaccination monitoring, to ensure the safety and efficacy of vaccination programs.

