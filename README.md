# Salifort-Motors-HR
Google Advanced Data Analytics Capstone Project

This was my capstone project for the Google Advanced Data Analytics Certificate through Coursera. It contains a fictional dataset for the company Salifort Motors that looks to establish what is causing certain employees to leave the company. Below is the business case. 

### Understand the business scenario and problem

The HR department at Salifort Motors wants to take some initiatives to improve employee satisfaction levels at the company. They collected data from employees, but now they don’t know what to do with it. They refer to you as a data analytics professional and ask you to provide data-driven suggestions based on your understanding of the data. They have the following question: what’s likely to make the employee leave the company?

Your goals in this project are to analyze the data collected by the HR department and to build a model that predicts whether or not an employee will leave the company.

If you can predict employees likely to quit, it might be possible to identify factors that contribute to their leaving. Because it is time-consuming and expensive to find, interview, and hire new employees, increasing employee retention will be beneficial to the company.

### Stakeholders, Goals, and Initial Observations

Stakeholders are going to be the Salifort Motors executive team and HR team but also the Salifort Motors employees. Determining the factors of why employees leave jobs could lead to an increase in employee satisfaction which makes life better for employees and the company. 

I'm trying to determine the factors that can be used to predict if an employee is going to leave the company or not. By understanding what does and doesn't contribute to employee turnover hopefully we can increase employee satisfaction and help save the company money. 

Looking at the different categories my initial thoughts are that salary, promotion within the last five years, and satisfaction level will be the most important features contributing to whether an employee leaves or not. I think my only concern could be that because there isn't a distinction between employees that leave on their own or if they are fired, and that there's a category about job accidents, it would be tough to say if employees were fired due to accidents had at work which could be viewed as retaliation by the company. 

### Process and Decisions

The first stage of this was basic exploratory data analysis. Second stage was using visualizations to look at how the variables worked together. Third I had to decide which type of model to use. The prediction task was a binary choice (left company or did not leave company) which meant I could use a logistic regression model or more of a tree based model. With logistic regression I'd need to scale a lot of the data with the average hours being on a higher scale than the rest of the data points. I know that logistic regression is sensitive to outliers, so if there are any outliers in the data I would need to address those. I'll need to encode the categorical data regardless so that doesn't play into the decision too much. Due to all those reasons I think a tree model will work best with the different scales of data, the outliers in the dataset, and in particular it will allow me to get the feature importance and see which of the predictor variables play the biggest role in why an employee leaves or stays. 


### Data Dictionary

Variable  |Description |
-----|-----|
satisfaction_level|Employee-reported job satisfaction level [0&ndash;1]|
last_evaluation|Score of employee's last performance review [0&ndash;1]|
number_project|Number of projects employee contributes to|
average_monthly_hours|Average number of hours employee worked per month|
time_spend_company|How long the employee has been with the company (years)
Work_accident|Whether or not the employee experienced an accident while at work
left|Whether or not the employee left the company
promotion_last_5years|Whether or not the employee was promoted in the last 5 years
Department|The employee's department
salary|The employee's salary (U.S. dollars)

### Summary of model results

**Decision Tree Results:**

Precision Score: 0.868335
This model predicted 86.83% of all data points that were actually true against all the of the data points that were predicted as true. This is a fairly good score and does a decent job of predicting those who will actually leave the company vs who was predicted to leave the company. 

Recall Score: 0.854672
This model predicted 85.47% of all employees that actual left the company, whether they were predicted to do so or not. This is a good score but does indicate that a higher number of employees were predicted to stay that actually left and that could something we'd want to avoid. 

Accuracy Score: 0.954187
This model predicted 95.42% of all data points correctly. That's a great score but since the classes were at an almost 80/20 class imbalance it doesn't provide us with a ton of information. 

F1 Score: 0.861146
This shows a balanced metric between recall and precision and shows us that we don't have either score affecting the other too much. 

AUC Score: 0.946465
This tells us that we have a fairly good model. A score of 1 would imply that the model was able to perfectly distinguish between those who left and those who did not while a score of 0 would imply that the model was getting every prediction wrong. Since this score is closer to 1 I'm comfortable saying this is a good model. 

