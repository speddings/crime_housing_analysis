# Crime and Wildfire Housing Analysis

## Week 1
### Assigned Roles
* Square - Shannon - repository owner
* Circle - Lee - mockup of a database(basic schema)
* Triangle - Kyle - mockup of machine learning model
* X - Afton - technologies

### Communication
We will primarily be communicating in our slack group. Lee and Shannon are available weeknights and weekends. Kyle is available evenings Sat, M, W, Th. Afton does not have a set schedule but will meet up as needed. Trello will be used to stay on task and meet deadlines. Zoom will be utilizted to collaborate outside of class times.

### Seclected Topic
#### Crime and Wildfire Housing Analysis
We will be looking at the impact of wildfires and crime on housing prices in CA and the safey of the neighborhoods based on the wildfires and crime features.

### Reason for Selected Topic
We wanted to try to do something a little different while working with datasets we would be able to understand without extensive research due to time constraints. We also wanted to pick datasets that would allow for visualizations for the final presentation.

### Description of the Source of Data
[USA+California Wildfire Data](https://www.kaggle.com/datasets/avkashchauhan/california-wildfire-dataset-from-2000-2021)
This data set was found on Kaggle and is from the NASA website.
[California Crime Data](https://ucr.fbi.gov/crime-in-the-u.s/2019/crime-in-the-u.s.-2019/tables/table-8/table-8-state-cuts/california.xls)
This dataset is from the FBI.
[Housing Data](https://www.zillow.com/research/data/)
This data is from Zillow
[OpenAddresses - CA](https://www.kaggle.com/datasets/openaddresses/openaddresses-us-west?select=ca.csv)
This data was found on Kaggle but is from OpenAddresses and is needed to convert longitude and lattitude pairs to zip codes.
[Combined Data Sets](https://drive.google.com/drive/u/0/folders/1-zhi3_Q58BbRhsWnGf-_EYHGx61R9N05)

### Mock Up Dataset
![image](https://github.com/speddings/crime_housing_analysis/blob/main/Images/Final%20Project%20Mockup%20database.png)
### Mock Up Machine Learning
![image](https://github.com/speddings/crime_housing_analysis/blob/main/Images/Flowcharts.jpeg)

### Technologies to Use
* Jupyter Notebook - reading and cleaning data
* Python
    * Pandas
    * Tensorflow
* Jupyter Notebook
* SQL
* SQLAlchemy - connection string
* PGAdmin 
* Machine Learning (Scikit Learn)
* Tableau


### Questions We Hope to Answer Through Our Analysis
* What neighborhoods in California area are safest taking into consideration crime and natural disasters?
* What trends can we see between wildfires and crime?
* Which zip codes have the highest crime?
* Which zip codes have the lowest crime?
* Which zip codes were impacted by wildfires?
* How does the crime and wilfires data effect the house pricing data?

## Week 2

### Descriptions
* Data Exploration
    * Drop unnecessary columns.
    * Drop nulls.
    * Rename columns.
    * Check data types and unique values.
    * Reorder columns.

* Analysis
    * On further analysis of our prelimary selected datasets we realized we would need to add the OpenAddresses dataset because the wildfire dataset contained lattitudes and longitudes instead of zip codes. 

* Preliminary Data Processing
    * Our preliminary data processing consisted of cleaning our data to get it ready for analysis. We had large raw datasets that we needed to drops unnessar columns and nulls as well as rename and reorder columns before they would be ready for the database. We had to change columns names from all caps to lower case for .merge to work in pandas.
* Preliminary Feature Engineering and Preliminary Feature Selection

* How Data Was Split Into Training and Testing Sets

* Model Choice - Neural Networks
Neural networks
    * Benefits

    * Limitations


