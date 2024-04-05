```python
import pandas as pd
import numpy as np
```


```python
#Importing the three years of spirit sales that will be used for analysis

iowa_spirits_2022 = pd.read_csv('/Users/christopherkonopka/Desktop/Data Analytics/Capstone 2/Iowa Liquor Sales/Iowa_Liquor_Sales2022.csv')
iowa_spirits_2021 = pd.read_csv('/Users/christopherkonopka/Desktop/Data Analytics/Capstone 2/Iowa Liquor Sales/Iowa_Liquor_Sales2021.csv')
iowa_spirits_2020 = pd.read_csv('/Users/christopherkonopka/Desktop/Data Analytics/Capstone 2/Iowa Liquor Sales/Iowa_Liquor_Sales2020.csv')

```


```python
#Combining all three csv files into one file

iowa_sales = pd.concat([iowa_spirits_2020, iowa_spirits_2021, iowa_spirits_2022], ignore_index=True)
```


```python
#Examine the dataset and columns

print(iowa_sales.head)
```

    <bound method NDFrame.head of         Invoice/Item Number        Date  Store Number  \
    0           INV-24306300080  01/02/2020          5257   
    1           INV-24306300069  01/02/2020          5257   
    2           INV-24290800022  01/02/2020          2500   
    3           INV-24314100034  01/02/2020          5501   
    4           INV-24312800010  01/02/2020          5709   
    ...                     ...         ...           ...   
    7800554     INV-54529100111  12/30/2022          5916   
    7800555     INV-54551000003  12/30/2022          6021   
    7800556     INV-54528400003  12/30/2022          3868   
    7800557     INV-54548000013  12/30/2022          4159   
    7800558     INV-54543000001  12/30/2022          5726   
    
                                        Store Name  \
    0                            MAD AVE QUIK SHOP   
    1                            MAD AVE QUIK SHOP   
    2                  HY-VEE FOOD STORE #1 / AMES   
    3                      QUIK TRIP #530 / EUCLID   
    4                                    JW LIQUOR   
    ...                                        ...   
    7800554                 ANOTHER ROUND / DEWITT   
    7800555  CASEY'S GENERAL STORE #2315 / CORYDON   
    7800556                 WAL-MART 3630 / MARION   
    7800557   FAREWAY STORES #073 / COUNCIL BLUFFS   
    7800558              EHLINGER'S VINTON EXPRESS   
    
                                      Address            City  Zip Code  \
    0                        405, MADISON AVE         OTTUMWA   52501.0   
    1                        405, MADISON AVE         OTTUMWA   52501.0   
    2                      3800 W LINCOLN WAY            AMES   50010.0   
    3                       1424 E EUCLID AVE      DES MOINES   50313.0   
    4        4518 MORTONSEN STREET SUITE #109            AMES   50014.0   
    ...                                   ...             ...       ...   
    7800554                     622 S 6TH AVE          DEWITT   52742.0   
    7800555               220 N WASHINGTON ST         CORYDON   50060.0   
    7800556             5491 BUSINESS HWY 151          MARION   52302.0   
    7800557                  310 MCKENZIE AVE  COUNCIL BLUFFS   51503.0   
    7800558                310 K AVENUE SOUTH          VINTON   52349.0   
    
                         Store Location  County Number         County  ...  \
    0                               NaN           90.0        WAPELLO  ...   
    1                               NaN           90.0        WAPELLO  ...   
    2                               NaN           85.0          STORY  ...   
    3                               NaN           77.0           POLK  ...   
    4                               NaN           85.0          STORY  ...   
    ...                             ...            ...            ...  ...   
    7800554  POINT (-90.53908 41.80942)            NaN        CLINTON  ...   
    7800555  POINT (-93.31801 40.75866)            NaN          WAYNE  ...   
    7800556  POINT (-91.55323 42.03567)            NaN           LINN  ...   
    7800557  POINT (-95.81894 41.28021)            NaN  POTTAWATTAMIE  ...   
    7800558  POINT (-92.03752 42.16832)            NaN         BENTON  ...   
    
             State Bottle Retail Bottles Sold  Sale (Dollars)  \
    0                       6.60           12           79.20   
    1                      10.80            6           64.80   
    2                      32.22            2           64.44   
    3                       5.25            2           10.50   
    4                      27.74            2           55.48   
    ...                      ...          ...             ...   
    7800554                21.99           12          263.88   
    7800555                13.47            4           53.88   
    7800556                12.38            6           74.28   
    7800557                20.25           12          243.00   
    7800558                 9.21           12          110.52   
    
            Volume Sold (Liters)  Volume Sold (Gallons)  \
    0                      12.00                   3.17   
    1                      10.50                   2.77   
    2                       1.50                   0.39   
    3                       0.75                   0.19   
    4                       1.50                   0.39   
    ...                      ...                    ...   
    7800554                21.00                   5.54   
    7800555                 3.00                   0.79   
    7800556                10.50                   2.77   
    7800557                 9.00                   2.37   
    7800558                12.00                   3.17   
    
            Iowa ZIP Code Tabulation Areas  Iowa Watershed Sub-Basins (HUC 08)  \
    0                                  NaN                                 NaN   
    1                                  NaN                                 NaN   
    2                                  NaN                                 NaN   
    3                                  NaN                                 NaN   
    4                                  NaN                                 NaN   
    ...                                ...                                 ...   
    7800554                          841.0                                 9.0   
    7800555                          703.0                                54.0   
    7800556                          443.0                                19.0   
    7800557                          817.0                                40.0   
    7800558                          804.0                                18.0   
    
             Iowa Watersheds (HUC 10)  County Boundaries of Iowa  US Counties  
    0                             NaN                        NaN          NaN  
    1                             NaN                        NaN          NaN  
    2                             NaN                        NaN          NaN  
    3                             NaN                        NaN          NaN  
    4                             NaN                        NaN          NaN  
    ...                           ...                        ...          ...  
    7800554                     103.0                       55.0       1745.0  
    7800555                     531.0                       97.0       1887.0  
    7800556                     265.0                       45.0        287.0  
    7800557                     236.0                       69.0       1879.0  
    7800558                     248.0                       46.0       1367.0  
    
    [7800559 rows x 29 columns]>



