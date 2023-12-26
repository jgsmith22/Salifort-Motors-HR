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
