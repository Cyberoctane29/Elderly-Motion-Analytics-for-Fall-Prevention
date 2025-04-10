# Elderly Motion Analytics for Fall Prevention

This project analyzes how vertical acceleration, measured through wearable motion sensors, influences the probability of lying down among older adults. Using binomial logistic regression, I aim to model this relationship to inform the development of fall detection and elderly monitoring systems. The project uses Python libraries such as pandas, seaborn, statsmodels, and scikit-learn for data preprocessing, visualization, modeling, and performance evaluation.

## **Project Overview**  

The **Elderly Motion Analytics for Fall Prevention** project aims to:  

- **Model LyingDown Behavior**: Predict the likelihood of an individual lying down based on vertical acceleration data  
- **Evaluate Predictive Power**: Interpret coefficients and assess model accuracy using ROC-AUC, F1 Score, and other metrics  
- **Check Assumptions**: Assess the linearity of the logit and consider implications of assumption violations  
- **Support Fall Detection Research**: Provide practical insights that can assist in real-time motion monitoring and early detection systems  

## **Dataset Structure**  

The dataset contains motion sensor readings collected from elderly individuals. The main features used in this analysis include:  

- **Acc (vertical)**: Continuous variable representing vertical acceleration from the sensor  
- **LyingDown**: Binary outcome variable indicating whether the individual is lying down (1) or not (0)  

Additional derived columns were created for diagnostic and visualization purposes.

## **Data Processing and Analysis Steps**  

- **Data Cleaning**:  
  - Filter relevant observations and drop missing values  
  - Convert data types and validate binary encoding for the target variable  

- **Exploratory Data Analysis (EDA)**:  
  - Visualize the overall distribution of vertical acceleration  
  - Plot class-specific histograms to assess overlap between LyingDown classes  

- **Modeling Approach**:  
  - Fit a binomial logistic regression using `statsmodels`  
  - Interpret coefficients and calculate odds ratios  
  - Assess model assumptions including linearity of the logit  
  - Evaluate model performance using accuracy, precision, recall, F1 score, and ROC-AUC  

- **Linearity of Logit**:  
  - A plot of binned `Acc (vertical)` values against log-odds revealed a **non-linear, U-shaped trend**, violating the linearity of the logit assumption.  
  - This suggests the predictor is not perfectly captured by a simple linear term.  
  - To better model this, I could consider polynomial transformations, splines, or interaction terms.  
  - However, given the **moderate level of non-linearity**, and since my primary goal is prediction, I’m comfortable proceeding without adjustment for now—especially if performance metrics (e.g., accuracy, ROC-AUC, F1) remain strong. I’ll keep this in mind for future refinements if necessary.

## **Key Insights**  

### **Predictor Strength**  
- The histogram by class shows **two distinct peaks** for `Acc (vertical)`, suggesting it is a **meaningful predictor** of body position  
- While some overlap exists between classes in the middle range, the separation is clear enough to aid classification  

### **Coefficient Interpretation**  
- The model shows a statistically significant negative coefficient for `Acc (vertical)`, indicating that higher values are associated with **lower odds of lying down**  
- Odds ratio interpretation: For each unit increase in vertical acceleration, the odds of lying down decrease  

### **Model Evaluation**  
- Accuracy, F1 score, and ROC-AUC indicate that the model performs **well in distinguishing between classes**  
- Despite mild assumption violations, the model shows strong predictive ability  

## **Project Highlights**  

- Applied **logistic regression** to a real-world binary classification task  
- Performed **EDA and visual diagnostics** to support modeling decisions  
- Evaluated model assumptions and discussed limitations openly  
- Interpreted results in terms of **practical implications** for fall detection and elderly care  
- Used **ROC-AUC and classification metrics** to validate model performance  

## **Future Work**  

- **Refine Model Formulation**: Apply non-linear transformations or splines to better model the relationship  
- **Add More Predictors**: Incorporate additional motion metrics or contextual features (e.g., time of day, activity type)  
- **Develop Real-Time Monitoring Tools**: Translate the model into deployable systems for wearable or smart home devices  
- **Explore Alternative Models**: Compare logistic regression with tree-based or ensemble classifiers  
- **Evaluate on Broader Data**: Test on larger, more diverse samples of elderly individuals for generalizability  

This project highlights how a well-structured statistical approach, even with assumption trade-offs, can yield **interpretable and actionable insights** in health-related motion analytics.