```python
#Determine the amount of entries for each column

iowa_sales.count()
```




    Invoice/Item Number                   7800559
    Date                                  7800559
    Store Number                          7800559
    Store Name                            7800559
    Address                               7798438
    City                                  7798438
    Zip Code                              7798416
    Store Location                        7035723
    County Number                         6554266
    County                                7798438
    Category                              7799877
    Category Name                         7799877
    Vendor Number                         7800555
    Vendor Name                           7800555
    Item Number                           7800559
    Item Description                      7800559
    Pack                                  7800559
    Bottle Volume (ml)                    7800559
    State Bottle Cost                     7800559
    State Bottle Retail                   7800559
    Bottles Sold                          7800559
    Sale (Dollars)                        7800559
    Volume Sold (Liters)                  7800559
    Volume Sold (Gallons)                 7800559
    Iowa ZIP Code Tabulation Areas        2343215
    Iowa Watershed Sub-Basins (HUC 08)    2343215
    Iowa Watersheds (HUC 10)              2343215
    County Boundaries of Iowa             2343215
    US Counties                           2347069
    dtype: int64




```python
#See if any of the columns have 0 or null values

iowa_sales.isnull().sum()
```




    Invoice/Item Number                         0
    Date                                        0
    Store Number                                0
    Store Name                                  0
    Address                                  2121
    City                                     2121
    Zip Code                                 2143
    Store Location                         764836
    County Number                         1246293
    County                                   2121
    Category                                  682
    Category Name                             682
    Vendor Number                               4
    Vendor Name                                 4
    Item Number                                 0
    Item Description                            0
    Pack                                        0
    Bottle Volume (ml)                          0
    State Bottle Cost                           0
    State Bottle Retail                         0
    Bottles Sold                                0
    Sale (Dollars)                              0
    Volume Sold (Liters)                        0
    Volume Sold (Gallons)                       0
    Iowa ZIP Code Tabulation Areas        5457344
    Iowa Watershed Sub-Basins (HUC 08)    5457344
    Iowa Watersheds (HUC 10)              5457344
    County Boundaries of Iowa             5457344
    US Counties                           5453490
    dtype: int64




