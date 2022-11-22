# Crime and Wildfire Housing Analysis

## Week 1
### Assigned Roles
* Square - Shannon - repository owner
* Circle - Lee - mockup of a database(basic schema)
* Triangle - Kyle - mockup of machine learning model
* X - Afton - technologies

### Communication
We will primarily be communicating in our slack group. Lee and Shannon are available weeknights and weekends. Kyle is available evenings Sat, M, W, Th. Afton does not have a set schedule but will meet up as needed. Trello will be used to stay on task and meet deadlines. Zoom will be utilizted to collaborate outside of class times.
[Trello](https://trello.com/invite/b/PgQ0nXA4/ATTIa4dccc45909e55e864ab3e269c1ccfe45A9532FE/final-project)

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
    * On further analysis of our prelimary selected datasets we realized we would need to add the OpenAddresses dataset because the wildfire dataset contained lattitudes and longitudes instead of zip codes. While trying to merge on zip code we then had issues with no lattitude and longitude pairs matching. While looking for other options we discovered a python module, uszipcode, that uses data from datasets from 2018 to 2020 that allowed us to get cities for our lattitude,longitude pairs without making API calls. 

* Preliminary Data Processing
    * Our preliminary data processing consisted of cleaning our data to get it ready for analysis. We had large raw datasets that we needed to drops unnessar columns and nulls as well as rename and reorder columns before they would be ready for the database. We had to change columns names from all caps to lower case for .merge to work in pandas. We then realized that we didn't have any matches to merge and used the uszipcode module in python previously mentioned.

* Preliminary Feature Engineering and Preliminary Feature Selection
    * We dropped columns we knew would were not needed. As we progress with our model we may need to fine tune our feature selection to eliminate noise. By chooseing significate features we hope to improve the performance of our model.

* How Data Was Split Into Training and Testing Sets

* Model Choice - Random Forest Classifiers | Neural Networks

Random Forest Classifiers - A combination/ensemble of random decision trees for classification. The output of the random forest is the class selected by most trees, like an average prediction.
    * Benefits - Accuracy is typically high. It's efficiency is most prominant with large data sets. It does not overfit with more features. Forests generated could be saved and reused. 

    * Limitations - Random forest classifiers require a lot of computational power and resources as it builds numerous trees to combine the outputs. A lot of time is also required for training as it combines a lot of decision trees to determine the class. Due to the ensemble of the decision trees, it also can be more difficult to interpret and may struggle to determine the significance of each variable. 
    
    ![image](https://github.com/speddings/crime_housing_analysis/blob/AftonsBranch/Images/RandomForestClassifierVisualAid.png)
    * [A Visual Guide to Random Forests](https://towardsdatascience.com/a-visual-guide-to-random-forests-b3965f453135)

Neural Networks - Neural networks combine the power of our neural abilities to process data and create outputs using the input layer, hidden layers, and the output layers.
    * Benefits - Neural networks lead to effective visual analysis since an artificial neural network is similar to that of a human's neural network. It can process unorganized data. They may not require as much training time as artificial neural networks quickly transform, adapt, and adjust to new environments. Neural networks typicall have a user-friendly interface.

    * Limitations - Neural networks may require heavier machinery and hardware as compared to other models and cost more to invest it. Neural networks can often create incomplete results/outputs. To prevent faulty/distorted findings neural networks need to be large amounts of data. 

    ![image](https://github.com/speddings/crime_housing_analysis/blob/AftonsBranch/Images/NeuralNetworkVisualAid.png)
    * [Neural Networks Basics](https://social.technet.microsoft.com/wiki/contents/articles/32140.visual-basic-net-neural-networks-basics.aspx)

### Links
[Tableau](https://public.tableau.com/views/CrimeHouseingAnalysis/Dashboard2?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link)
[Presentation](https://docs.google.com/presentation/d/1-puxLIPB6Hh_OjgRc4uT9RSXgNqcqybiYex7fpONIfU/edit?usp=sharing)