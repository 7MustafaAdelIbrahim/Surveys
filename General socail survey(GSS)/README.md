

INTRODUCTION
The National Data Program for the Social Sciences is designed as a data diffusion project and a program of social indicator research. The 
data come from the General Social Surveys, interviews administered to NORC national samples using a standard questionnaire. Toward the 
major goal of functioning as a social indicator program, items which have appeared on previous national surveys starting in 1937 have been 
replicated here. The search for trend items led us to published reports from Gallup, Harris, the Detroit Area Study, SRC (Michigan) studies, 
NORC files, and Federal Commissions such as those on Violence and Pornography.
By retaining the exact wording, we hope to facilitate time trend studies as well as replications of earlier findings. For the base line items in 
the initial 1972 survey, some 105 sociologists and social scientists reviewed drafts of the questionnaire, suggested revisions and additions, 
and expressed their question preference by vote. Their serious assistance was extremely helpful in putting together a final version of the 
questionnaire which would represent the varied interests of social scientists. Topic and question selection continues to be monitored by 
leading social scientists who serve as a Board of Overseers: Deborah Carr, Jeremy Freese, Bridget Goosby, Darrick Hamilton, Vincent 
Hutchings, Frauke Kreuter, Taeku Lee, Jason Schnittker, Judith Seltzer, Florenica Torche, Rob Warren, and Rebeca Wong.
The items appearing on the surveys are one of three types: Permanent questions that occur on each survey, rotating questions that appear on 
two out of every three surveys (1973, 1974, and 1976, or 1973, 1975, and 1976), and a few occasional questions such as split ballot 
experiments that occur in a single survey. Starting in 1988, items were no longer rotated across years but appeared on two-thirds of the cases 
every year. This design is discussed in Appendix Q. A detailed layout of the appearance of questions can be found right before the index to 
this codebook.
A second objective is the prompt distribution of fresh, interesting, and high-quality data to a variety of users who are not affiliated with large 
research centers. The initial survey, 1972, was supported by grants from the Russell Sage Foundation and the National Science Foundation. 
NSF has provided support for the 1973 through 1978, 1980, and 1982 through 2018 surveys. We welcome your participation in this program. 
While it is not necessary to request permission from NORC before publishing analyses of these data, we do ask that NORC be cited as the 
source of your data. We also request that copies of reports which utilize the data be sent to the General Social Survey, NORC, 1155 East 
60th Street, Chicago, IL 60637




Reading the data¶
The data we’ll use is from the General Social Survey (GSS). [Using the GSS Data Explorer](https://gssdataexplorer.norc.org/projects/52787), I selected a subset of the variables in the GSS and made it available along with this notebook. The following cell downloads this extract.


Validation¶
Now that we’ve got the data loaded, it is important to validate it, which means checking for errors.

The kinds of errors you have to check for depend on the nature of the data, the collection process, how the data is stored and transmitted, etc.

For this dataset, there are three kinds of validation we’ll think about:

We need to check the integrity of the dataset; that is, whether the data were corrupted or changed during transmission, storage, or conversion from one format to another.

We need to check our interpretation of the data; for example, whether the numbers used to encode the data mean what we think they mean.

We will also keep an eye out for invalid data; for example, missing data might be represented using special codes, or there might be patterns in the data that indicate problems with the survey process and the recording of the data.

In a different dataset I worked with, I found a surprising number of respondents whose height was supposedly 62 centimeters. After investigating, I concluded that they were probably 6 feet, 2 inches, and their heights were recorded incorrectly.

Validating data can be a tedious process, but it is important. If you interpret data incorrectly and publish invalid results, you will be embarrassed in the best case, and in the worst case you might do real harm. See this article for a recent example.

However, I don’t expect you to validate every variable in this dataset. Instead, I will demonstrate the process, and then ask you to validate one additional variable as an exercise.

The first variable we’ll validate is called polviews. It records responses to the following question:

We hear a lot of talk these days about liberals and conservatives. I’m going to show you a seven-point scale on which the political views that people might hold are arranged from extremely liberal–point 1–to extremely conservative–point 7. Where would you place yourself on this scale?

You can read the documentation of this [variable in the GSS codebook](https://gssdataexplorer.norc.org/variables/vfilter).

PMFs¶
To visualize these distributions, we’ll use the Probability Mass Function (PMF), which is similar to a histogram. The difference is that the PMF is “normalized”, which means that it shows the percentage of people who gave each response, rather than the number.


introduction form local source.

Introduction
The General Social Survey, or GSS, has run annually since 1972; it surveys a ‎representative sample of the adult population in the American society;‎
It is widely used by politicians, policy makers, and researchers.‎
in order to monitor and explain trends and constants in attitudes, behaviors, and ‎attributes. and asks questions about standard core of demographics, beliefs about ‎social and political issues, behavioral, and attitudinal questions, plus topics of special ‎interest. Among the topics covered are civil liberties, crime and violence, intergroup ‎tolerance, morality, national spending priorities, psychological well-being, social ‎mobility, and stress and traumatic events.  ‎
Altogether the GSS is the single best source for sociological and attitudinal trend data ‎covering the United States. It allows researchers to examine the structure and ‎functioning of society in general as well as the role played by relevant subgroups and ‎to compare the United States to other nations.‎
Source  http://gss.norc.org/About-The-GSS
About the Data
The survey is conducted face-to-face with an in-person interview by National Opinion ‎Research Center (NORC) at the University of Chicago. However, participation in the study is ‎strictly voluntary.‎
Therefore, study based on the GSS sample data is:‎
•	generalizable to the target population if we ignore the non-response bias;‎
•	definitely not causal, because the study does not employ random assignments ‎and is only observational.‎
Research Question
As for the research question, I'm interested in exploring the relationship between ‎people's job preference and their education status, using latest data. ‎
More specifically, are people's preference in a job (like job security, high income, short ‎working hours etc.) associated with their highest degree received?‎
Motivation: Aside from sleeping, working is the activity that takes away the most of ‎our lifetime hours, and has a huge impact on people's well-being and happiness. I ‎would be really interested in the factors that determines peoples' attitude toward job.‎


The survey contains more that 5000 of variables with data on a wide range of subjects, ‎I have selected just a few ‎
How the dataset was collected

Interview with respondent and Question associated with a variable.‎

Year:  in which year each respondent was interviewed.‎
Age: contains the respondent's age.‎
cohort, the year in which the respondent was born, from 1953 to 1998.‎

Sex: respondent's gender, 1 for male, 2 for female.‎

race: The question associated, what race do you consider yourself? ‎
Takes 3 discrete valves 1,2 0r 3. Where 1 ‎represents white, 2 for black, 3 represents other.‎

Educ: years of education.‎

realinc: represents total household income in dollars. ‎

Gunlaw: The question associated , Would you favor or oppose a law which would ‎require a person to obtain a police permit before he or she could buy a gun?‎
Grass: Do you think the use of marijuana should be made legal or not?‎
wtssall: weight variable [for number of adults in hh before or after 2004]‎

