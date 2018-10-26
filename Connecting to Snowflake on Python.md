
## Connecting to Snowflake on Python

Connecting to a sample database using Python connectors 

Author : Naren Sham


```python
#!/usr/bin/env python

import snowflake.connector

#Connection Details : SSO 

ctx = snowflake.connector.connect(
	user='email@DOMAIN.COM',#Your Email ID
	account='accountname',
   region='us-east-1', # This could vary based on location
	authenticator='externalbrowser', # For SSO Authentication - idP
)

cur = ctx.cursor()#Query data
cnx=ctx

#This could reroute you to a browser which says " Your identity was confirmed and propagated to Snowflake PythonConnector. You can close this window now and go back where you started from." 
```

    Initiating login request with your identity provider. A browser window should have opened for you to complete the login. If you can't see it, check existing browser windows, or your OS settings. Press CTRL+C to abort and try again...



```python
cnx.cursor().execute("USE SNOWFLAKE_SAMPLE_DATA") # Select the database to query in

```




    <snowflake.connector.cursor.SnowflakeCursor at 0x1d6a397e3c8>




```python
cnx.cursor().execute("USE SNOWFLAKE_SAMPLE_DATA.WEATHER") # Select Database and Schema to query in
```




    <snowflake.connector.cursor.SnowflakeCursor at 0x1d6a397e7b8>




