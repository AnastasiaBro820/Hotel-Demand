```python
# Loading Data
```


```python
import pandas as pd
import numpy as n
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
import missingno
datapro=pd.read_csv('hotel_bookings.csv',header=0)
hd=pd.DataFrame(datapro)
pd.set_option('display.max_columns', None)
datapro


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hotel</th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_month</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>children</th>
      <th>babies</th>
      <th>meal</th>
      <th>country</th>
      <th>market_segment</th>
      <th>distribution_channel</th>
      <th>is_repeated_guest</th>
      <th>previous_cancellations</th>
      <th>previous_bookings_not_canceled</th>
      <th>reserved_room_type</th>
      <th>assigned_room_type</th>
      <th>booking_changes</th>
      <th>deposit_type</th>
      <th>agent</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>customer_type</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
      <th>reservation_status</th>
      <th>reservation_status_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>342</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>PRT</td>
      <td>Direct</td>
      <td>Direct</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>C</td>
      <td>C</td>
      <td>3</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2015-07-01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>737</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>PRT</td>
      <td>Direct</td>
      <td>Direct</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>C</td>
      <td>C</td>
      <td>4</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>0.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2015-07-01</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>7</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>GBR</td>
      <td>Direct</td>
      <td>Direct</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>C</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2015-07-02</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>GBR</td>
      <td>Corporate</td>
      <td>Corporate</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>304.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>75.00</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2015-07-02</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>14</td>
      <td>2015</td>
      <td>July</td>
      <td>27</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>GBR</td>
      <td>Online TA</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>240.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>98.00</td>
      <td>0</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>2015-07-03</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>119385</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>23</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>30</td>
      <td>2</td>
      <td>5</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>BEL</td>
      <td>Offline TA/TO</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>394.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>96.14</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2017-09-06</td>
    </tr>
    <tr>
      <th>119386</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>102</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>31</td>
      <td>2</td>
      <td>5</td>
      <td>3</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>FRA</td>
      <td>Online TA</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>E</td>
      <td>E</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>225.43</td>
      <td>0</td>
      <td>2</td>
      <td>Check-Out</td>
      <td>2017-09-07</td>
    </tr>
    <tr>
      <th>119387</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>34</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>31</td>
      <td>2</td>
      <td>5</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>DEU</td>
      <td>Online TA</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>D</td>
      <td>D</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>157.71</td>
      <td>0</td>
      <td>4</td>
      <td>Check-Out</td>
      <td>2017-09-07</td>
    </tr>
    <tr>
      <th>119388</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>109</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>31</td>
      <td>2</td>
      <td>5</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>GBR</td>
      <td>Online TA</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>89.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>104.40</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2017-09-07</td>
    </tr>
    <tr>
      <th>119389</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>205</td>
      <td>2017</td>
      <td>August</td>
      <td>35</td>
      <td>29</td>
      <td>2</td>
      <td>7</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>HB</td>
      <td>DEU</td>
      <td>Online TA</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>NaN</td>
      <td>0</td>
      <td>Transient</td>
      <td>151.20</td>
      <td>0</td>
      <td>2</td>
      <td>Check-Out</td>
      <td>2017-09-07</td>
    </tr>
  </tbody>
</table>
<p>119390 rows × 32 columns</p>
</div>




```python
# Clearing Data
```


```python
hd.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 119390 entries, 0 to 119389
    Data columns (total 32 columns):
     #   Column                          Non-Null Count   Dtype  
    ---  ------                          --------------   -----  
     0   hotel                           119390 non-null  object 
     1   is_canceled                     119390 non-null  int64  
     2   lead_time                       119390 non-null  int64  
     3   arrival_date_year               119390 non-null  int64  
     4   arrival_date_month              119390 non-null  object 
     5   arrival_date_week_number        119390 non-null  int64  
     6   arrival_date_day_of_month       119390 non-null  int64  
     7   stays_in_weekend_nights         119390 non-null  int64  
     8   stays_in_week_nights            119390 non-null  int64  
     9   adults                          119390 non-null  int64  
     10  children                        119386 non-null  float64
     11  babies                          119390 non-null  int64  
     12  meal                            119390 non-null  object 
     13  country                         118902 non-null  object 
     14  market_segment                  119390 non-null  object 
     15  distribution_channel            119390 non-null  object 
     16  is_repeated_guest               119390 non-null  int64  
     17  previous_cancellations          119390 non-null  int64  
     18  previous_bookings_not_canceled  119390 non-null  int64  
     19  reserved_room_type              119390 non-null  object 
     20  assigned_room_type              119390 non-null  object 
     21  booking_changes                 119390 non-null  int64  
     22  deposit_type                    119390 non-null  object 
     23  agent                           103050 non-null  float64
     24  company                         6797 non-null    float64
     25  days_in_waiting_list            119390 non-null  int64  
     26  customer_type                   119390 non-null  object 
     27  adr                             119390 non-null  float64
     28  required_car_parking_spaces     119390 non-null  int64  
     29  total_of_special_requests       119390 non-null  int64  
     30  reservation_status              119390 non-null  object 
     31  reservation_status_date         119390 non-null  object 
    dtypes: float64(4), int64(16), object(12)
    memory usage: 29.1+ MB
    


```python
hd.isna().sum()
```




    hotel                                  0
    is_canceled                            0
    lead_time                              0
    arrival_date_year                      0
    arrival_date_month                     0
    arrival_date_week_number               0
    arrival_date_day_of_month              0
    stays_in_weekend_nights                0
    stays_in_week_nights                   0
    adults                                 0
    children                               4
    babies                                 0
    meal                                   0
    country                              488
    market_segment                         0
    distribution_channel                   0
    is_repeated_guest                      0
    previous_cancellations                 0
    previous_bookings_not_canceled         0
    reserved_room_type                     0
    assigned_room_type                     0
    booking_changes                        0
    deposit_type                           0
    agent                              16340
    company                           112593
    days_in_waiting_list                   0
    customer_type                          0
    adr                                    0
    required_car_parking_spaces            0
    total_of_special_requests              0
    reservation_status                     0
    reservation_status_date                0
    dtype: int64