```python
#Remove columns that aren't needed for Tableau analysis to speed up processing

iowa_salesv2 = iowa_sales.drop(iowa_sales.columns[[0, 2, 3, 4, 7, 8, 10, 12, 14, 16, 23, 24, 25, 26, 27, 28]],axis=1)
```


```python
print(iowa_salesv2.head())
```

             Date        City  Zip Code   County     Category Name  \
    0  01/02/2020     OTTUMWA   52501.0  WAPELLO  BLENDED WHISKIES   
    1  01/02/2020     OTTUMWA   52501.0  WAPELLO   AMERICAN VODKAS   
    2  01/02/2020        AMES   50010.0    STORY    IRISH WHISKIES   
    3  01/02/2020  DES MOINES   50313.0     POLK   AMERICAN VODKAS   
    4  01/02/2020        AMES   50014.0    STORY   IMPORTED VODKAS   
    
              Vendor Name      Item Description  Bottle Volume (ml)  \
    0     LAIRD & COMPANY             FIVE STAR                1000   
    1     LAIRD & COMPANY    FIVE O'CLOCK VODKA                1750   
    2   PERNOD RICARD USA  JAMESON BLACK BARREL                 750   
    3  E & J GALLO WINERY   NEW AMSTERDAM 80PRF                 375   
    4     BACARDI USA INC            GREY GOOSE                 750   
    
       State Bottle Cost  State Bottle Retail  Bottles Sold  Sale (Dollars)  \
    0               4.40                 6.60            12           79.20   
    1               7.20                10.80             6           64.80   
    2              21.48                32.22             2           64.44   
    3               3.50                 5.25             2           10.50   
    4              18.49                27.74             2           55.48   
    
       Volume Sold (Liters)  
    0                 12.00  
    1                 10.50  
    2                  1.50  
    3                  0.75  
    4                  1.50  



```python
iowa_salesv2.isnull().sum()
```




    Date                       0
    City                    2121
    Zip Code                2143
    County                  2121
    Category Name            682
    Vendor Name                4
    Item Description           0
    Bottle Volume (ml)         0
    State Bottle Cost          0
    State Bottle Retail        0
    Bottles Sold               0
    Sale (Dollars)             0
    Volume Sold (Liters)       0
    dtype: int64




```python
#Removing some entries with null information

iowa_salesv3 = iowa_salesv2.dropna(subset=['Category Name', 'Vendor Name'])
```


```python
iowa_salesv3.isnull().sum()
```




    Date                       0
    City                    2121
    Zip Code                2143
    County                  2121
    Category Name              0
    Vendor Name                0
    Item Description           0
    Bottle Volume (ml)         0
    State Bottle Cost          0
    State Bottle Retail        0
    Bottles Sold               0
    Sale (Dollars)             0
    Volume Sold (Liters)       0
    dtype: int64




