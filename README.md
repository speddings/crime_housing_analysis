# Housing Analysis with Crime and Wildfire Data

[Presentation](https://docs.google.com/presentation/d/1-puxLIPB6Hh_OjgRc4uT9RSXgNqcqybiYex7fpONIfU/edit?usp=sharing)

## Team Members and Roles
* Shannon - Repository Owner, Data Cleaning, Image Selection
* Lee - Database
* Kyle - Machine Learning
* Afton - Technologies, Dashboard, Presentation, ReadMe Editor

### Technologies
* Jupyter Notebook - reading and cleaning data
* Python
    * Pandas
    * Tensorflow
    * uszipcode - module
    [uszipcode](https://www.pythonpool.com/uszipcode-python/#:~:text=You%20can%20find%20the%20zip%20codes%20by%20using,to%20use%20them.%20How%20To%20Install%20Uszipcode%20Python%3F)
* Jupyter Notebook - clean data
* SQL - Structured Query Language
* SQLAlchemy - connection string
* Machine Learning (Scikit Learn)
* Tableau - Dashboard and Storyboard

## Project Overview
Topic: Housing Analysis with Crime and Wildfire Data

We will be looking at the impact of wildfires and crime on housing prices in CA and the safety of the neighborhoods based on the wildfires and crime features.

### Questions We Hope to Answer Through Our Analysis
* Considering crime and wildfires, which city/zip codes are safest?
* Is there a relation between wildfires and crime?
* How does the crime and wildfires data effect the house pricing data?

### Hypothesis
As crime and wildfires increase the housing market value will decrease.

## Analysis
### Description of the Source of Data
[USA+California Wildfire Data](https://www.kaggle.com/datasets/avkashchauhan/california-wildfire-dataset-from-2000-2021)
This data set was found on Kaggle and is from the NASA website. acq_date is the date when the wilfire was collected.
[California Crime Data](https://ucr.fbi.gov/crime-in-the-u.s/2019/crime-in-the-u.s.-2019/tables/table-8/table-8-state-cuts/california.xls)
This dataset is from the FBI.
[Housing Data](https://www.zillow.com/research/data/)
This data is from Zillow
[OpenAddresses - CA](https://www.kaggle.com/datasets/openaddresses/openaddresses-us-west?select=ca.csv)
This data was found on Kaggle but is from OpenAddresses and is needed to convert longitude and lattitude pairs to zip codes.
[Combined Data Sets](https://drive.google.com/drive/u/0/folders/1-zhi3_Q58BbRhsWnGf-_EYHGx61R9N05)

* Data Exploration
    * Drop unnecessary columns.
    * Drop nulls.
    * Rename columns.
    * Check data types and unique values.
    * Reorder columns.

Example Code 

![image]()

![image](https://github.com/speddings/crime_housing_analysis/blob/main/Images/ca_fire_tbl.png)

![image](https://github.com/speddings/crime_housing_analysis/blob/main/Images/ca_crime_tbl.png)

![image](https://github.com/speddings/crime_housing_analysis/blob/main/Images/ca_housing_median_tbl.png)

* Analysis
    * On further analysis of our prelimary selected datasets we thought we would need to add the OpenAddresses dataset because the wildfire dataset contained lattitudes and longitudes instead of zip codes. While trying to merge on zip code we then had issues with no lattitude and longitude pairs matching. While looking for other options we discovered a python module, uszipcode, that uses data from datasets from 2018 to 2020 that allowed us to get cities for our lattitude,longitude pairs without making API calls. 

![image](https://github.com/speddings/crime_housing_analysis/blob/main/Images/ca_fire_city_tbl.png)

## Database
### Mock Up Database
![image](https://github.com/speddings/crime_housing_analysis/blob/main/Images/ERD.png)

SQL Database Process
Before setting up the database, the first step was to receive and download the clean datasets locally to import the dependencies in order to use SQLAlchemy for the process.
After importing all the dependencies, the next step was to setup the database on pgAdmin. First using the schema query tools to create the tables that we will be using throughout the project. There were three tables that were used, ca_crime, ca_housing_median, and ca_fire. Upon creating the three tables on pgAdmin, the next step was to import the data into the tables that were created.
The import was not successful at times due to the data having null values or the varchar was too short/long. The clean up was quick and was done through Jupyter Notebook. Upon the successful imports, the next step was going back to the ipynb file and to insert the link, username, and password for the members to be able to access the database. In order to make it accessible, the necessary step was to create an AWS database, and to replace the host section on postgres link with the AWS endpoint link.
The database was finalized, tested, and was accessible. The next step was to merge the tables into one, while also dropping unnecessary columns. The step was done through creating a SQL query via the query tool on pgAdmin. By using the JOIN commands to join the relationships and afterwards creating a new table named ‘Final’. The database was clean, merged, and accessible and ready to connect for the Machine Learning Model.

## Machine Learning Model
### Mock Up Machine Learning - Random Forest Classifier Model
![image](https://github.com/speddings/crime_housing_analysis/blob/main/Images/Machine%20Learning.png)

* Preliminary Data Preprocessing
    * Our preliminary data processing consisted of cleaning our raw data to get it ready for analysis. We had raw datasets that we needed to drops unnecessary columns and nulls as well as rename and reorder columns before they would be ready for the database. We had to change columns names from all caps to lower case for merge to work in pandas. We then realized that we didn't have any matches to merge and used the uszipcode module in python.

* Preliminary Feature Engineering and Preliminary Feature Selection
    * We dropped columns we knew would were not needed. As we progress with our model we may need to fine tune our feature selection to eliminate noise. By focusing on significant features we hope to improve the performance of our model.


    * For the Random Forest Classifier Model we plan to do our initial run without the Ada Boost. Ada Boost may be added to improve model accuracy.

    * To input the three datasets into the Random Forest Classifier model they will be merged on city in SQL. The housing data will be an aggregate of the median housing prices. We chose the aggregate median over the aggregate average as outliers in the average could significantly skew our results. USA+California Wildfire Data will be aggregate count of cities. 

    * Features
        * aggregate count of wildfires by city
        * violentzncrime
        * nmanslaughter
        * rape1
        * robbery
        * aggravated\nassault
        * property\ncrime
        * burglary
        * larceny-\ntheft
        * motor\nvehicle\ntheft
        * arson
        * city
    * Target
        * Housing prices/mo

* How Data Was Split Into Training and Testing Sets
    * We used the default 70/30 split. To test if we have a good split we will change the split to see if the change makes a difference.

* Model Choice - Random Forest Classifiers | Neural Networks

Random Forest Classifiers - A combination/ensemble of random decision trees for classification. The output of the random forest is the class selected by most trees, like an average prediction.

    * Benefits - Accuracy is typically high. It's efficiency is most prominant with large data sets. It does not overfit with more features. Forests generated could be saved and reused. 

    * Limitations - Random forest classifiers require a lot of computational power and resources as it builds numerous trees to combine the outputs. A lot of time is also required for training as it combines a lot of decision trees to determine the class. Due to the ensemble of the decision trees, it also can be more difficult to interpret and may struggle to determine the significance of each variable. 
    
    ![image](https://github.com/speddings/crime_housing_analysis/blob/AftonsBranch/Images/RandomForestClassifierVisualAid.png)

    * [A Visual Guide to Random Forests](https://towardsdatascience.com/a-visual-guide-to-random-forests-b3965f453135)

Neural Networks - Neural networks combine the power of our neural abilities to process data and create outputs using the input layer, hidden layers, and the output layers.

    * Benefits - Neural networks lead to effective visual analysis since an artificial neural network is similar to that of a human's neural network. It can process unorganized data. They may not require as much training time as artificial neural networks quickly transform, adapt, and adjust to new environments. Neural networks typicall have a user-friendly interface.

    * Limitations - Neural networks may require heavier machinery and hardware as compared to other models and cost more to invest it. Neural networks can often create incomplete results/outputs. To prevent faulty/distorted findings neural networks need to be large amounts of data.

## Dashboard
We couldn't filter by housing price with our current data sets so the clean_ca_housing.csv was reworked to allow for that filtering capability. Also, the crime was summed so that the filter would show the city with the highest crime total vs. only one crime such as murder. These changes are shown below.


![image](https://github.com/speddings/crime_housing_analysis/blob/AftonsBranch/Images/housinganlysisT.png)

![image](https://github.com/speddings/crime_housing_analysis/blob/AftonsBranch/Images/CodeforHousingTableau.png)

![image](https://github.com/speddings/crime_housing_analysis/blob/AftonsBranch/Images/NewHousingTableau.png)

Tableau Outline
    Data Source
        * ca_fire.csv
        * clean_ca_crime.csv
        * clean_ca_housing.csv
        * clean_ca_housing_new_one.csv

    Dashboard Interactivity
        * Fire and Housing Data filterable by Median Housing Price.
        * Populations Map adjust other maps to show selected cities.

![image](https://github.com/speddings/crime_housing_analysis/blob/AftonsBranch/dashboard.png)

[Tableau](https://public.tableau.com/app/profile/afton.snider/viz/HousingAnalysiswithCrimeandWildfireData/CAMedianHousingPriceAnalysiswithWildfireandCrimeData2019?publish=yes)