```python
hd = hd.dropna(subset=['company','agent','country'],axis=0)
hd
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hotel</th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_month</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>children</th>
      <th>babies</th>
      <th>meal</th>
      <th>country</th>
      <th>market_segment</th>
      <th>distribution_channel</th>
      <th>is_repeated_guest</th>
      <th>previous_cancellations</th>
      <th>previous_bookings_not_canceled</th>
      <th>reserved_room_type</th>
      <th>assigned_room_type</th>
      <th>booking_changes</th>
      <th>deposit_type</th>
      <th>agent</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>customer_type</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
      <th>reservation_status</th>
      <th>reservation_status_date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2392</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>6</td>
      <td>2015</td>
      <td>October</td>
      <td>42</td>
      <td>11</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>PRT</td>
      <td>Online TA</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>E</td>
      <td>E</td>
      <td>1</td>
      <td>No Deposit</td>
      <td>240.0</td>
      <td>113.0</td>
      <td>0</td>
      <td>Transient</td>
      <td>82.0</td>
      <td>1</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>2015-10-13</td>
    </tr>
    <tr>
      <th>2697</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>24</td>
      <td>2015</td>
      <td>October</td>
      <td>44</td>
      <td>26</td>
      <td>7</td>
      <td>15</td>
      <td>1</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>AUT</td>
      <td>Corporate</td>
      <td>Corporate</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>E</td>
      <td>G</td>
      <td>2</td>
      <td>No Deposit</td>
      <td>185.0</td>
      <td>281.0</td>
      <td>0</td>
      <td>Transient-Party</td>
      <td>52.2</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2015-11-17</td>
    </tr>
    <tr>
      <th>2867</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>24</td>
      <td>2015</td>
      <td>November</td>
      <td>45</td>
      <td>3</td>
      <td>0</td>
      <td>3</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>ESP</td>
      <td>Corporate</td>
      <td>Corporate</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>1</td>
      <td>No Deposit</td>
      <td>334.0</td>
      <td>281.0</td>
      <td>0</td>
      <td>Transient-Party</td>
      <td>48.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2015-11-06</td>
    </tr>
    <tr>
      <th>2877</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>24</td>
      <td>2015</td>
      <td>November</td>
      <td>45</td>
      <td>3</td>
      <td>2</td>
      <td>10</td>
      <td>1</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>PRT</td>
      <td>Corporate</td>
      <td>Corporate</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>2</td>
      <td>No Deposit</td>
      <td>328.0</td>
      <td>281.0</td>
      <td>0</td>
      <td>Transient-Party</td>
      <td>40.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2015-11-15</td>
    </tr>
    <tr>
      <th>2878</th>
      <td>Resort Hotel</td>
      <td>0</td>
      <td>24</td>
      <td>2015</td>
      <td>November</td>
      <td>45</td>
      <td>3</td>
      <td>3</td>
      <td>10</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>ITA</td>
      <td>Corporate</td>
      <td>Corporate</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>2</td>
      <td>No Deposit</td>
      <td>326.0</td>
      <td>281.0</td>
      <td>0</td>
      <td>Transient-Party</td>
      <td>48.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2015-11-16</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>112499</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2017</td>
      <td>May</td>
      <td>21</td>
      <td>24</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>CHN</td>
      <td>Online TA</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>478.0</td>
      <td>0</td>
      <td>Transient-Party</td>
      <td>150.0</td>
      <td>0</td>
      <td>1</td>
      <td>Check-Out</td>
      <td>2017-05-25</td>
    </tr>
    <tr>
      <th>113046</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2017</td>
      <td>May</td>
      <td>22</td>
      <td>29</td>
      <td>1</td>
      <td>3</td>
      <td>1</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>ITA</td>
      <td>Offline TA/TO</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>1</td>
      <td>No Deposit</td>
      <td>290.0</td>
      <td>148.0</td>
      <td>0</td>
      <td>Transient</td>
      <td>95.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2017-06-02</td>
    </tr>
    <tr>
      <th>113082</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>13</td>
      <td>2017</td>
      <td>May</td>
      <td>22</td>
      <td>29</td>
      <td>1</td>
      <td>3</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>ITA</td>
      <td>Offline TA/TO</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>A</td>
      <td>A</td>
      <td>1</td>
      <td>No Deposit</td>
      <td>290.0</td>
      <td>148.0</td>
      <td>0</td>
      <td>Transient</td>
      <td>110.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2017-06-02</td>
    </tr>
    <tr>
      <th>113627</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>210</td>
      <td>2017</td>
      <td>June</td>
      <td>23</td>
      <td>9</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>GBR</td>
      <td>Direct</td>
      <td>Direct</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>D</td>
      <td>D</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>14.0</td>
      <td>229.0</td>
      <td>0</td>
      <td>Transient</td>
      <td>135.0</td>
      <td>0</td>
      <td>0</td>
      <td>Check-Out</td>
      <td>2017-06-10</td>
    </tr>
    <tr>
      <th>116451</th>
      <td>City Hotel</td>
      <td>0</td>
      <td>191</td>
      <td>2017</td>
      <td>July</td>
      <td>29</td>
      <td>16</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>0.0</td>
      <td>0</td>
      <td>BB</td>
      <td>PRT</td>
      <td>Online TA</td>
      <td>TA/TO</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>D</td>
      <td>D</td>
      <td>0</td>
      <td>No Deposit</td>
      <td>9.0</td>
      <td>421.0</td>
      <td>0</td>
      <td>Transient</td>
      <td>120.6</td>
      <td>0</td>
      <td>2</td>
      <td>Check-Out</td>
      <td>2017-07-20</td>
    </tr>
  </tbody>
</table>
<p>217 rows × 32 columns</p>
</div>




```python
hd.isna().sum()
```




    hotel                             0
    is_canceled                       0
    lead_time                         0
    arrival_date_year                 0
    arrival_date_month                0
    arrival_date_week_number          0
    arrival_date_day_of_month         0
    stays_in_weekend_nights           0
    stays_in_week_nights              0
    adults                            0
    children                          0
    babies                            0
    meal                              0
    country                           0
    market_segment                    0
    distribution_channel              0
    is_repeated_guest                 0
    previous_cancellations            0
    previous_bookings_not_canceled    0
    reserved_room_type                0
    assigned_room_type                0
    booking_changes                   0
    deposit_type                      0
    agent                             0
    company                           0
    days_in_waiting_list              0
    customer_type                     0
    adr                               0
    required_car_parking_spaces       0
    total_of_special_requests         0
    reservation_status                0
    reservation_status_date           0
    dtype: int64




```python
missingno.matrix(hd)
```




    <Axes: >




    
![png](project_files/project_7_1.png)
    



```python
hd.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Index: 217 entries, 2392 to 116451
    Data columns (total 32 columns):
     #   Column                          Non-Null Count  Dtype  
    ---  ------                          --------------  -----  
     0   hotel                           217 non-null    object 
     1   is_canceled                     217 non-null    int64  
     2   lead_time                       217 non-null    int64  
     3   arrival_date_year               217 non-null    int64  
     4   arrival_date_month              217 non-null    object 
     5   arrival_date_week_number        217 non-null    int64  
     6   arrival_date_day_of_month       217 non-null    int64  
     7   stays_in_weekend_nights         217 non-null    int64  
     8   stays_in_week_nights            217 non-null    int64  
     9   adults                          217 non-null    int64  
     10  children                        217 non-null    float64
     11  babies                          217 non-null    int64  
     12  meal                            217 non-null    object 
     13  country                         217 non-null    object 
     14  market_segment                  217 non-null    object 
     15  distribution_channel            217 non-null    object 
     16  is_repeated_guest               217 non-null    int64  
     17  previous_cancellations          217 non-null    int64  
     18  previous_bookings_not_canceled  217 non-null    int64  
     19  reserved_room_type              217 non-null    object 
     20  assigned_room_type              217 non-null    object 
     21  booking_changes                 217 non-null    int64  
     22  deposit_type                    217 non-null    object 
     23  agent                           217 non-null    float64
     24  company                         217 non-null    float64
     25  days_in_waiting_list            217 non-null    int64  
     26  customer_type                   217 non-null    object 
     27  adr                             217 non-null    float64
     28  required_car_parking_spaces     217 non-null    int64  
     29  total_of_special_requests       217 non-null    int64  
     30  reservation_status              217 non-null    object 
     31  reservation_status_date         217 non-null    object 
    dtypes: float64(4), int64(16), object(12)
    memory usage: 55.9+ KB
    


```python
hd.arrival_date_year.describe()
```




    count     217.000000
    mean     2015.465438
    std         0.720053
    min      2015.000000
    25%      2015.000000
    50%      2015.000000
    75%      2016.000000
    max      2017.000000
    Name: arrival_date_year, dtype: float64




```python
hd.arrival_date_week_number.describe()
```




    count    217.000000
    mean      38.198157
    std       12.890292
    min        1.000000
    25%       33.000000
    50%       45.000000
    75%       46.000000
    max       53.000000
    Name: arrival_date_week_number, dtype: float64




```python
hd.lead_time .describe()
```




    count    217.000000
    mean      40.520737
    std       61.748375
    min        0.000000
    25%       12.000000
    50%       27.000000
    75%       36.000000
    max      364.000000
    Name: lead_time, dtype: float64




```python
# Analytics
```


```python
## Descriptive statistics
```


```python
hd.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>is_canceled</th>
      <th>lead_time</th>
      <th>arrival_date_year</th>
      <th>arrival_date_week_number</th>
      <th>arrival_date_day_of_month</th>
      <th>stays_in_weekend_nights</th>
      <th>stays_in_week_nights</th>
      <th>adults</th>
      <th>children</th>
      <th>babies</th>
      <th>is_repeated_guest</th>
      <th>previous_cancellations</th>
      <th>previous_bookings_not_canceled</th>
      <th>booking_changes</th>
      <th>agent</th>
      <th>company</th>
      <th>days_in_waiting_list</th>
      <th>adr</th>
      <th>required_car_parking_spaces</th>
      <th>total_of_special_requests</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.00000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.0</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.0</td>
      <td>217.000000</td>
      <td>217.000000</td>
      <td>217.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.078341</td>
      <td>40.520737</td>
      <td>2015.465438</td>
      <td>38.198157</td>
      <td>10.824885</td>
      <td>1.56682</td>
      <td>4.631336</td>
      <td>1.410138</td>
      <td>0.036866</td>
      <td>0.0</td>
      <td>0.069124</td>
      <td>0.009217</td>
      <td>0.147465</td>
      <td>1.285714</td>
      <td>202.617512</td>
      <td>262.105991</td>
      <td>0.0</td>
      <td>63.793733</td>
      <td>0.092166</td>
      <td>0.198157</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.269329</td>
      <td>61.748375</td>
      <td>0.720053</td>
      <td>12.890292</td>
      <td>7.582065</td>
      <td>1.49270</td>
      <td>3.552846</td>
      <td>0.520406</td>
      <td>0.232788</td>
      <td>0.0</td>
      <td>0.254252</td>
      <td>0.135769</td>
      <td>0.717768</td>
      <td>1.251454</td>
      <td>111.487444</td>
      <td>103.602708</td>
      <td>0.0</td>
      <td>38.823568</td>
      <td>0.289929</td>
      <td>0.546365</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2015.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>0.00000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>5.000000</td>
      <td>9.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.000000</td>
      <td>12.000000</td>
      <td>2015.000000</td>
      <td>33.000000</td>
      <td>6.000000</td>
      <td>0.00000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>185.000000</td>
      <td>281.000000</td>
      <td>0.0</td>
      <td>40.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.000000</td>
      <td>27.000000</td>
      <td>2015.000000</td>
      <td>45.000000</td>
      <td>9.000000</td>
      <td>2.00000</td>
      <td>4.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>185.000000</td>
      <td>281.000000</td>
      <td>0.0</td>
      <td>48.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.000000</td>
      <td>36.000000</td>
      <td>2016.000000</td>
      <td>46.000000</td>
      <td>13.000000</td>
      <td>2.00000</td>
      <td>6.000000</td>
      <td>2.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.000000</td>
      <td>324.000000</td>
      <td>281.000000</td>
      <td>0.0</td>
      <td>85.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.000000</td>
      <td>364.000000</td>
      <td>2017.000000</td>
      <td>53.000000</td>
      <td>31.000000</td>
      <td>9.00000</td>
      <td>21.000000</td>
      <td>3.000000</td>
      <td>2.000000</td>
      <td>0.0</td>
      <td>1.000000</td>
      <td>2.000000</td>
      <td>7.000000</td>
      <td>6.000000</td>
      <td>444.000000</td>
      <td>499.000000</td>
      <td>0.0</td>
      <td>246.000000</td>
      <td>1.000000</td>
      <td>3.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
hd.is_canceled.mean()
```




    np.float64(0.07834101382488479)




