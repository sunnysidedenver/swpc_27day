<center><h1>27 Day F10.7 "Solar Flux" Forecast Performance Verification</h1></center><br>

The Space Weather Prediction Center produces 27-day geomagnetic (Kp and Ap) and radio (F10.7 cm) forecasts found in [Weekly Highlights and 27-day Forecast](https://www.swpc.noaa.gov/products/weekly-highlights-and-27-day-forecast). These forecasts are not archived in a database and can only be found in these PDF documents, which are [archived](ftp://ftp.swpc.noaa.gov/pub/warehouse/) by year. In order to assess forecast skill, the forecasts have to be extracted from these PDF files into a readable format. This program will extract the forecasts from the PDF files (found on pages 4, 5, 6 or 7) then convert them into text files. The text files will then be read into Pandas dataframes for additional analysis. Once cleaned, these forecasts can be compared against observed values in order to obtain a "skill score". Observed [F10.7 flux data](ftp://ftp.seismo.nrcan.gc.ca/spaceweather/solar_flux/daily_flux_values/fluxtable.txt) were collected from the Government of Canada.  

The first study will assess F10.7 cm forecasts from 2020-2023.

*Example 27 Day Forecast found in a PDF file table*

![EXAMPLE 27 DAY FORECAST in PDF FORMAT](https://github.com/sunnysidedenver/swpc_27day/blob/main/Example%20Forecast.PNG)
