# HotelBooking-EDA




# Objective:
To Extract some interesting Analysis/Insights from the HotelBooking Dataset



## Technologies Used:
**Programming Language:** Python

**Software used:** Jupyter NoteBook and Microsoft Excel 



## Data Cleaning Process : 

### In Microsoft Excel:
- Deleted Duplicate rows and dropped columns like Name, Email , Phone-number, Agent, Company and Credit-cards which are not required.





### In Jupyter Notebook:
- imported Libraries like Numpy and Pandas for Data Analysis
- imported Libraries like Seaborn and Matplotlib for Data Visualisation

## Following are step for required Data analysis

## Loading CSV file
- A1=pd.read_csv(r'C:\Users\kunal\Desktop\coding\Python\hotel_booking.csv',encoding='utf-8')   
- 
## Checking shape of dataset and columns present in it                
- A1.shape and A1.columns    

## Converted Selected column into datetime format                                                                                 
- A1['reservation_status_date']=pd.to_datetime(A1['reservation_status_date'])   

## Checking object datatype present in Dataset
- A1.describe(include=object)

## Using FOR loop for columns to display unique Values
- for col in A1.describe(include='object').columns:
    print(col)
    print(A1[col].unique())
    print('-'*60)
    
 ## checking and Deleting Null values
 - A1.isnull().sum()
 - A1.dropna(inplace=True)
 - A1.describe()                 ## For Confirmation
 -  
