

## ***INTRODUCTION.***
The General Social Survey, or GSS, has run annually since 1972; it surveys a representative sample of the adult population in the American society;
It is widely used by politicians, policy makers, and researchers.
in order to monitor and explain trends and constants in attitudes, behaviors, and attributes. and asks questions about standard core of demographics, beliefs about social and political issues, behavioral, and attitudinal questions, plus topics of special interest. Among the topics covered are civil liberties, crime and violence, intergroup tolerance, morality, national spending priorities, psychological well-being, social ‎mobility, and stress and traumatic events.  
Altogether the GSS is the single best source for sociological and attitudinal trend data covering the United States. It allows researchers to examine the structure and functioning of society in general as well as the role played by relevant subgroups and to compare the United States to other nations.
Source  http://gss.norc.org/About-The-GSS
About the Data
The survey is conducted face-to-face with an in-person interview by National Opinion ‎Research Center (NORC) at the University of Chicago. However, participation in the study is strictly voluntary.
Therefore, study based on the GSS sample data is:
•	generalizable to the target population if we ignore the non-response bias;
•	definitely not causal, because the study does not employ random assignments and is only observational.

#### Research Question
As for the research question, I'm interested in exploring the relationship between people's job preference and their education status, using latest data. 
More specifically, are people's preference in a job (like job security, high income, short working hours etc.) associated with their highest degree received?
Motivation: Aside from sleeping, working is the activity that takes away the most of our lifetime hours, and has a huge impact on people's well-being and happiness. I would be really interested in the factors that determines peoples' attitude toward job.

## ***Reading the data.***
The data we’ll use is from the General Social Survey (GSS). [Using the GSS Data Explorer](https://gssdataexplorer.norc.org/projects/52787), 
I selected a subset of the variables in the GSS and made it available along with this notebook. The survey contains more that 5000 of variables with data on a wide range of subjects, I have selected just a few.

## ***Data Cleaning and Validation.***
       As the old says "garbage in garbage out".

Now we’ve got our datase loaded, it's important to validate it, which means checking for errors.
The kinds of proplems and errors we've to check for depend on the nature of the data, the collection process, how the data is stored and transmitted, etc.
For this dataset, there are three kinds of validation we’ll think about:
#### ***Missingness*** 
Missed data might be represented using special codes, or there might be patterns in the data that indicate problems with the survey process and the recording.
Seemingly, there're alot of missingness in realic, gunlaw and grass columns.
<p>
<img src= https://user-images.githubusercontent.com/84151016/170541964-4a8bf65f-9506-4284-9dfc-b1eac82d242d.png width= 400 />
 <img src= https://user-images.githubusercontent.com/84151016/170541987-ba1bc8cc-2b1f-4dfe-896f-98bd9d42f68d.png width= 400 />
 <img src= https://user-images.githubusercontent.com/84151016/170542061-17f04ba8-28d4-4227-9a11-363b50baeb00.png width= 400 />
</p>
 
We can describe missingness in GSS as missing-not-at-random, as there's a heigh-relationship between missingness and remaining values.
There's a strong negative correlation between missingness in gunlaw and grass columns
And we can notice that there'are a heigh-relation between missingness in age and cohort columns.

Again from this dendogram and heatmap, we can observe:
There is a heigh-correlation between missingness in age and cohort columnsand some missied samples in edu and realinc and grass too.
And strog negative correlation between gunlaw and grass columns.
This heatmap confirms everything, we have elicited from matrix and dendogram.

<br> From the ***CUMULATIVE CODEBOOK*** of our GSS. [link](https://gss.norc.org/documents/codebook/gss_codebook.pdf), we'll replace NANs in***` gunlaw and grass columns `***with their origin values, "***Don't know***". Which refers to respondents who refused to answer those questions.

Missingness in age, cohort and educ columns will be dropped, as they are the same samples and represent 0.3% of our dataset.

##### ***Missingness imputation.***
We're going to impute the remain missingness in ***cohort, educ and realinc columns*** 
***KNN imputation technique.***
<br> It uses the ***K-Nearest Neighbor algorithm*** for predicting the missing values, finding the most similar data points using all the non-missing features for a data point and calculates the average of these similar points to fill the missing feature. Here, K specifies the number of similar or nearest points to consider.

#### ***Integrity of the dataset***
Whether the data were corrupted or changed during transmission, storage, or conversion from one format to another. 
We need to check our interpretation of the data; for example, whether the numbers used to encode the data mean what we think they mean.

### Datatype constrains.
We've to make sure that data's in correct datatype. Luckily, Python has specific data type objects for various data types. This makes it much easier to manipulate these various data types in Python.

As such, before preparing to analyze and extract insights from our data, we need to make sure our variables have the correct data types, other wise we risk compromising our analysis.


### Cross field validation.
Year column contains the year of interview with respondent, and cohort column conatains the year in which the respondent was born. So, we can say that respondent age is considered the output of the Subtraction between year and cohor to make sure that data stored in age column is valid.

Validating data can be a tedious process, but it is important. If you interpret data incorrectly and publish invalid results, you will be embarrassed in the best case, and in the worst case you might do real harm. See this article for a recent example. However, I don’t expect you to validate every variable in this dataset. Instead, I will demonstrate the process, and then ask you to validate one additional variable as an exercise.

We hear a lot of talk these days about liberals and conservatives. I’m going to show you a seven-point scale on which the political views that people might hold are arranged from extremely liberal–point 1–to extremely conservative–point 7. Where would you place yourself on this scale?
You can read the documentation of this [variable in the GSS codebook](https://gssdataexplorer.norc.org/variables/vfilter).
To visualize these distributions, we’ll use the Probability Mass Function (PMF), which is similar to a histogram. The difference is that the PMF is “normalized”, which means that it shows the percentage of people who gave each response, rather than the number.
