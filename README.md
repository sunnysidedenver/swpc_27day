<center><h1>27 Day Geomagnetic Forecast Performance Verification</h1></center><br>

The Space Weather Prediction Center produces 27-day geomagnetic forecasts found in [Weekly Highlights and 27-day Forecast](https://www.swpc.noaa.gov/products/weekly-highlights-and-27-day-forecast). These forecast are not archived in a database and can only be found in these PDF documents. In order to assess forecast skill, the forecasts have to be extracted from these PDF files into a readable format. This program will extract the forecasts from the PDF files (found on page 4) using tabula-py then convert them into text files. The text files will then be read into Pandas dataframes for additional analysis. Once cleaned, these forecasts can be compared against observed values in order to obtain a "skill score". Observed Kp data are archived in a database locally and have been made available in an .xlsx spreadsheet. Observed F10.7 data were collected from the Government of Canada.

Seperate notebooks can be found for Kp and F10.7 verification. These notebooks will continue to be edited until deemed otherwise here.

*Example 27 Day Forecast found in a PDF file table*

![EXAMPLE 27 DAY FORECAST in PDF FORMAT](https://github.com/sunnysidedenver/swpc_27day/blob/main/Example%20Forecast.PNG)