```python
hd.required_car_parking_spaces.mean()
```




    np.float64(0.09216589861751152)




```python
import plotly.express as px
fig = px.histogram(hd, x="country",nbins=30,title='Country Distribution')
fig.update_layout(xaxis_title='Country',yaxis_title='Distribution')
fig.show()

```


<div>                            <div id="a89e39c2-b0f0-49bb-8cfa-aa30c0f273e5" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                require(["plotly"], function(Plotly) {                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("a89e39c2-b0f0-49bb-8cfa-aa30c0f273e5")) {                    Plotly.newPlot(                        "a89e39c2-b0f0-49bb-8cfa-aa30c0f273e5",                        [{"alignmentgroup":"True","bingroup":"x","hovertemplate":"country=%{x}\u003cbr\u003ecount=%{y}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":"#636efa","pattern":{"shape":""}},"name":"","nbinsx":30,"offsetgroup":"","orientation":"v","showlegend":false,"x":["PRT","AUT","ESP","PRT","ITA","ITA","ESP","ITA","ITA","FRA","FRA","PRT","PRT","PRT","FRA","AUT","AUT","AUT","AUT","FRA","AUT","DEU","PRT","DEU","BEL","CZE","GBR","DEU","DEU","AUT","FRA","PRT","PRT","FRA","PRT","PRT","PRT","PRT","PRT","PRT","PRT","ESP","PRT","PRT","ESP","DEU","PRT","AUT","FRA","FRA","FRA","FRA","PRT","PRT","FRA","PRT","FRA","NLD","FRA","PRT","PRT","PRT","PRT","ESP","PRT","ITA","PRT","GBR","PRT","PRT","ITA","PRT","PRT","ITA","PRT","AUT","PRT","PRT","ESP","PRT","PRT","AUT","USA","AUT","PRT","GBR","ITA","ITA","FRA","GBR","PRT","BEL","MEX","ITA","PRT","PRT","AUT","AUT","AUT","AUT","AUT","AUT","PRT","AUT","AUT","GBR","AUT","AUT","AUT","GBR","DEU","AUT","AUT","AUT","PRT","PRT","CZE","GBR","FRA","GBR","PRT","CZE","USA","CZE","CHE","FRA","FRA","FRA","FRA","DEU","FRA","AUT","AUT","PRT","AUT","AUT","AUT","AUS","PRT","PRT","PRT","PRT","PRT","PRT","PRT","PRT","PRT","GBR","PRT","GBR","GBR","GBR","PRT","PRT","PRT","PRT","PRT","PRT","BGR","PRT","PRT","PRT","ITA","PRT","NLD","GBR","GBR","GBR","GBR","GBR","PRT","PRT","FRA","ITA","FRA","FRA","FRA","PRT","PRT","FRA","PRT","PRT","PRT","PRT","PRT","PRT","ITA","ITA","GBR","CHN","MEX","PRT","DEU","DEU","DEU","DEU","DEU","DEU","DEU","DEU","DEU","BEL","PRT","DEU","ROU","PRT","IRL","PRT","PRT","PRT","ESP","ESP","CHN","ITA","ITA","GBR","PRT"],"xaxis":"x","yaxis":"y","type":"histogram"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Country"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Distribution"}},"legend":{"tracegroupgap":0},"title":{"text":"Country Distribution"},"barmode":"relative"},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('a89e39c2-b0f0-49bb-8cfa-aa30c0f273e5');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{ x.observe(notebookContainer, {childList: true}) }}


// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                });            </script>        </div>



```python
import plotly.express as px
fig = px.histogram(hd, x="arrival_date_month",nbins=30,title='Month Distribution')
fig.update_layout(xaxis_title='Month',yaxis_title='Distribution')
fig.show()
```


<div>                            <div id="d538445a-a7fd-4c6d-a470-79f85de17cd2" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                require(["plotly"], function(Plotly) {                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("d538445a-a7fd-4c6d-a470-79f85de17cd2")) {                    Plotly.newPlot(                        "d538445a-a7fd-4c6d-a470-79f85de17cd2",                        [{"alignmentgroup":"True","bingroup":"x","hovertemplate":"arrival_date_month=%{x}\u003cbr\u003ecount=%{y}\u003cextra\u003e\u003c\u002fextra\u003e","legendgroup":"","marker":{"color":"#636efa","pattern":{"shape":""}},"name":"","nbinsx":30,"offsetgroup":"","orientation":"v","showlegend":false,"x":["October","October","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","May","October","June","December","January","October","October","January","May","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","November","October","November","October","November","November","October","November","March","November","January","May","February","March","April","May","May","May","May","May","May","July","July","August","September","November","November","December","December","January","January","January","January","March","March","June","June","July","August","August","August","August","August","August","August","August","August","August","August","August","September","January","August","October","January","January","May","May","July","September","September","September","October","October","October","October","October","October","October","October","October","November","November","December","December","January","February","March","May","May","May","May","May","May","May","June","July"],"xaxis":"x","yaxis":"y","type":"histogram"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Month"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Distribution"}},"legend":{"tracegroupgap":0},"title":{"text":"Month Distribution"},"barmode":"relative"},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('d538445a-a7fd-4c6d-a470-79f85de17cd2');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                });            </script>        </div>



```python
plt.figure(figsize=(10, 6))
sns.countplot(x='hotel', data=hd,hue='hotel')
plt.title('Hotel Type', fontsize=16)
plt.xlabel('Hotel Type', fontsize=12)
plt.ylabel('Distribution', fontsize=12)
plt.xticks(rotation=45)
plt.show()
```


    
![png](project_files/project_19_0.png)
    



```python
plt.figure(figsize=(10, 3))
sns.boxplot(x=hd['lead_time'], color='black')
plt.title('Amount Of Day To Stay', fontsize=15)
plt.xlabel('Days', fontsize=10)
plt.show()
```


    
![png](project_files/project_20_0.png)
    



```python
plt.figure(figsize=(15, 6))
sns.scatterplot(data=hd, x='arrival_date_month', y='country', hue='is_canceled', alpha=0.7)
plt.title('Country and Month', fontsize=16)
plt.xlabel('Month', fontsize=12)
plt.ylabel('Country', fontsize=12)
plt.legend(title='Status')
plt.grid(alpha=1)
plt.show()
```


    
![png](project_files/project_21_0.png)
    



```python

```


```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(12, 6))
sns.histplot(data=hd, x='arrival_date_year', hue='is_canceled', kde=True, bins=60)
plt.title('Year Distribution', fontsize=18)
plt.xticks([2015,2016,2017])
plt.xlabel('Year', fontsize=12)
plt.ylabel('Amount', fontsize=12)
plt.show()
```


    
![png](project_files/project_23_0.png)
    



```python
# Hypothesis
```


```python
# The best time to go to Europe in Resort Hotel is in summer, while City Hotels are popular in the colder seasons.
```