**Random Forest Results:**

Precision Score: 0.928122
This model predicted 92.81% of all data points that were actually true against all the of the data points that were predicted as true. This is a fairly good score and does a decent job of predicting those who will actually leave the company vs who was predicted to leave the company. 

Recall Score: 0.794348
This model predicted 79.43% of all employees that actual left the company, whether they were predicted to do so or not. This is a good score but does indicate that a higher number of employees were predicted to stay that actually left and that could something we'd want to avoid. 

Accuracy Score: 0.955631
This model predicted 95.56% of all data points correctly. That's a great score but since the classes were at an almost 80/20 class imbalance it doesn't provide us with a ton of information. 

F1 Score: 0.855979
This shows a balanced metric between recall and precision and shows us that we don't have either score affecting the other too much. Here you can see how, despite a precision score of almost 6% higher than the decision tree model, due to the much lower recall score (6% worse) the F1 score ends up being just slightly worse than the decision tree model (1%). 

AUC Score: 0.970592
This tells us that we have a fairly good model. A score of 1 would imply that the model was able to perfectly distinguish between those who left and those who did not while a score of 0 would imply that the model was getting every prediction wrong. Since this score is closer to 1 I'm comfortable saying this is a good model. 



Looking at these two models, they both performed quite well. Since we used the ROC_AUC score as the metric to refit against in the grid search I would use that metric to make a final comparison and say that the Random Forest model performed slightly better than the decision tree model with an AUC score of 0.97 vs 0.94. 


## Recall evaluation metrics

- **AUC** is the area under the ROC curve; it's also considered the probability that the model ranks a random positive example more highly than a random negative example.
- **Precision** measures the proportion of data points predicted as True that are actually True, in other words, the proportion of positive predictions that are true positives.
- **Recall** measures the proportion of data points that are predicted as True, out of all the data points that are actually True. In other words, it measures the proportion of positives that are correctly classified.
- **Accuracy** measures the proportion of data points that are correctly classified.
- **F1-score** is an aggregation of precision and recall.

### Conclusion, Recommendations, Next Steps

Looking at the feature importance from both the models, I was able to identify a similar pattern. Each of the models featured number of projects, company tenure, last evaluation, and overworked as having the highest importance into predicting whether or not an employee will leave the company. As such here are my recommendations:

> - Limit the number of projects a person can be working on to three (3). Looking at the balance of who left vs who didn't when it came to number of projects, three had the best results in terms of retention. This makes sense as people who are spread to thin, so to speak, tend to be less happy with their job than those that are doing a manageable amount of work. 
> 
> - Tenure appeared to become a factor around four (4) and five (5) year benchmark. This could be for a number of reasons and is something I would recommend looking closer at. If promotions are not a reasonable option for those at this stage in their tenure, look at other options for rewarding employees that have been at the company for this long, such as extra vacation, gifts, etc. 
> 
> - Last evaluation affecting whether someone stays or leaves a company could mean several things. Looking at the mean score for the evaluations we see a score of 0.7161 out of 1 which in terms of school grades would equate to about a C, indicating average performance. This could be an issue with those that thought their performance deserved something higher or could be an issue with how the evaluation is performed, or even the frequency of evaluations. Looking deeper into this process may turn up more insights. 
> 
> - Being overworked ties in slightly to the number of projects and the strain employees can feel when being asked to do too much. Looking back onto the scatterplot of hours worked vs satisfaction levels you could see how poor the scores were, and the proportion of employees that left, when their average monthly hours were above 200 per month (over 50 hours per week). I'd recommend a 40 to 45 hour work week for all employees, with rare exceptions, to help promote a better work life balance. 
> 
> - A final recommendation would be to include your employees in these decisions. Have company wide meetings, or better yet, smaller more specialized meetings across departments to find out what works best for everyone. It can be helpful to get a sense of what your teams are going through, rather than making top down decisions without input from those that may feel the brunt of those decisions the most. 







