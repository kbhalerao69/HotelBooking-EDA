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
-A1=pd.read_csv(r'C:\Users\kunal\Desktop\coding\Python\hotel_booking.csv',encoding='utf-8')  ## Loading CSV file
- A1.shape and A1.columns ## Checking shape of dataset and columns present in it