```python
# JSON Data
try:
    cur.execute("SELECT * FROM WEATHER.DAILY_14_TOTAL limit 1")
    for (col1, col2) in cur:
        print('{0}, {1}'.format(col1, col2))
finally:
    cnx.close()
```

    {
      "city": {
        "coord": {
          "lat": 12.75,
          "lon": 78.366669
        },
        "country": "IN",
        "id": 1265555,
        "name": "Kuppam"
      },
      "data": [
        {
          "clouds": 68,
          "deg": 236,
          "dt": 1495432800,
          "humidity": 95,
          "pressure": 924.88,
          "rain": 1.29,
          "speed": 3.06,
          "temp": {
            "day": 300.15,
            "eve": 300.15,
            "max": 300.15,
            "min": 298.61,
            "morn": 300.15,
            "night": 298.61
          },
          "uvi": 12.51,
          "weather": [
            {
              "description": "light rain",
              "icon": "10d",
              "id": 500,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 32,
          "deg": 334,
          "dt": 1495519200,
          "humidity": 56,
          "pressure": 924.03,
          "rain": 0.35,
          "speed": 3.29,
          "temp": {
            "day": 305.27,
            "eve": 304.11,
            "max": 305.27,
            "min": 296.5,
            "morn": 296.5,
            "night": 296.56
          },
          "uvi": 13.57,
          "weather": [
            {
              "description": "light rain",
              "icon": "10d",
              "id": 500,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 32,
          "deg": 7,
          "dt": 1495605600,
          "humidity": 43,
          "pressure": 923.39,
          "rain": 7.73,
          "speed": 1.97,
          "temp": {
            "day": 307.66,
            "eve": 299.81,
            "max": 307.66,
            "min": 293.96,
            "morn": 293.96,
            "night": 294.04
          },
          "uvi": 12.99,
          "weather": [
            {
              "description": "moderate rain",
              "icon": "10d",
              "id": 501,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 20,
          "deg": 277,
          "dt": 1495692000,
          "humidity": 57,
          "pressure": 922.19,
          "rain": 16.22,
          "speed": 2.77,
          "temp": {
            "day": 306.31,
            "eve": 294.57,
            "max": 306.31,
            "min": 294.35,
            "morn": 294.49,
            "night": 294.35
          },
          "uvi": 13.11,
          "weather": [
            {
              "description": "heavy intensity rain",
              "icon": "10d",
              "id": 502,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 10,
          "deg": 313,
          "dt": 1495778400,
          "humidity": 0,
          "pressure": 936.1,
          "rain": 6.91,
          "speed": 5.6,
          "temp": {
            "day": 306.84,
            "eve": 301.86,
            "max": 306.84,
            "min": 295.85,
            "morn": 295.85,
            "night": 296.69
          },
          "uvi": 13.99,
          "weather": [
            {
              "description": "moderate rain",
              "icon": "10d",
              "id": 501,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 4,
          "deg": 297,
          "dt": 1495864800,
          "humidity": 0,
          "pressure": 934.85,
          "rain": 8.76,
          "speed": 7.28,
          "temp": {
            "day": 305.02,
            "eve": 301.5,
            "max": 305.02,
            "min": 295.68,
            "morn": 295.68,
            "night": 295.73
          },
          "uvi": 13.18,
          "weather": [
            {
              "description": "moderate rain",
              "icon": "10d",
              "id": 501,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 6,
          "deg": 301,
          "dt": 1495951200,
          "humidity": 0,
          "pressure": 934.55,
          "rain": 0.53,
          "speed": 7.93,
          "temp": {
            "day": 303.32,
            "eve": 303.69,
            "max": 303.69,
            "min": 295.33,
            "morn": 295.33,
            "night": 299.31
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "light rain",
              "icon": "10d",
              "id": 500,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 0,
          "deg": 311,
          "dt": 1496037600,
          "humidity": 0,
          "pressure": 934.05,
          "rain": 32.93,
          "speed": 7,
          "temp": {
            "day": 305.85,
            "eve": 299.64,
            "max": 305.85,
            "min": 295.5,
            "morn": 296.54,
            "night": 295.5
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "heavy intensity rain",
              "icon": "10d",
              "id": 502,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 42,
          "deg": 288,
          "dt": 1496124000,
          "humidity": 0,
          "pressure": 935.09,
          "rain": 7.34,
          "speed": 4.2,
          "temp": {
            "day": 301.32,
            "eve": 300.1,
            "max": 301.32,
            "min": 294.91,
            "morn": 294.91,
            "night": 295.87
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "moderate rain",
              "icon": "10d",
              "id": 501,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 15,
          "deg": 235,
          "dt": 1496210400,
          "humidity": 0,
          "pressure": 935.13,
          "rain": 4.46,
          "speed": 1.88,
          "temp": {
            "day": 302.3,
            "eve": 300.65,
            "max": 302.3,
            "min": 294.15,
            "morn": 294.15,
            "night": 295.21
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "moderate rain",
              "icon": "10d",
              "id": 501,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 24,
          "deg": 207,
          "dt": 1496296800,
          "humidity": 0,
          "pressure": 933.34,
          "rain": 22.16,
          "speed": 1.5,
          "temp": {
            "day": 299.05,
            "eve": 298.16,
            "max": 299.05,
            "min": 293.46,
            "morn": 293.46,
            "night": 295.06
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "heavy intensity rain",
              "icon": "10d",
              "id": 502,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 46,
          "deg": 246,
          "dt": 1496383200,
          "humidity": 0,
          "pressure": 931.11,
          "rain": 12.06,
          "speed": 5.52,
          "temp": {
            "day": 298.89,
            "eve": 296.3,
            "max": 298.89,
            "min": 294.64,
            "morn": 294.64,
            "night": 295.37
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "heavy intensity rain",
              "icon": "10d",
              "id": 502,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 54,
          "deg": 229,
          "dt": 1496469600,
          "humidity": 0,
          "pressure": 931.64,
          "rain": 2.7,
          "speed": 6.74,
          "temp": {
            "day": 299.59,
            "eve": 300.16,
            "max": 300.16,
            "min": 295.13,
            "morn": 295.13,
            "night": 296.88
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "light rain",
              "icon": "10d",
              "id": 500,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 71,
          "deg": 223,
          "dt": 1496556000,
          "humidity": 0,
          "pressure": 932.31,
          "rain": 0.56,
          "speed": 10.38,
          "temp": {
            "day": 300.85,
            "eve": 300.09,
            "max": 300.85,
            "min": 296.58,
            "morn": 296.58,
            "night": 297.87
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "light rain",
              "icon": "10d",
              "id": 500,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 55,
          "deg": 218,
          "dt": 1496642400,
          "humidity": 0,
          "pressure": 933.99,
          "speed": 9.11,
          "temp": {
            "day": 302.18,
            "eve": 301.7,
            "max": 302.18,
            "min": 296.92,
            "morn": 296.92,
            "night": 297.29
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "light rain",
              "icon": "10d",
              "id": 500,
              "main": "Rain"
            }
          ]
        },
        {
          "clouds": 50,
          "deg": 232,
          "dt": 1496728800,
          "humidity": 0,
          "pressure": 932.42,
          "speed": 5.89,
          "temp": {
            "day": 295.07,
            "eve": 295.07,
            "max": 295.07,
            "min": 295.07,
            "morn": 295.07,
            "night": 295.07
          },
          "uvi": 12.59,
          "weather": [
            {
              "description": "light rain",
              "icon": "10dd",
              "id": 500,
              "main": "Rain"
            }
          ]
        }
      ],
      "time": 1495471966
    }, 2017-05-22 09:52:46



```python
#For Tablular Data

ctx = snowflake.connector.connect(
	user='email@DOMAIN.COM',
	account='accountname',
   region='us-east-1',
	authenticator='externalbrowser',
)

cur = ctx.cursor()
cnx=ctx

cnx.cursor().execute("USE SNOWFLAKE_SAMPLE_DATA.TPCDS_SF100TCL")

cur.execute("SELECT CC_CITY,CC_COUNTY FROM CALL_CENTER limit 10")
for (col1, col2) in cur:
    print('{0}, {1}'.format(col1, col2))
        
print(type(cur))
    

```

    Initiating login request with your identity provider. A browser window should have opened for you to complete the login. If you can't see it, check existing browser windows, or your OS settings. Press CTRL+C to abort and try again...
    Georgetown, Harmon County
    Friendship, Raleigh County
    Friendship, Raleigh County
    Spring Valley, Saginaw County
    Spring Valley, Saginaw County
    Spring Valley, Saginaw County
    Oak Hill, Hubbard County
    Five Points, West Feliciana Parish
    Five Points, West Feliciana Parish
    Buena Vista, Huron County
    <class 'snowflake.connector.cursor.SnowflakeCursor'>



```python
#Data description

cur.description
```




    [('CC_CITY', 2, None, 60, None, None, True),
     ('CC_COUNTY', 2, None, 30, None, None, True)]



[For more details on the python connector and its variables, click here :](https://docs.snowflake.net/manuals/user-guide/python-connector-api.html)
