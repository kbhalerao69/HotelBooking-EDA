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
 
 ## Data analysis For Total Reservation Status Count
 
 - cancel_per = A1['is_canceled'].value_counts(normalize=True)
 - print(cancel_per)
 
 - plt.figure(figsize = (5,4))
 - plt.title('Reservation status count')
 - plt.bar(['Not Cancelled','Cancelled'],A1['is_canceled'].value_counts(),edgecolor = 'r' , width = 0.7)
 - plt.show()
 
 ## Reservation Status For Different Hotel
 
 - plt.figure(figsize=(8,4))
 - sea= sns.countplot( x= 'Hotel' , hue= 'is_canceled', data= A1 , palette = 'Blues')
 - legend_labels = sea. get_legend_handles_labels()
 - plt.title('Reservation status in different hotels', size= 20)
 - plt.xlabel('hotel')
 - plt.ylabel('number of reservations')
 - plt.show()

## Added Extra Month column to check reservation according Montly
 - A1['Month']=A1['reservation_status_date'].dt.month

## Reservation per Month
 - A1['Month']
 - plt.figure(figsize= (16,8))
 - sea = sns.countplot(x= 'Month', hue = 'is_canceled' , data = A1 , palette = 'bright')
 - legend_labels = sea. get_legend_handles_labels()
 - plt.title('Reservation per Month', size= 20)
 - plt.xlabel('Month')
 - plt.ylabel('number of reservations')
 - plt.legend(['not canceled','canceled'])
 - plt.show()
 
 
 ## Top 10 Countries with reservation canceled
 - canceled_data = A1[A1['is_canceled'] == 1]
 - top_10_country = canceled_data['country'].value_counts()[:10]
 - plt.figure(figsize= (8,8))
 - plt.title('Top 10 countries with reservation cancelled')
 - plt.pie(top_10_country,autopct ='%2f', labels = top_10_country.index)
 - plt.show()

 ## Checking Booking Reservation by different market segments
 
- A1['market_segment'].value_counts()
- 
- canceled_data = A1[A1['is_canceled'] == 1]
- canceled_data['market_segment'].value_counts(normalize=True)
- 
- not_canceled_data =  A1[A1['is_canceled'] == 0]
- not_canceled_data['market_segment'].value_counts(normalize=True)

## Average Daily Rate for Year 2017
- canceled_adr = canceled_data.groupby('reservation_status_date')[['adr']].mean()
- canceled_adr.reset_index(inplace=True)
- canceled_adr.sort_values('reservation_status_date',inplace=True)

- not_canceled_adr = not_canceled_data.groupby('reservation_status_date')[['adr']].mean()
- not_canceled_adr.reset_index(inplace=True)
- not_canceled_adr.sort_values('reservation_status_date',inplace=True)

- canceled1=canceled_adr[(canceled_adr['reservation_status_date']> '2017') & (canceled_adr['reservation_status_date'] < '2017-09')]
- not_canceled1= not_canceled_adr[(not_canceled_adr['reservation_status_date']> '2017') & (not_canceled_adr['reservation_status_date'] < '2017-09')]


- plt.figure(figsize = (20,6))
- plt.title('Average Daily Rate')
- plt.plot(not_canceled1['reservation_status_date'],not_canceled1['adr'],label= 'Not Canceled')
- plt.plot(canceled1['reservation_status_date'],canceled1['adr'],label= 'Canceled')
- plt.legend(fontsize = 20)
- plt.show()
