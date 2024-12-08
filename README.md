# Water Pump Status Predictions in Tanzania

![My Image](./water_wells_image.jpeg)



Tanzania is a third world country. As of 2024 December, the country has a population of 67.44 million people. As with many third wold countries, access to clean water is a major challenge. Through both public and private participation, the country has been able to install water pumps across the country. Unforturnetly, a number of these water points require repairs or are completely not functional. 

Alot of factors affect the functionality/availablity of the water points including:
1. Geographical Loction
2. Environmental conditions
3. Water pump specifications
4. Maintenance schedules
5. Water quality

The aim of this project is to develop various machine learning models using different techniques. The models will help to categorise the water points into 3 different groups:

1. Functional
2. Non-Functional
3. Requires Repair

The stakeholders for this project include:

1. Government of Tanzania
2. NGOs in the country
3. Private Limited Companies

With this classification, the stakeholders can take corrective action to improve the situation. The results will significantly increase the effeciency of the implementation plan as the associated parties will be able to: 

1. Introduce preventative maintanance
2. Create an effective resource allocation plan
3. Improve future water points installations

The project hopeful will lead to an increase in socio-economice development in Tanzania by ensuring sustainability through clean water sources across the country. 

### Data Understanding

The data onsists of three CSV files: a training dataset with 59,400 records (80% of the data), a test dataset with 14,850 records (20%), and a third file containing the labels for the training data, which categorize each pump’s status as either “functional,” “non-functional,” or “in need of repairs.” Both the training and test datasets feature 40 columns with similar attributes, including details on pump location, construction, management, payment methods, and water quality in Tanzania.
Data source: [www.drivendata.org](www.drivendata.org)

First step is to import the required libraries for the project and load the csv files that contain the data.
From my analysis of this dataset, the irrelevant columns are:

<b>wpt_name:</b> Name of the waterpoint (not relevant for our analysis).
<b>num_private:</b> Number of private pumps (not relevant for our analysis).
<b>subvillage:</b> Subvillage location (not relevant for our analysis).
<b>district_code:</b> District code (not relevant for our analysis).
<b>lga:</b> Local government authority (not relevant for our analysis).
<b>ward:</b> Administrative ward (not relevant for our analysis).
<b>public_meeting:</b> Whether there was a public meeting related to the waterpoint (not relevant for our analysis).
<b>recorded_by:</b> Entity recording the data (not relevant for our analysis).
<b>scheme_name:</b> Name of the waterpoint scheme (not relevant for our analysis).
<b>extraction_type_group:</b> Grouped extraction type (redundant with 'extraction_type').
<b>extraction_type_class:</b> Classification of extraction type (redundant with 'extraction_type').
<b>management_group:</b> Grouped management type (redundant with 'management').
<b>payment_type:</b> Payment method (redundant with 'payment').
<b>quality_group:</b> Grouped water quality (redundant with 'water_quality').
<b>quantity_group:</b> Grouped water quantity (redundant with 'quantity').
<b>source_type:</b> Source type (redundant with 'source').
<b>source_class:</b> Source class (redundant with 'source').
<b>waterpoint_type_group:</b> Grouped waterpoint type (redundant with 'waterpoint_type').
As a result, we shall drop them.

### Tabluea Dashboard

https://public.tableau.com/app/profile/victor.kigen3018/viz/VKIGEN-DSC-PHASE-3-PROJECT-TANZANIA-WATER-PUMPS-ANALYSIS/TanzaniaWaterPumpsanalysis?publish=yes


### Modeling

In order to design and build a logistict regression model, we first need to identify:

<b>1. Target Variable</b>

Considering the stated task is to building a classifier to predict the condition of a water well, our target variable would be the `status_group`. This column displays the condition of the water well.

<b>2. Independent Variables (Features)</b>

The water pump is affected by a magnitude of features. The numerical features are as follows: 

- `amount_tsh`
- `gps_height`
- `longitude`
- `latitude`
- `population`
- `age`
- `population`
- `district_code`

Categorical features include: 

- `funder`
- `installer`
- `basin`
- `region`
- `scheme_management`
- `permit`
- `extraction_type`
- `management`
- `payment`
- `water_quality`
- `source`

We've already performed one hot encoding on the categorical features, so we can go ahead and split the data into two sets. One for training and one for testing. 

Upon creating the first model, the results are shown below:


The output from the classification report and confusion matrix suggests that your model is not performing well on the minority classes (specifically, "functional needs repair" and "non functional"). This is a common issue in imbalanced datasets. In order to solve this we can:

Resampling techniques like SMOTE (Synthetic Minority Over-sampling Technique) to balance the class distribution.