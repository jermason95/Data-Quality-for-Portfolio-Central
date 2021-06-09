# Data Quality for Portfolio Central
Data analysis with an interactive dashboard that allows stackholders to quickly identify current trends, data quality averages, and locations of incorrect data.


### About
The purpose of this project was to objectively measure the quality of data for critical information in the Portfolio Central application.  Specific outcomes of this project include:

•	Identifying critical information (“what matters most”)

•	Defining business rules (“what makes data fit for purpose”)

•	Executing data quality measurements

•       Trend Analystis

•	Improving Data


### Process
#### 1. Identifying Critical Information

        •	Data Profiling

        •	Outlier Detection

        •	Statistical & Pattern Analysis

        •	Custom Rule based validation
    
*this work was done through a tool called Collibra. More details on this process can be seen in the project Data Quality ESG (add link)

#### 2. Defining Business Rules

     Business Rules are statements that describe the requirements for our data to be fit for purpose. 
     Requirements are defined by our stakeholders and apply to the data regardless of the storage method and location.
     The rules are aligned to requirement types and dimensions that tell us at a glance what kinds of requirements apply to the term
     
![Data Rule Categories](https://user-images.githubusercontent.com/85593608/121283266-d3e51a00-c8a8-11eb-9dde-0234018a7a8f.png)


#### 3.Executing Data Quality Measurements

Through our data lineage tool we developed exactly where the data comes from and how we can join tables.
![image](https://user-images.githubusercontent.com/85593608/121288462-67bae400-c8b1-11eb-9cdf-c35322521b2f.png)

For this project we found the data was housed in 15 different tables and views. Data came from the Global LEI Foundation, Neoxam (for 3rd party vendors), Portfolio Central, and Everest (for investment teams). Linked servers had to be setup in order to join tables across these softwares. Then high level sql was required to create a view to join all of the tables, which all had their own unique structure.

Once the view was in place, I setup a stored procedure to refresh the view then automatically run a the hard coded rules daily.

Here is a simple example of a set up rules and it's code.
LEI: Legal Enity Identifier

Completeness: LEI must be present for all portfolios that do not envolve derivative trading

Conformity: LEI must consist of twenty alpha-numberic characters, with the last two digits numeric

Accuracy: LEI must match the legal entity identifier provided by the Global LEI Foundation with an 'Active' status and 'Issued registration. 


![image](https://user-images.githubusercontent.com/85593608/121286616-152bf880-c8ae-11eb-8a36-1eef9b7c5bf8.png)




#### 4. Trend Analystis

In order that users across the Baring's enterprise could personally see the trends on the specifc data they needed, I created the below Microsoft PowerBI Dashboard.


As you will see, this dashboard not only allows users a fast glance at the high level standing of the data in their system, but also provides a variety of drill downs for users to see specifics at the granular level

Format:

Top Left: Drill downs by system name, grouping (eg investment team), and term names

Top Right: total number of failures based on category of the rule

Middle Left: overall scores based on category (these will display red and email an alert if it drops below a certain threshold. 95% in this case)

Middle Right: historical trend line

Bottom: field name and number of failures. High to low. 

![image](https://user-images.githubusercontent.com/85593608/121284368-be70ef80-c8aa-11eb-8a04-aa32e10ea98d.png)
![image](https://user-images.githubusercontent.com/85593608/121284553-0abc2f80-c8ab-11eb-921c-eca6fe999e3c.png)



Practical Functionality:
Taking audit firm as an example, a user can select the field at the bottom, easily identify trends, then for practical use they can select exceptions at the top right and see a copy of all the failures. This can be exported to excel and filtered on any column on the left.

![image](https://user-images.githubusercontent.com/85593608/121284399-c761c100-c8aa-11eb-965a-eb81b90a23b4.png)
![image](https://user-images.githubusercontent.com/85593608/121284622-29bac180-c8ab-11eb-9191-3a341436cd48.png)

Then with the setup of an automated report creator, a user can quickly generate a report like the below for any upcoming presentation

![image](https://user-images.githubusercontent.com/85593608/121284298-a39e7b00-c8aa-11eb-9c6e-a1924b0ef270.png)

Finally, an artificial intelligence tool has also been setup where a user can ask an extrememly wide range of questions to answer any of their needs.
They only need to click the 'ask a question' button at the top.
![image](https://user-images.githubusercontent.com/85593608/121284664-3ccd9180-c8ab-11eb-8cb9-8e8d1f0c778d.png)
![image](https://user-images.githubusercontent.com/85593608/121284677-3fc88200-c8ab-11eb-94b6-121186cb6535.png)





#### 5. Improving Data
        One of the many benefits of this dashboard is it allows you the opportunity to make immediate improvements.
Certainly data cleaning and scrubbing is a large component of improving the overall data quality scores. It's quick and easy since on the exceptions screen you can export all of the completeness failures, for example, filter on data owner, and send them the excel of all the data the needs to be uploaded.
        
However, one step better than cleaning the data is setting up the controls in the software so the break never occurs in the first place.

For example, if you see a lot of completeness failures you can hard code that the field must be populated before a user is allowed to save in the software. 
For accuacy, which is the toughest problem, you can prioritize the worst data and use our data lineage maps to identify just where the inaccuate data is comming from.


### Success of this project:

**Data Quality Score** → Overall score improved from 68% to 98%

**Incorrect Data Points** → 5,000 points of inaccurate data to 300

**Recognistion** -- Personal meetings with Ian Dalton- Chief Data Officer and Steve Boehm-Chief Operating Officer, to discuss the success and oppotunites for this dashboard.

*With only 3 months since it's inception*




### What I Learned

**Data Analysis Tools** → SQL Server (creating views, stored procedures, data architecture)

**Data Visualization Tools** → Microsoft PowerBI

**Soft Skills and Critical Thinking** → Public Speaking, Quantitave and Statistical Analysis
