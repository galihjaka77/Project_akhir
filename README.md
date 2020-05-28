# Project Akhir Job Connector Data Science "Used Car Price Prediction"
by Jaka Galih Febrian

# 1. Dataset and Data Cleaning
Context

Craigslist is the world's largest collection of used vehicles for sale, yet it's very difficult to collect all of them in the same place. I found this dataset from kaggle.com whici is this dataset built from a scraper for a school project and expanded upon it later to create this dataset which includes every used vehicle entry within the United States on Craigslist.

Content

This data is scraped every few months, it contains most all relevant information that Craigslist provides on car sales including columns like price, condition, manufacturer, latitude/longitude, and 18 other categories. For ML projects, consider feature engineering on location columns such as long/lat. For previous listings, check older versions of the dataset.

Feature in dataset:

1. id = entry ID
2. url = listing URL
3. region = craigslist region
4. region_ur = lregion URL
5. price = entry price
6. year = entry year
7. manufacturer = manufacturer of vehicle
8. model = model of vehicle
9. condition = condition of vehicle
10. cylinders = number of cylinders
11. fuel = fuel type
12. odometer = miles traveled by vehicle
13. title_status = title status of vehicle
14. transmission = transmission of vehicle
15. vinvehicle id = entification number
16. drive = type of drive
17. size = size of vehicle
18. type = generic type of vehicle
19. paint_color = color of vehicle
20. image_url = image URL
21. description = listed description of vehicle
22. county = useless column left in by mistake
23. state = state of listing
24. lat = latitude of listing
25. long = longitude of listing

we can see the df.info() and null values in dataframe:
1. dataframe info:

![dataframe info](./gambar/gambar1_info_data.png)

2. null values:

![null info](./gambar/gambar1_info_null.png)

<b>after that i make a new data frame:</b>

![new dataframe](./gambar/gambar1_new_dataframe.png)

![new dataframe1](./gambar/gambar1_new_dataframe1.png)

this is the final dataset after doing data cleaning:

![new dataframe2](./gambar/gambar1_finaldataset.png)

# 2. Data Preprocessing
before make a machine learning your dataset must be numerical type, because machine learning can only process data type numerical. i change data type from my dataset using pd.get_dummies.

![new dataframe dummies](./gambar/gambar1_data_features.png)

# 3. Modeling
i was try LinearRegression, Ridge, Lasso, DecisionTreeRegressor, RandomForestRegressor, and XGBRegressor.
we can see the comparison table of all models:
| Model                     |        MAE         |          MSE          |        RMSE         |         R2Score         |
|---------------------------|--------------------|-----------------------|---------------------|-------------------------|
|LinearRegression           | 10959964598611.639 | 1.390472441290668e+29 | 372890391575147.44  | -1.4950759434565916e+21 |
|Ridge                      | 5167.735564747135  |   51118256.0698117    |  7149.703215505641  |   0.45036181479088266   |
|Lasso                      | 5167.994400569772  |   51112882.454225294  |  71.88876407735614  |    0.4504195934505242   |
|DecisionTreeRegressor      | 3545.413238602576  |   46313472.953224204  |  59.54337275131949  |    0.502024224183682    |
|RandomForestRegressor      | 3137.5482317382694 |   28962579.153778754  |  56.01382179193158  |    0.6885860225098832   |
|XGBRegressor               | 3296.442799968624  |   29361057.822966177  |  57.41465666507659  |    0.6843014653004665   |

but from all model i found the best model is RandomForestRegressor, but the R2Score is still bad it's 0.6885860225098832. so i doing Hyper-parameter optimization using GridSearchCV.

# 4. Hyper-parameter optimization
We have RandomForestRegressor for the best model. but we know that we can doing optimization for hyper-parameter so i use GridSearchCV to increase accuracy from my best model.

![GridSearchCV](./gambar/gambar1_result_random_and_GridSearchCV.png)

from picture above my model accuracy incrace to 0.6910669829544902.
