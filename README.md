# <center>27 Day F10.7 cm "Solar Flux" Forecast Performance Evaluation (2020-2023)</center><br>
[Click here to access notebook file.](https://github.com/sunnysidedenver/swpc_27day/blob/main/27%20Day%20F10%20Forecast%20Verification%20for%202020_2023.ipynb)

## Background
The Space Weather Prediction Center produces 27-day geomagnetic (Kp and Ap) and radio (F10.7 cm) forecasts found in [Weekly Highlights and 27-day Forecast](https://www.swpc.noaa.gov/products/weekly-highlights-and-27-day-forecast). These forecasts are perishable and are not archived in any database. They can only be found in these PDF documents, which are [archived](ftp.swpc.noaa.gov/pub/warehouse/) by year. 

*Example 27 Day F10.7 cm Forecast Table found in a "Weekly" PDF file*
![EXAMPLE 27 DAY FORECAST in PDF FORMAT](https://github.com/sunnysidedenver/swpc_27day/blob/main/Example%20Forecast.PNG)
## Purpose
This study will evaluate F10.7 cm forecasts from 2020-2023 in order to determine how good or bad the forecasts are. 

## Hypothesis
Null: The forecasts are skillful and become more accurate with increased solar activity. </br>
Alternate: The forecasts are not skillful and become less accurate with increased solar activity.

## Data
In order to test this hypothesis, the forecasts have to be extracted from 185 PDF "Weekly" files into a readable format. This Python program will extract the forecasts from these files (found on pages 4, 5, 6 or 7) then convert them into text files. The text files will then be read into Pandas dataframes for additional analysis. [Observed F10.7 cm flux data](ftp.seismo.nrcan.gc.ca/spaceweather/solar_flux/daily_flux_values/fluxtable.txt) were collected from the Government of Canada. 

## Analysis
These forecasts were compared against observed values in order to obtain a "skill score" and other statistical performance metrics. Some analysis techniques required the subjective transformation of quanitatitve data into qualitative (hit or miss). For purposes of this study, if a forecast was within 5 sfu, it was considered a hit.

The period of study was chosen carefully to minimize the size of the dataset and yet still be representative of solar minimum (2020) and maximum (2023) conditions and the years in between. 

*Analysis Period 2020-2023*: </br> 
This [plot](https://www.swpc.noaa.gov/products/solar-cycle-progression) shows previous and forecast solar activity. It has edited to highlight the years analyzed in this study. The y-axis shows sunspot number, an indicator of solar activity, and the x-axis show years. 2020 is generally considered to be the end of the previous SC24 and the start of SC25 with minimum activity. A sharp rise in activity is observed between 2020-23 with solar maximum forecast to occur in around 2025 as indicated by the red line. However, updated forecasts not reflected on this plot indicate [SC25 will peak in 2024](https://www.space.com/sun-solar-maximum-may-arrive-early). The gray shading indicates error bars. Note SC25 peak activity has already surpassed SC24.
![2020-2023 Study Period](https://github.com/sunnysidedenver/swpc_27day/blob/main/study%20period.png)
## Conclusions
The forecasts suffer from a high degree of variability, with low accuracy and high false alarm. Forecast error generally increases from 2020-2023 as solar activity increased. R-squared, a statistical representation of variance, allows for rejection of Ho and acceptance of Ha: The forecasts are bad.

However, other metrics like mean absolute error, suggest the forecasts are at least fair overall.

## Future Efforts
ROC curves, which look at the relationship between hits and misses, should be considered as well as other hypothesis testing measures other than R-squared, like p-values.

Other tolerances for transformation of quantitative data into qualitative should be considered as well. These tolerances may not be the same during all parts of the solar cycle.

Heidke skill score may also be useful. This analysis compares the forecast against the long term average, which the daily forecasts outpeform, on average. A more accurate model could be trained based on solar input parameters. The [ADAPT model](https://gong.nso.edu/adapt/sift/adapt_f10_forecast.txt) could also be evaluated, and if determiend to be more consistently accurate, it could inform the Heidke skill score, or even replace the manual forecast process all together.

Last updated: Sep 2023

