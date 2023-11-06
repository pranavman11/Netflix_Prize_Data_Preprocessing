# Netflix Prize Data Preprocessing

### Dataset description
We are using the [Netflix Prize dataset](https://www.kaggle.com/datasets/netflix-inc/netflix-prize-data/data) available on Kaggle. This dataset consists of four .txt files of half GB that contain data about MovieId, CustomerId, and the ratings customers have given to that movie. There are multiple data groups for each movie. The first line of each data group of a movie starts with the movie ID followed by a colon. Each subsequent line corresponds to a rating from a customer and a date on which the rating is given in the following format: CustomerID, Rating, Date. Similarly, multiple such groups are stored in each file for other movie IDs.
- MovieIDs range from 1 to 17770 sequentially.
- CustomerIDs range from 1 to 2649429, with gaps. There are 480189 users.
- Ratings are on a five-star (integral) scale from 1 to 5.
- Dates have the format YYYY-MM-DD

### Data pre-processing procedure
All the data is stored in four .txt files which are not straightforward to handle as there is no schema. First, we converted all of the data from these files into a .csv file with MovieId as a separate column. All files have a similar structure, so we arranged the data with columns namely CustomerId, MovieId, Rating, and Date, and each row will contain information about the rating the customer gave to a movie on a particular date.

To reduce the size of the data and improve the data quality, we deleted entries of customers who have rated fewer movies and entries of movies with fewer reviews. This reduced the initial size by 3x. The dataset also contained duplicate data, we dropped all the duplicate rows.

The rating system has personal bias as one person can be conservative about their rating and the highest rating they give is 3, however, another person can be very generous and the highest rating they give to a movie is 5. This can result in flawed similarity measures. To reduce this, we have normalized our data on the rating column using the Z-score normalization
- Number of features: 4 (CustomerId, MovieId, Rating, Date)
- Number of rows after removing sparse and duplicate data: 2,58,89,858 
- Pre-processing procedure: Data loading, Data cleaning, Normalization 

### Raw data after loading

<img width="339" alt="netflix-raw-data" src="https://github.com/pranavman11/Netflix_Prize_Data_Preprocessing/assets/42564227/131111a3-191c-443e-b264-d78f33aa3dfc">

### Normalized tabular data

<img width="482" alt="netflix-normalized-data" src="https://github.com/pranavman11/Netflix_Prize_Data_Preprocessing/assets/42564227/48db0002-dc09-4de7-b67f-848d81e229d2">

#### Before running the .py file
Before running the code download the dataset from the link in Readme.md and save the dataset in /content/netflix-prize-data directory
