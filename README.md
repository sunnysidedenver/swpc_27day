<center><h1>27 Day Geomagnetic Forecast <br> Exploratory Data Analysis & Hypothesis Testing</h1></center><br>

The Space Weather Prediction Center produces and releases 27-day geomagnetic forecasts found in ["Weekly Highlights and 27-day Forecast](https://www.swpc.noaa.gov/products/weekly-highlights-and-27-day-forecast), which is in a PDF format. These forecast are not archived in a database and can only be found in these PDF documents. In order to assess forecast skill, the forecasts have to be extracted from these files into a readable format. This program will extract the data from the PDF files (found on page 4) using tabula-py then convert into text files. The text files will then be read into Pandas dataframes for additional analysis.  

**Null Hypothesis:** 27 day forecasts are skillful <br>
**Alternate Hypothesis:** 27 day forecast are not skillful

This project is ongoing.

![EXAMPLE 27 DAY FORECAST in PDF FORMAT](https://github.com/sunnysidedenver/swpc_27day/blob/main/Example%20Forecast.PNG)