```python
df=hd
countries = pd.DataFrame(df['country'].value_counts().sort_values())
countries['country_name'] = countries.index
countries.reset_index(drop=True, inplace=True)

top_countries = countries['country_name'].loc[countries.shape[0] - 5:].values


agg_hd = df.groupby(['arrival_date_month', 'country', 'hotel', 'is_canceled']).size().reset_index(name='count'); agg_hd
fig = px.sunburst(agg_hd[agg_hd['country'].isin(top_countries)], path=['country', 'hotel', 'arrival_date_month', 'count'], color='is_canceled')
fig.update_layout(hovermode=False)
fig.show()
```


<div>                            <div id="869c2d95-df36-4367-a148-5b4d5440625a" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                require(["plotly"], function(Plotly) {                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("869c2d95-df36-4367-a148-5b4d5440625a")) {                    Plotly.newPlot(                        "869c2d95-df36-4367-a148-5b4d5440625a",                        [{"branchvalues":"total","customdata":[[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[0.0],[1.0],[1.0],[1.0],[0.0],[1.0],[1.0],[0.0],[1.0],[1.0],[1.0],[1.0],[0.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[0.0],[0.0],[0.0],[1.0],[1.0],[1.0],[0.0],[1.0],[1.0],[0.0],[0.0],[1.0],[0.0],[1.0],[0.0],[1.0],[1.0],[1.0],[1.0],[1.0],[0.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[0.0],[0.0],[1.0],[0.0],[1.0],[0.0],[0.0],[0.0],[1.0],[1.0],[1.0],[1.0],[0.0],[0.0],[1.0],[0.0],[1.0],[1.0],[0.0],[1.0],[1.0],[1.0],[1.0],[1.0],[0.0],[1.0],[0.0],[1.0],[0.0],[1.0],[0.0],[0.0],[0.0],[0.0],[1.0],[1.0],[0.0],[1.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[1.0],[0.0],[1.0],[0.0],[1.0],[1.0],[0.0],[1.0],[0.0],[1.0],[1.0],[0.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[1.0],[0.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[0.0],[1.0],[1.0],[1.0],[0.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[0.0],[0.0],[1.0],[0.0],[0.0],[1.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[0.0],[0.0],[0.0],[1.0],[0.0],[0.0],[0.0],[1.0],[0.0],[1.0],[0.0],[0.0],[1.0],[0.0],[1.0],[0.0],[0.0],[0.0],[1.0],[0.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[1.0],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5],[0.5]],"domain":{"x":[0.0,1.0],"y":[0.0,1.0]},"hovertemplate":"labels=%{label}\u003cbr\u003ecountryhotelarrival_date_monthcountis_canceledcount_path_copyarrival_date_month_path_copyhotel_path_copycountry_path_copy=%{value}\u003cbr\u003eparent=%{parent}\u003cbr\u003eid=%{id}\u003cbr\u003eis_canceled=%{color}\u003cextra\u003e\u003c\u002fextra\u003e","ids":["DEU\u002fResort Hotel\u002fMarch\u002f3","DEU\u002fResort Hotel\u002fFebruary\u002f6","DEU\u002fResort Hotel\u002fJanuary\u002f7","DEU\u002fResort Hotel\u002fNovember\u002f7","FRA\u002fResort Hotel\u002fSeptember\u002f7","DEU\u002fResort Hotel\u002fDecember\u002f8","FRA\u002fResort Hotel\u002fNovember\u002f8","FRA\u002fResort Hotel\u002fJanuary\u002f10","FRA\u002fResort Hotel\u002fJune\u002f10","DEU\u002fResort Hotel\u002fSeptember\u002f11","DEU\u002fResort Hotel\u002fJuly\u002f12","DEU\u002fResort Hotel\u002fOctober\u002f12","FRA\u002fResort Hotel\u002fOctober\u002f12","FRA\u002fResort Hotel\u002fMarch\u002f13","FRA\u002fResort Hotel\u002fFebruary\u002f15","DEU\u002fResort Hotel\u002fApril\u002f16","DEU\u002fResort Hotel\u002fJune\u002f16","ESP\u002fResort Hotel\u002fJanuary\u002f19","FRA\u002fResort Hotel\u002fDecember\u002f21","ESP\u002fResort Hotel\u002fNovember\u002f21","ESP\u002fResort Hotel\u002fMarch\u002f22","FRA\u002fResort Hotel\u002fApril\u002f23","DEU\u002fResort Hotel\u002fMay\u002f23","FRA\u002fResort Hotel\u002fJuly\u002f24","FRA\u002fResort Hotel\u002fMay\u002f24","DEU\u002fResort Hotel\u002fAugust\u002f25","DEU\u002fCity Hotel\u002fJanuary\u002f29","GBR\u002fCity Hotel\u002fJanuary\u002f30","GBR\u002fResort Hotel\u002fJanuary\u002f30","ESP\u002fResort Hotel\u002fDecember\u002f34","DEU\u002fResort Hotel\u002fDecember\u002f36","ESP\u002fResort Hotel\u002fFebruary\u002f36","FRA\u002fCity Hotel\u002fNovember\u002f36","GBR\u002fResort Hotel\u002fDecember\u002f37","DEU\u002fResort Hotel\u002fJanuary\u002f37","ESP\u002fResort Hotel\u002fMay\u002f38","ESP\u002fResort Hotel\u002fSeptember\u002f38","DEU\u002fResort Hotel\u002fAugust\u002f39","ESP\u002fCity Hotel\u002fOctober\u002f43","FRA\u002fResort Hotel\u002fAugust\u002f44","ESP\u002fCity Hotel\u002fNovember\u002f44","GBR\u002fResort Hotel\u002fNovember\u002f44","DEU\u002fResort Hotel\u002fFebruary\u002f46","GBR\u002fResort Hotel\u002fFebruary\u002f46","GBR\u002fResort Hotel\u002fMarch\u002f46","GBR\u002fCity Hotel\u002fDecember\u002f47","DEU\u002fCity Hotel\u002fNovember\u002f47","DEU\u002fCity Hotel\u002fFebruary\u002f49","GBR\u002fCity Hotel\u002fNovember\u002f49","ESP\u002fCity Hotel\u002fSeptember\u002f50","DEU\u002fResort Hotel\u002fJuly\u002f51","FRA\u002fResort Hotel\u002fJune\u002f54","DEU\u002fResort Hotel\u002fJune\u002f56","DEU\u002fCity Hotel\u002fDecember\u002f59","ESP\u002fResort Hotel\u002fJune\u002f61","DEU\u002fCity Hotel\u002fSeptember\u002f61","DEU\u002fResort Hotel\u002fSeptember\u002f63","FRA\u002fCity Hotel\u002fJanuary\u002f67","ESP\u002fCity Hotel\u002fJanuary\u002f69","GBR\u002fCity Hotel\u002fDecember\u002f70","DEU\u002fResort Hotel\u002fNovember\u002f70","ESP\u002fCity Hotel\u002fFebruary\u002f71","FRA\u002fResort Hotel\u002fJuly\u002f71","GBR\u002fCity Hotel\u002fOctober\u002f71","DEU\u002fResort Hotel\u002fOctober\u002f71","FRA\u002fCity Hotel\u002fDecember\u002f73","DEU\u002fCity Hotel\u002fOctober\u002f73","GBR\u002fResort Hotel\u002fJuly\u002f74","GBR\u002fResort Hotel\u002fOctober\u002f77","ESP\u002fCity Hotel\u002fMay\u002f79","FRA\u002fResort Hotel\u002fJanuary\u002f81","ESP\u002fResort Hotel\u002fOctober\u002f88","ESP\u002fResort Hotel\u002fApril\u002f95","DEU\u002fCity Hotel\u002fJune\u002f96","GBR\u002fResort Hotel\u002fAugust\u002f97","GBR\u002fCity Hotel\u002fFebruary\u002f97","ESP\u002fCity Hotel\u002fJune\u002f99","GBR\u002fResort Hotel\u002fApril\u002f100","GBR\u002fResort Hotel\u002fJune\u002f102","FRA\u002fResort Hotel\u002fFebruary\u002f105","GBR\u002fCity Hotel\u002fJanuary\u002f105","FRA\u002fCity Hotel\u002fSeptember\u002f108","FRA\u002fResort Hotel\u002fMarch\u002f111","GBR\u002fCity Hotel\u002fSeptember\u002f112","ESP\u002fResort Hotel\u002fJune\u002f113","FRA\u002fResort Hotel\u002fOctober\u002f113","ESP\u002fResort Hotel\u002fMay\u002f114","DEU\u002fCity Hotel\u002fMarch\u002f116","GBR\u002fResort Hotel\u002fMay\u002f119","GBR\u002fResort Hotel\u002fSeptember\u002f119","DEU\u002fCity Hotel\u002fJuly\u002f123","FRA\u002fResort Hotel\u002fDecember\u002f124","DEU\u002fCity Hotel\u002fDecember\u002f125","FRA\u002fCity Hotel\u002fFebruary\u002f127","FRA\u002fResort Hotel\u002fApril\u002f129","FRA\u002fCity Hotel\u002fMarch\u002f135","DEU\u002fCity Hotel\u002fAugust\u002f137","FRA\u002fResort Hotel\u002fMay\u002f137","DEU\u002fCity Hotel\u002fApril\u002f138","FRA\u002fCity Hotel\u002fOctober\u002f138","GBR\u002fCity Hotel\u002fMarch\u002f139","ESP\u002fCity Hotel\u002fMarch\u002f141","ESP\u002fCity Hotel\u002fJuly\u002f142","DEU\u002fCity Hotel\u002fJanuary\u002f143","ESP\u002fResort Hotel\u002fJuly\u002f143","ESP\u002fCity Hotel\u002fJune\u002f144","DEU\u002fCity Hotel\u002fMay\u002f144","FRA\u002fResort Hotel\u002fAugust\u002f151","ESP\u002fCity Hotel\u002fApril\u002f153","DEU\u002fResort Hotel\u002fMarch\u002f154","ESP\u002fResort Hotel\u002fSeptember\u002f154","FRA\u002fResort Hotel\u002fSeptember\u002f155","ESP\u002fCity Hotel\u002fMay\u002f160","FRA\u002fCity Hotel\u002fJune\u002f162","GBR\u002fCity Hotel\u002fApril\u002f164","ESP\u002fCity Hotel\u002fNovember\u002f165","FRA\u002fCity Hotel\u002fJuly\u002f168","DEU\u002fCity Hotel\u002fNovember\u002f168","GBR\u002fCity Hotel\u002fNovember\u002f169","FRA\u002fResort Hotel\u002fNovember\u002f169","ESP\u002fResort Hotel\u002fJanuary\u002f178","ESP\u002fCity Hotel\u002fApril\u002f185","DEU\u002fCity Hotel\u002fFebruary\u002f187","GBR\u002fCity Hotel\u002fJune\u002f187","DEU\u002fResort Hotel\u002fMay\u002f188","ESP\u002fCity Hotel\u002fDecember\u002f190","ESP\u002fCity Hotel\u002fJanuary\u002f200","FRA\u002fCity Hotel\u002fMay\u002f200","GBR\u002fResort Hotel\u002fJanuary\u002f202","PRT\u002fResort Hotel\u002fJanuary\u002f205","FRA\u002fCity Hotel\u002fApril\u002f210","ESP\u002fResort Hotel\u002fNovember\u002f212","GBR\u002fCity Hotel\u002fJuly\u002f216","ESP\u002fResort Hotel\u002fOctober\u002f218","GBR\u002fCity Hotel\u002fMay\u002f223","GBR\u002fCity Hotel\u002fAugust\u002f227","GBR\u002fResort Hotel\u002fDecember\u002f227","GBR\u002fCity Hotel\u002fFebruary\u002f227","ESP\u002fCity Hotel\u002fJuly\u002f235","ESP\u002fResort Hotel\u002fApril\u002f237","ESP\u002fCity Hotel\u002fOctober\u002f241","ESP\u002fCity Hotel\u002fAugust\u002f245","DEU\u002fResort Hotel\u002fApril\u002f246","ESP\u002fResort Hotel\u002fAugust\u002f256","GBR\u002fResort Hotel\u002fNovember\u002f258","FRA\u002fCity Hotel\u002fJanuary\u002f261","ESP\u002fCity Hotel\u002fFebruary\u002f285","ESP\u002fCity Hotel\u002fMarch\u002f288","GBR\u002fCity Hotel\u002fOctober\u002f294","FRA\u002fCity Hotel\u002fAugust\u002f299","ESP\u002fResort Hotel\u002fFebruary\u002f300","ESP\u002fResort Hotel\u002fMarch\u002f310","GBR\u002fCity Hotel\u002fApril\u002f328","GBR\u002fCity Hotel\u002fMarch\u002f334","PRT\u002fResort Hotel\u002fNovember\u002f334","ESP\u002fCity Hotel\u002fSeptember\u002f336","GBR\u002fCity Hotel\u002fSeptember\u002f337","ESP\u002fResort Hotel\u002fDecember\u002f352","ESP\u002fCity Hotel\u002fDecember\u002f359","ESP\u002fResort Hotel\u002fJuly\u002f401","DEU\u002fCity Hotel\u002fMarch\u002f410","FRA\u002fCity Hotel\u002fDecember\u002f415","GBR\u002fResort Hotel\u002fFebruary\u002f423","PRT\u002fResort Hotel\u002fSeptember\u002f430","GBR\u002fCity Hotel\u002fMay\u002f432","GBR\u002fResort Hotel\u002fAugust\u002f433","GBR\u002fCity Hotel\u002fAugust\u002f444","DEU\u002fCity Hotel\u002fSeptember\u002f447","GBR\u002fResort Hotel\u002fMarch\u002f469","GBR\u002fCity Hotel\u002fJune\u002f477","PRT\u002fResort Hotel\u002fDecember\u002f483","DEU\u002fCity Hotel\u002fApril\u002f493","FRA\u002fCity Hotel\u002fNovember\u002f500","GBR\u002fResort Hotel\u002fJuly\u002f510","PRT\u002fResort Hotel\u002fJune\u002f514","ESP\u002fResort Hotel\u002fAugust\u002f517","DEU\u002fCity Hotel\u002fMay\u002f518","FRA\u002fCity Hotel\u002fSeptember\u002f519","FRA\u002fCity Hotel\u002fJuly\u002f520","GBR\u002fCity Hotel\u002fJuly\u002f536","GBR\u002fResort Hotel\u002fApril\u002f555","FRA\u002fCity Hotel\u002fFebruary\u002f564","GBR\u002fResort Hotel\u002fSeptember\u002f568","PRT\u002fResort Hotel\u002fMay\u002f574","DEU\u002fCity Hotel\u002fOctober\u002f584","PRT\u002fResort Hotel\u002fOctober\u002f585","FRA\u002fCity Hotel\u002fJune\u002f590","GBR\u002fResort Hotel\u002fJune\u002f612","PRT\u002fResort Hotel\u002fJune\u002f623","PRT\u002fResort Hotel\u002fMarch\u002f623","PRT\u002fResort Hotel\u002fFebruary\u002f625","DEU\u002fCity Hotel\u002fJune\u002f633","PRT\u002fCity Hotel\u002fJanuary\u002f644","DEU\u002fCity Hotel\u002fJuly\u002f646","DEU\u002fCity Hotel\u002fAugust\u002f658","PRT\u002fCity Hotel\u002fDecember\u002f660","PRT\u002fResort Hotel\u002fMay\u002f660","PRT\u002fResort Hotel\u002fOctober\u002f682","FRA\u002fCity Hotel\u002fOctober\u002f685","ESP\u002fCity Hotel\u002fAugust\u002f687","PRT\u002fResort Hotel\u002fSeptember\u002f696","PRT\u002fCity Hotel\u002fApril\u002f702","PRT\u002fCity Hotel\u002fNovember\u002f704","PRT\u002fResort Hotel\u002fApril\u002f708","FRA\u002fCity Hotel\u002fApril\u002f712","FRA\u002fCity Hotel\u002fMarch\u002f714","PRT\u002fResort Hotel\u002fApril\u002f768","GBR\u002fResort Hotel\u002fMay\u002f783","FRA\u002fCity Hotel\u002fMay\u002f786","PRT\u002fResort Hotel\u002fNovember\u002f807","FRA\u002fCity Hotel\u002fAugust\u002f815","PRT\u002fCity Hotel\u002fJanuary\u002f857","PRT\u002fCity Hotel\u002fFebruary\u002f870","GBR\u002fResort Hotel\u002fOctober\u002f883","PRT\u002fCity Hotel\u002fMarch\u002f888","PRT\u002fCity Hotel\u002fMay\u002f896","PRT\u002fResort Hotel\u002fJuly\u002f911","PRT\u002fResort Hotel\u002fDecember\u002f952","PRT\u002fCity Hotel\u002fJune\u002f955","PRT\u002fResort Hotel\u002fJanuary\u002f956","PRT\u002fCity Hotel\u002fDecember\u002f963","PRT\u002fResort Hotel\u002fMarch\u002f983","PRT\u002fResort Hotel\u002fAugust\u002f985","PRT\u002fCity Hotel\u002fAugust\u002f987","PRT\u002fResort Hotel\u002fFebruary\u002f1074","PRT\u002fCity Hotel\u002fFebruary\u002f1097","PRT\u002fResort Hotel\u002fJuly\u002f1098","PRT\u002fCity Hotel\u002fNovember\u002f1171","PRT\u002fCity Hotel\u002fJuly\u002f1178","PRT\u002fCity Hotel\u002fSeptember\u002f1196","PRT\u002fCity Hotel\u002fOctober\u002f1199","PRT\u002fCity Hotel\u002fMarch\u002f1232","PRT\u002fResort Hotel\u002fAugust\u002f1354","PRT\u002fCity Hotel\u002fJuly\u002f1718","PRT\u002fCity Hotel\u002fAugust\u002f1828","PRT\u002fCity Hotel\u002fApril\u002f1856","PRT\u002fCity Hotel\u002fMay\u002f2187","PRT\u002fCity Hotel\u002fJune\u002f2283","PRT\u002fCity Hotel\u002fOctober\u002f2442","PRT\u002fCity Hotel\u002fSeptember\u002f2447","DEU\u002fCity Hotel\u002fApril","ESP\u002fCity Hotel\u002fApril","FRA\u002fCity Hotel\u002fApril","GBR\u002fCity Hotel\u002fApril","PRT\u002fCity Hotel\u002fApril","DEU\u002fResort Hotel\u002fApril","ESP\u002fResort Hotel\u002fApril","FRA\u002fResort Hotel\u002fApril","GBR\u002fResort Hotel\u002fApril","PRT\u002fResort Hotel\u002fApril","DEU\u002fCity Hotel\u002fAugust","ESP\u002fCity Hotel\u002fAugust","FRA\u002fCity Hotel\u002fAugust","GBR\u002fCity Hotel\u002fAugust","PRT\u002fCity Hotel\u002fAugust","DEU\u002fResort Hotel\u002fAugust","ESP\u002fResort Hotel\u002fAugust","FRA\u002fResort Hotel\u002fAugust","GBR\u002fResort Hotel\u002fAugust","PRT\u002fResort Hotel\u002fAugust","DEU\u002fCity Hotel\u002fDecember","ESP\u002fCity Hotel\u002fDecember","FRA\u002fCity Hotel\u002fDecember","GBR\u002fCity Hotel\u002fDecember","PRT\u002fCity Hotel\u002fDecember","DEU\u002fResort Hotel\u002fDecember","ESP\u002fResort Hotel\u002fDecember","FRA\u002fResort Hotel\u002fDecember","GBR\u002fResort Hotel\u002fDecember","PRT\u002fResort Hotel\u002fDecember","DEU\u002fCity Hotel\u002fFebruary","ESP\u002fCity Hotel\u002fFebruary","FRA\u002fCity Hotel\u002fFebruary","GBR\u002fCity Hotel\u002fFebruary","PRT\u002fCity Hotel\u002fFebruary","DEU\u002fResort Hotel\u002fFebruary","ESP\u002fResort Hotel\u002fFebruary","FRA\u002fResort Hotel\u002fFebruary","GBR\u002fResort Hotel\u002fFebruary","PRT\u002fResort Hotel\u002fFebruary","DEU\u002fCity Hotel\u002fJanuary","ESP\u002fCity Hotel\u002fJanuary","FRA\u002fCity Hotel\u002fJanuary","GBR\u002fCity Hotel\u002fJanuary","PRT\u002fCity Hotel\u002fJanuary","DEU\u002fResort Hotel\u002fJanuary","ESP\u002fResort Hotel\u002fJanuary","FRA\u002fResort Hotel\u002fJanuary","GBR\u002fResort Hotel\u002fJanuary","PRT\u002fResort Hotel\u002fJanuary","DEU\u002fCity Hotel\u002fJuly","ESP\u002fCity Hotel\u002fJuly","FRA\u002fCity Hotel\u002fJuly","GBR\u002fCity Hotel\u002fJuly","PRT\u002fCity Hotel\u002fJuly","DEU\u002fResort Hotel\u002fJuly","ESP\u002fResort Hotel\u002fJuly","FRA\u002fResort Hotel\u002fJuly","GBR\u002fResort Hotel\u002fJuly","PRT\u002fResort Hotel\u002fJuly","DEU\u002fCity Hotel\u002fJune","ESP\u002fCity Hotel\u002fJune","FRA\u002fCity Hotel\u002fJune","GBR\u002fCity Hotel\u002fJune","PRT\u002fCity Hotel\u002fJune","DEU\u002fResort Hotel\u002fJune","ESP\u002fResort Hotel\u002fJune","FRA\u002fResort Hotel\u002fJune","GBR\u002fResort Hotel\u002fJune","PRT\u002fResort Hotel\u002fJune","DEU\u002fCity Hotel\u002fMarch","ESP\u002fCity Hotel\u002fMarch","FRA\u002fCity Hotel\u002fMarch","GBR\u002fCity Hotel\u002fMarch","PRT\u002fCity Hotel\u002fMarch","DEU\u002fResort Hotel\u002fMarch","ESP\u002fResort Hotel\u002fMarch","FRA\u002fResort Hotel\u002fMarch","GBR\u002fResort Hotel\u002fMarch","PRT\u002fResort Hotel\u002fMarch","DEU\u002fCity Hotel\u002fMay","ESP\u002fCity Hotel\u002fMay","FRA\u002fCity Hotel\u002fMay","GBR\u002fCity Hotel\u002fMay","PRT\u002fCity Hotel\u002fMay","DEU\u002fResort Hotel\u002fMay","ESP\u002fResort Hotel\u002fMay","FRA\u002fResort Hotel\u002fMay","GBR\u002fResort Hotel\u002fMay","PRT\u002fResort Hotel\u002fMay","DEU\u002fCity Hotel\u002fNovember","ESP\u002fCity Hotel\u002fNovember","FRA\u002fCity Hotel\u002fNovember","GBR\u002fCity Hotel\u002fNovember","PRT\u002fCity Hotel\u002fNovember","DEU\u002fResort Hotel\u002fNovember","ESP\u002fResort Hotel\u002fNovember","FRA\u002fResort Hotel\u002fNovember","GBR\u002fResort Hotel\u002fNovember","PRT\u002fResort Hotel\u002fNovember","DEU\u002fCity Hotel\u002fOctober","ESP\u002fCity Hotel\u002fOctober","FRA\u002fCity Hotel\u002fOctober","GBR\u002fCity Hotel\u002fOctober","PRT\u002fCity Hotel\u002fOctober","DEU\u002fResort Hotel\u002fOctober","ESP\u002fResort Hotel\u002fOctober","FRA\u002fResort Hotel\u002fOctober","GBR\u002fResort Hotel\u002fOctober","PRT\u002fResort Hotel\u002fOctober","DEU\u002fCity Hotel\u002fSeptember","ESP\u002fCity Hotel\u002fSeptember","FRA\u002fCity Hotel\u002fSeptember","GBR\u002fCity Hotel\u002fSeptember","PRT\u002fCity Hotel\u002fSeptember","DEU\u002fResort Hotel\u002fSeptember","ESP\u002fResort Hotel\u002fSeptember","FRA\u002fResort Hotel\u002fSeptember","GBR\u002fResort Hotel\u002fSeptember","PRT\u002fResort Hotel\u002fSeptember","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU","ESP","FRA","GBR","PRT"],"labels":["3","6","7","7","7","8","8","10","10","11","12","12","12","13","15","16","16","19","21","21","22","23","23","24","24","25","29","30","30","34","36","36","36","37","37","38","38","39","43","44","44","44","46","46","46","47","47","49","49","50","51","54","56","59","61","61","63","67","69","70","70","71","71","71","71","73","73","74","77","79","81","88","95","96","97","97","99","100","102","105","105","108","111","112","113","113","114","116","119","119","123","124","125","127","129","135","137","137","138","138","139","141","142","143","143","144","144","151","153","154","154","155","160","162","164","165","168","168","169","169","178","185","187","187","188","190","200","200","202","205","210","212","216","218","223","227","227","227","235","237","241","245","246","256","258","261","285","288","294","299","300","310","328","334","334","336","337","352","359","401","410","415","423","430","432","433","444","447","469","477","483","493","500","510","514","517","518","519","520","536","555","564","568","574","584","585","590","612","623","623","625","633","644","646","658","660","660","682","685","687","696","702","704","708","712","714","768","783","786","807","815","857","870","883","888","896","911","952","955","956","963","983","985","987","1074","1097","1098","1171","1178","1196","1199","1232","1354","1718","1828","1856","2187","2283","2442","2447","April","April","April","April","April","April","April","April","April","April","August","August","August","August","August","August","August","August","August","August","December","December","December","December","December","December","December","December","December","December","February","February","February","February","February","February","February","February","February","February","January","January","January","January","January","January","January","January","January","January","July","July","July","July","July","July","July","July","July","July","June","June","June","June","June","June","June","June","June","June","March","March","March","March","March","March","March","March","March","March","May","May","May","May","May","May","May","May","May","May","November","November","November","November","November","November","November","November","November","November","October","October","October","October","October","October","October","October","October","October","September","September","September","September","September","September","September","September","September","September","City Hotel","City Hotel","City Hotel","City Hotel","City Hotel","Resort Hotel","Resort Hotel","Resort Hotel","Resort Hotel","Resort Hotel","DEU","ESP","FRA","GBR","PRT"],"marker":{"coloraxis":"coloraxis","colors":[1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,0.0,1.0,1.0,1.0,0.0,1.0,1.0,0.0,1.0,1.0,1.0,1.0,0.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,0.0,0.0,0.0,1.0,1.0,1.0,0.0,1.0,1.0,0.0,0.0,1.0,0.0,1.0,0.0,1.0,1.0,1.0,1.0,1.0,0.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,0.0,0.0,1.0,0.0,1.0,0.0,0.0,0.0,1.0,1.0,1.0,1.0,0.0,0.0,1.0,0.0,1.0,1.0,0.0,1.0,1.0,1.0,1.0,1.0,0.0,1.0,0.0,1.0,0.0,1.0,0.0,0.0,0.0,0.0,1.0,1.0,0.0,1.0,0.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,1.0,0.0,1.0,0.0,1.0,1.0,0.0,1.0,0.0,1.0,1.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,1.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,0.0,0.0,0.0,1.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,0.0,1.0,1.0,1.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,0.0,0.0,1.0,0.0,0.0,1.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1.0,0.0,0.0,0.0,0.0,1.0,0.0,0.0,0.0,1.0,0.0,1.0,0.0,0.0,1.0,0.0,1.0,0.0,0.0,0.0,1.0,0.0,1.0,1.0,1.0,1.0,1.0,1.0,1.0,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5,0.5]},"name":"","parents":["DEU\u002fResort Hotel\u002fMarch","DEU\u002fResort Hotel\u002fFebruary","DEU\u002fResort Hotel\u002fJanuary","DEU\u002fResort Hotel\u002fNovember","FRA\u002fResort Hotel\u002fSeptember","DEU\u002fResort Hotel\u002fDecember","FRA\u002fResort Hotel\u002fNovember","FRA\u002fResort Hotel\u002fJanuary","FRA\u002fResort Hotel\u002fJune","DEU\u002fResort Hotel\u002fSeptember","DEU\u002fResort Hotel\u002fJuly","DEU\u002fResort Hotel\u002fOctober","FRA\u002fResort Hotel\u002fOctober","FRA\u002fResort Hotel\u002fMarch","FRA\u002fResort Hotel\u002fFebruary","DEU\u002fResort Hotel\u002fApril","DEU\u002fResort Hotel\u002fJune","ESP\u002fResort Hotel\u002fJanuary","FRA\u002fResort Hotel\u002fDecember","ESP\u002fResort Hotel\u002fNovember","ESP\u002fResort Hotel\u002fMarch","FRA\u002fResort Hotel\u002fApril","DEU\u002fResort Hotel\u002fMay","FRA\u002fResort Hotel\u002fJuly","FRA\u002fResort Hotel\u002fMay","DEU\u002fResort Hotel\u002fAugust","DEU\u002fCity Hotel\u002fJanuary","GBR\u002fCity Hotel\u002fJanuary","GBR\u002fResort Hotel\u002fJanuary","ESP\u002fResort Hotel\u002fDecember","DEU\u002fResort Hotel\u002fDecember","ESP\u002fResort Hotel\u002fFebruary","FRA\u002fCity Hotel\u002fNovember","GBR\u002fResort Hotel\u002fDecember","DEU\u002fResort Hotel\u002fJanuary","ESP\u002fResort Hotel\u002fMay","ESP\u002fResort Hotel\u002fSeptember","DEU\u002fResort Hotel\u002fAugust","ESP\u002fCity Hotel\u002fOctober","FRA\u002fResort Hotel\u002fAugust","ESP\u002fCity Hotel\u002fNovember","GBR\u002fResort Hotel\u002fNovember","DEU\u002fResort Hotel\u002fFebruary","GBR\u002fResort Hotel\u002fFebruary","GBR\u002fResort Hotel\u002fMarch","GBR\u002fCity Hotel\u002fDecember","DEU\u002fCity Hotel\u002fNovember","DEU\u002fCity Hotel\u002fFebruary","GBR\u002fCity Hotel\u002fNovember","ESP\u002fCity Hotel\u002fSeptember","DEU\u002fResort Hotel\u002fJuly","FRA\u002fResort Hotel\u002fJune","DEU\u002fResort Hotel\u002fJune","DEU\u002fCity Hotel\u002fDecember","ESP\u002fResort Hotel\u002fJune","DEU\u002fCity Hotel\u002fSeptember","DEU\u002fResort Hotel\u002fSeptember","FRA\u002fCity Hotel\u002fJanuary","ESP\u002fCity Hotel\u002fJanuary","GBR\u002fCity Hotel\u002fDecember","DEU\u002fResort Hotel\u002fNovember","ESP\u002fCity Hotel\u002fFebruary","FRA\u002fResort Hotel\u002fJuly","GBR\u002fCity Hotel\u002fOctober","DEU\u002fResort Hotel\u002fOctober","FRA\u002fCity Hotel\u002fDecember","DEU\u002fCity Hotel\u002fOctober","GBR\u002fResort Hotel\u002fJuly","GBR\u002fResort Hotel\u002fOctober","ESP\u002fCity Hotel\u002fMay","FRA\u002fResort Hotel\u002fJanuary","ESP\u002fResort Hotel\u002fOctober","ESP\u002fResort Hotel\u002fApril","DEU\u002fCity Hotel\u002fJune","GBR\u002fResort Hotel\u002fAugust","GBR\u002fCity Hotel\u002fFebruary","ESP\u002fCity Hotel\u002fJune","GBR\u002fResort Hotel\u002fApril","GBR\u002fResort Hotel\u002fJune","FRA\u002fResort Hotel\u002fFebruary","GBR\u002fCity Hotel\u002fJanuary","FRA\u002fCity Hotel\u002fSeptember","FRA\u002fResort Hotel\u002fMarch","GBR\u002fCity Hotel\u002fSeptember","ESP\u002fResort Hotel\u002fJune","FRA\u002fResort Hotel\u002fOctober","ESP\u002fResort Hotel\u002fMay","DEU\u002fCity Hotel\u002fMarch","GBR\u002fResort Hotel\u002fMay","GBR\u002fResort Hotel\u002fSeptember","DEU\u002fCity Hotel\u002fJuly","FRA\u002fResort Hotel\u002fDecember","DEU\u002fCity Hotel\u002fDecember","FRA\u002fCity Hotel\u002fFebruary","FRA\u002fResort Hotel\u002fApril","FRA\u002fCity Hotel\u002fMarch","DEU\u002fCity Hotel\u002fAugust","FRA\u002fResort Hotel\u002fMay","DEU\u002fCity Hotel\u002fApril","FRA\u002fCity Hotel\u002fOctober","GBR\u002fCity Hotel\u002fMarch","ESP\u002fCity Hotel\u002fMarch","ESP\u002fCity Hotel\u002fJuly","DEU\u002fCity Hotel\u002fJanuary","ESP\u002fResort Hotel\u002fJuly","ESP\u002fCity Hotel\u002fJune","DEU\u002fCity Hotel\u002fMay","FRA\u002fResort Hotel\u002fAugust","ESP\u002fCity Hotel\u002fApril","DEU\u002fResort Hotel\u002fMarch","ESP\u002fResort Hotel\u002fSeptember","FRA\u002fResort Hotel\u002fSeptember","ESP\u002fCity Hotel\u002fMay","FRA\u002fCity Hotel\u002fJune","GBR\u002fCity Hotel\u002fApril","ESP\u002fCity Hotel\u002fNovember","FRA\u002fCity Hotel\u002fJuly","DEU\u002fCity Hotel\u002fNovember","GBR\u002fCity Hotel\u002fNovember","FRA\u002fResort Hotel\u002fNovember","ESP\u002fResort Hotel\u002fJanuary","ESP\u002fCity Hotel\u002fApril","DEU\u002fCity Hotel\u002fFebruary","GBR\u002fCity Hotel\u002fJune","DEU\u002fResort Hotel\u002fMay","ESP\u002fCity Hotel\u002fDecember","ESP\u002fCity Hotel\u002fJanuary","FRA\u002fCity Hotel\u002fMay","GBR\u002fResort Hotel\u002fJanuary","PRT\u002fResort Hotel\u002fJanuary","FRA\u002fCity Hotel\u002fApril","ESP\u002fResort Hotel\u002fNovember","GBR\u002fCity Hotel\u002fJuly","ESP\u002fResort Hotel\u002fOctober","GBR\u002fCity Hotel\u002fMay","GBR\u002fCity Hotel\u002fAugust","GBR\u002fResort Hotel\u002fDecember","GBR\u002fCity Hotel\u002fFebruary","ESP\u002fCity Hotel\u002fJuly","ESP\u002fResort Hotel\u002fApril","ESP\u002fCity Hotel\u002fOctober","ESP\u002fCity Hotel\u002fAugust","DEU\u002fResort Hotel\u002fApril","ESP\u002fResort Hotel\u002fAugust","GBR\u002fResort Hotel\u002fNovember","FRA\u002fCity Hotel\u002fJanuary","ESP\u002fCity Hotel\u002fFebruary","ESP\u002fCity Hotel\u002fMarch","GBR\u002fCity Hotel\u002fOctober","FRA\u002fCity Hotel\u002fAugust","ESP\u002fResort Hotel\u002fFebruary","ESP\u002fResort Hotel\u002fMarch","GBR\u002fCity Hotel\u002fApril","GBR\u002fCity Hotel\u002fMarch","PRT\u002fResort Hotel\u002fNovember","ESP\u002fCity Hotel\u002fSeptember","GBR\u002fCity Hotel\u002fSeptember","ESP\u002fResort Hotel\u002fDecember","ESP\u002fCity Hotel\u002fDecember","ESP\u002fResort Hotel\u002fJuly","DEU\u002fCity Hotel\u002fMarch","FRA\u002fCity Hotel\u002fDecember","GBR\u002fResort Hotel\u002fFebruary","PRT\u002fResort Hotel\u002fSeptember","GBR\u002fCity Hotel\u002fMay","GBR\u002fResort Hotel\u002fAugust","GBR\u002fCity Hotel\u002fAugust","DEU\u002fCity Hotel\u002fSeptember","GBR\u002fResort Hotel\u002fMarch","GBR\u002fCity Hotel\u002fJune","PRT\u002fResort Hotel\u002fDecember","DEU\u002fCity Hotel\u002fApril","FRA\u002fCity Hotel\u002fNovember","GBR\u002fResort Hotel\u002fJuly","PRT\u002fResort Hotel\u002fJune","ESP\u002fResort Hotel\u002fAugust","DEU\u002fCity Hotel\u002fMay","FRA\u002fCity Hotel\u002fSeptember","FRA\u002fCity Hotel\u002fJuly","GBR\u002fCity Hotel\u002fJuly","GBR\u002fResort Hotel\u002fApril","FRA\u002fCity Hotel\u002fFebruary","GBR\u002fResort Hotel\u002fSeptember","PRT\u002fResort Hotel\u002fMay","DEU\u002fCity Hotel\u002fOctober","PRT\u002fResort Hotel\u002fOctober","FRA\u002fCity Hotel\u002fJune","GBR\u002fResort Hotel\u002fJune","PRT\u002fResort Hotel\u002fJune","PRT\u002fResort Hotel\u002fMarch","PRT\u002fResort Hotel\u002fFebruary","DEU\u002fCity Hotel\u002fJune","PRT\u002fCity Hotel\u002fJanuary","DEU\u002fCity Hotel\u002fJuly","DEU\u002fCity Hotel\u002fAugust","PRT\u002fCity Hotel\u002fDecember","PRT\u002fResort Hotel\u002fMay","PRT\u002fResort Hotel\u002fOctober","FRA\u002fCity Hotel\u002fOctober","ESP\u002fCity Hotel\u002fAugust","PRT\u002fResort Hotel\u002fSeptember","PRT\u002fCity Hotel\u002fApril","PRT\u002fCity Hotel\u002fNovember","PRT\u002fResort Hotel\u002fApril","FRA\u002fCity Hotel\u002fApril","FRA\u002fCity Hotel\u002fMarch","PRT\u002fResort Hotel\u002fApril","GBR\u002fResort Hotel\u002fMay","FRA\u002fCity Hotel\u002fMay","PRT\u002fResort Hotel\u002fNovember","FRA\u002fCity Hotel\u002fAugust","PRT\u002fCity Hotel\u002fJanuary","PRT\u002fCity Hotel\u002fFebruary","GBR\u002fResort Hotel\u002fOctober","PRT\u002fCity Hotel\u002fMarch","PRT\u002fCity Hotel\u002fMay","PRT\u002fResort Hotel\u002fJuly","PRT\u002fResort Hotel\u002fDecember","PRT\u002fCity Hotel\u002fJune","PRT\u002fResort Hotel\u002fJanuary","PRT\u002fCity Hotel\u002fDecember","PRT\u002fResort Hotel\u002fMarch","PRT\u002fResort Hotel\u002fAugust","PRT\u002fCity Hotel\u002fAugust","PRT\u002fResort Hotel\u002fFebruary","PRT\u002fCity Hotel\u002fFebruary","PRT\u002fResort Hotel\u002fJuly","PRT\u002fCity Hotel\u002fNovember","PRT\u002fCity Hotel\u002fJuly","PRT\u002fCity Hotel\u002fSeptember","PRT\u002fCity Hotel\u002fOctober","PRT\u002fCity Hotel\u002fMarch","PRT\u002fResort Hotel\u002fAugust","PRT\u002fCity Hotel\u002fJuly","PRT\u002fCity Hotel\u002fAugust","PRT\u002fCity Hotel\u002fApril","PRT\u002fCity Hotel\u002fMay","PRT\u002fCity Hotel\u002fJune","PRT\u002fCity Hotel\u002fOctober","PRT\u002fCity Hotel\u002fSeptember","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU\u002fCity Hotel","ESP\u002fCity Hotel","FRA\u002fCity Hotel","GBR\u002fCity Hotel","PRT\u002fCity Hotel","DEU\u002fResort Hotel","ESP\u002fResort Hotel","FRA\u002fResort Hotel","GBR\u002fResort Hotel","PRT\u002fResort Hotel","DEU","ESP","FRA","GBR","PRT","DEU","ESP","FRA","GBR","PRT","","","","",""],"values":[1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,2,24,24,24,24,24,24,24,24,24,24,48,48,48,48,48],"type":"sunburst"}],                        {"template":{"data":{"histogram2dcontour":[{"type":"histogram2dcontour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"choropleth":[{"type":"choropleth","colorbar":{"outlinewidth":0,"ticks":""}}],"histogram2d":[{"type":"histogram2d","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmap":[{"type":"heatmap","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"heatmapgl":[{"type":"heatmapgl","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"contourcarpet":[{"type":"contourcarpet","colorbar":{"outlinewidth":0,"ticks":""}}],"contour":[{"type":"contour","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"surface":[{"type":"surface","colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]}],"mesh3d":[{"type":"mesh3d","colorbar":{"outlinewidth":0,"ticks":""}}],"scatter":[{"fillpattern":{"fillmode":"overlay","size":10,"solidity":0.2},"type":"scatter"}],"parcoords":[{"type":"parcoords","line":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolargl":[{"type":"scatterpolargl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"scattergeo":[{"type":"scattergeo","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterpolar":[{"type":"scatterpolar","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"scattergl":[{"type":"scattergl","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatter3d":[{"type":"scatter3d","line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattermapbox":[{"type":"scattermapbox","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scatterternary":[{"type":"scatterternary","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"scattercarpet":[{"type":"scattercarpet","marker":{"colorbar":{"outlinewidth":0,"ticks":""}}}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"pie":[{"automargin":true,"type":"pie"}]},"layout":{"autotypenumbers":"strict","colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"hovermode":"closest","hoverlabel":{"align":"left"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"bgcolor":"#E5ECF6","angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"ternary":{"bgcolor":"#E5ECF6","aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]]},"xaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"yaxis":{"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","automargin":true,"zerolinewidth":2},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white","gridwidth":2}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"geo":{"bgcolor":"white","landcolor":"#E5ECF6","subunitcolor":"white","showland":true,"showlakes":true,"lakecolor":"white"},"title":{"x":0.05},"mapbox":{"style":"light"}}},"coloraxis":{"colorbar":{"title":{"text":"is_canceled"}},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"legend":{"tracegroupgap":0},"margin":{"t":60},"hovermode":false},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('869c2d95-df36-4367-a148-5b4d5440625a');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                });            </script>        </div>



```python
#  According to my sunburst chart my hypothesis was not confirmed, as Resort Hotels are in high demand mostly in the summer, but  City hotels remain popular in both warm and cold seasons.
# For example: In France  Resort Hotels are queit popular August, at the same time City Hotels remain in demand both in June and December.
```
