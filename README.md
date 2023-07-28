<center><h1>27 Day Geomagnetic Forecast <br> Exploratory Data Analysis & Hypothesis Testing</h1></center><br>

The Space Weather Prediction Center produces 27-day geomagnetic forecasts found in ["Weekly Highlights and 27-day Forecast](https://www.swpc.noaa.gov/products/weekly-highlights-and-27-day-forecast). These forecast are not archived in a database and can only be found in these PDF documents. In order to assess forecast skill, the forecasts have to be extracted from these PDF files into a readable format. This program will extract the forecasts from the PDF files (found on page 4) using tabula-py then convert them into text files. The text files will then be read into Pandas dataframes for additional analysis. Once cleaned, these forecasts can be compared against observed values in order to obtain a "skill score". Observed data are archived in a database and have been made available in an .xlsx spreedsheet.

**Null Hypothesis:** 27 day forecasts are skillful <br>
**Alternate Hypothesis:** 27 day forecast are not skillful

This project is ongoing and the respository python notebook will be updated periodically with major milestones.

Example 27 Day Forecast found in a PDF file

![EXAMPLE 27 DAY FORECAST in PDF FORMAT](https://github.com/sunnysidedenver/swpc_27day/blob/main/Example%20Forecast.PNG)