```python
#Prelim analysis

sales = iowa_salesv3.groupby('Category Name').agg({'Sale (Dollars)' : 'sum', 'Volume Sold (Liters)' : 'sum'}).reset_index()
top_sales = sales.sort_values(by='Sale (Dollars)', ascending=False)
print(top_sales)
```

                               Category Name  Sale (Dollars)  Volume Sold (Liters)
    9                        AMERICAN VODKAS    1.822067e+08           16898434.81
    13                     CANADIAN WHISKIES    1.389400e+08            8949540.24
    43             STRAIGHT BOURBON WHISKIES    1.006575e+08            3915984.19
    48                       WHISKEY LIQUEUR    7.326980e+07            3394383.73
    0                     100% AGAVE TEQUILA    6.862055e+07            1776083.99
    42                            SPICED RUM    6.719631e+07            4324109.81
    46                    TENNESSEE WHISKIES    4.790320e+07            1538528.50
    23                     IMPORTED BRANDIES    4.624558e+07             973656.89
    30                       IMPORTED VODKAS    4.160334e+07            2396043.01
    11                      BLENDED WHISKIES    3.670993e+07            2485474.94
    45        TEMPORARY & SPECIALTY PACKAGES    3.447751e+07            1115990.79
    24          IMPORTED CORDIALS & LIQUEURS    3.249350e+07            1036676.17
    6                AMERICAN FLAVORED VODKA    3.205637e+07            2152636.39
    35                         MIXTO TEQUILA    3.077125e+07            1817436.07
    33                        IRISH WHISKIES    2.716965e+07             875066.27
    14                         COCKTAILS/RTD    2.548733e+07            3263937.25
    21                          FLAVORED RUM    2.531124e+07            1623164.48
    17                        CREAM LIQUEURS    2.493054e+07            1070142.54
    49                             WHITE RUM    1.941356e+07            1755564.07
    7                      AMERICAN SCHNAPPS    1.877639e+07            1478756.48
    29                     IMPORTED SCHNAPPS    1.823292e+07             953506.82
    38                       SCOTCH WHISKIES    1.712411e+07             704773.09
    27               IMPORTED FLAVORED VODKA    1.651695e+07             763271.60
    26                     IMPORTED DRY GINS    1.578182e+07             611528.26
    2                      AMERICAN BRANDIES    1.526133e+07            1218776.88
    44                 STRAIGHT RYE WHISKIES    1.349770e+07             328323.94
    40                    SINGLE MALT SCOTCH    1.299266e+07             212499.41
    3           AMERICAN CORDIALS & LIQUEURS    1.243592e+07             712666.89
    5                      AMERICAN DRY GINS    1.078408e+07            1009783.43
    25  IMPORTED DISTILLED SPIRITS SPECIALTY    6.183914e+06             736091.71
    15                       COFFEE LIQUEURS    6.106235e+06             276747.02
    37        NEUTRAL GRAIN SPIRITS FLAVORED    5.382856e+06             189276.17
    41                   SPECIAL ORDER ITEMS    4.944547e+06             453606.48
    4   AMERICAN DISTILLED SPIRITS SPECIALTY    4.059242e+06             149432.50
    22                              GOLD RUM    3.471264e+06             300488.20
    39        SINGLE BARREL BOURBON WHISKIES    3.249013e+06              71106.00
    1                          AGED DARK RUM    2.900488e+06             113994.70
    47                            TRIPLE SEC    2.417614e+06             588888.00
    12               BOTTLED IN BOND BOURBON    2.129175e+06              67238.50
    36                 NEUTRAL GRAIN SPIRITS    2.090025e+06             121261.62
    34                                MEZCAL    1.217810e+06              28690.95
    20                          FLAVORED GIN    1.192382e+06              41446.40
    16                         CORN WHISKIES    1.171381e+06              27717.57
    8                     AMERICAN SLOE GINS    8.861622e+04              10882.75
    19           DISTILLED SPIRITS SPECIALTY    5.603770e+04               1271.61
    32              IOWA DISTILLERY WHISKIES    2.208690e+04                656.25
    28                         IMPORTED GINS    6.904560e+03                234.00
    31                     IMPORTED WHISKIES    6.669360e+03                 54.00
    10                     AMERICAN WHISKIES    1.881000e+03                 49.50
    18        DELISTED / SPECIAL ORDER ITEMS    3.330000e+02                  9.00



```python
sales_by_county = iowa_salesv3.groupby('County').agg({'Sale (Dollars)' : 'sum', 'Volume Sold (Liters)' : 'sum'}).reset_index()
top_sales_county = sales_by_county.sort_values(by='Sale (Dollars)', ascending=False)
print(top_sales_county)
```

            County  Sale (Dollars)  Volume Sold (Liters)
    76        POLK    2.889902e+08           15251924.55
    56        LINN    1.068024e+08            6258050.23
    81       SCOTT    8.701891e+07            4883499.58
    51     JOHNSON    7.221947e+07            3953081.29
    6   BLACK HAWK    6.752603e+07            3809306.34
    ..         ...             ...                   ...
    1        ADAMS    6.664909e+05              41668.88
    79    RINGGOLD    6.596107e+05              43140.89
    86      TAYLOR    5.047469e+05              32596.10
    25       DAVIS    4.249710e+05              29346.21
    35     FREMONT    3.637386e+05              16540.20
    
    [99 rows x 3 columns]



```python
sales_by_vendor = iowa_salesv3.groupby('Vendor Name').agg({'Sale (Dollars)' : 'sum', 'Volume Sold (Liters)' : 'sum'}).reset_index()
top_sales_vendor = sales_by_vendor.sort_values(by='Sale (Dollars)', ascending=False)
print(top_sales_vendor)
```

                        Vendor Name  Sale (Dollars)  Volume Sold (Liters)
    84              DIAGEO AMERICAS    2.494271e+08           10603532.41
    259        SAZERAC COMPANY  INC    1.515304e+08           11014079.31
    159             JIM BEAM BRANDS    9.285187e+07            5013625.03
    134          HEAVEN HILL BRANDS    8.106692e+07            7251516.70
    108        FIFTH GENERATION INC    7.712180e+07            4176085.69
    ..                          ...             ...                   ...
    31          BOM DIA IMPORTS LLC    1.380600e+02                  4.50
    255      SAN LUIS SPIRITS, INC.    1.380600e+02                  4.50
    120     GLOBAL SPIRITS USA, LLC    9.000000e+01                  4.50
    235  PUENTE INTERNATIONAL, INC.    8.411000e+01                  3.00
    47    CARIBBEAN DISTILLERS, LLC    1.596000e+01                  0.75
    
    [324 rows x 3 columns]



```python
#Convert date column into Datetime data type for ease of analysis. Check to make sure data type has updated.

iowa_salesv3['Date'] = pd.to_datetime(iowa_salesv3['Date'])
iowa_salesv3['Date'].astype
```

    /var/folders/zc/n36z449509df72wqyy2b8y9c0000gn/T/ipykernel_20423/2019974280.py:1: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame.
    Try using .loc[row_indexer,col_indexer] = value instead
    
    See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
      iowa_salesv3['Date'] = pd.to_datetime(iowa_salesv3['Date'])





    <bound method NDFrame.astype of 0         2020-01-02
    1         2020-01-02
    2         2020-01-02
    3         2020-01-02
    4         2020-01-02
                 ...    
    7800554   2022-12-30
    7800555   2022-12-30
    7800556   2022-12-30
    7800557   2022-12-30
    7800558   2022-12-30
    Name: Date, Length: 7799873, dtype: datetime64[ns]>




```python
iowa_salesv3['Date'].astype
```




    <bound method NDFrame.astype of 0         2020-01-02
    1         2020-01-02
    2         2020-01-02
    3         2020-01-02
    4         2020-01-02
                 ...    
    7800554   2022-12-30
    7800555   2022-12-30
    7800556   2022-12-30
    7800557   2022-12-30
    7800558   2022-12-30
    Name: Date, Length: 7799873, dtype: datetime64[ns]>




```python
iowa_salesv3.to_csv('/Users/christopherkonopka/Desktop/Data Analytics/Capstone 2/Iowa Liquor Sales/Iowa_Liquor_Sales_Total.csv')
```


```python

```
