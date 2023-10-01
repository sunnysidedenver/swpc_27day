# <center>27 Day F10.7 cm "Solar Flux" Forecast Performance Evaluation (2020-2023)</center><br>
[Click here to access the full project notebook file.](https://github.com/sunnysidedenver/swpc_27day/blob/main/27%20Day%20F10%20Forecast%20Verification%20for%202020_2023.ipynb) </br>
Perfomance metrics and visualizations are outputed here.

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

The notebook file, linked above, is best referenced to understand how the data were staged, acquired and transformed into a useable format for analysis.

## Analysis
These forecasts were compared against observed values in order to obtain a "skill score" and other statistical performance metrics. Some analysis techniques required the subjective transformation of quanitatitve data into qualitative (hit or miss). For purposes of this study, if a forecast was within 5 sfu, it was considered a hit. Detailed analysis can be found in the linked notebook above.

The period of study was chosen carefully to minimize the size of the dataset and yet still be representative of solar minimum (2020) and maximum (2023) conditions and the years in between. 

*Analysis Period 2020-2023*: </br> 

This [plot](https://www.swpc.noaa.gov/products/solar-cycle-progression) shows previous and forecast solar activity. It has edited to highlight the years analyzed in this study. The y-axis shows sunspot number, an indicator of solar activity, and the x-axis show years. 2020 is generally considered to be the end of the previous SC24 and the start of SC25 with minimum activity. A sharp rise in activity is observed between 2020-23 with solar maximum forecast to occur in around 2025 as indicated by the red line. However, updated forecasts not reflected on this plot indicate [SC25 will peak in 2024](https://www.space.com/sun-solar-maximum-may-arrive-early). The gray shading indicates error bars. Note SC25 peak activity has already surpassed SC24.
![2020-2023 Study Period](https://github.com/sunnysidedenver/swpc_27day/blob/main/study%20period.png)
## Conclusions
The forecasts suffer from a high degree of variability, with low accuracy and high false alarm. Forecast error generally increases from 2020-2023 as solar activity increased. R-squared, a statistical representation of variance, allows for reasonable rejection of Ho and acceptance of Ha.

The average error was off by nearly 14 sfu with a large standard deviation (sd) of 17 sfu. When you move just 1 sd away from the mean, representing 68% of forecasts, the error jumps another 17 sfu. There is also a tendency to underforecast. </br>

95 percent of the forecasts have an error < 47 (2 sd) => 5 percent have an error > 47 (3 sd+) </br>
68 percent of the forecasts have an error < 31 (1 sd).</br>

Note: Flare enhanced F10.7 values have not been removed from this table and likely reflect the largest of the forecast errors seen here. More detail can be found in the notebook file.

![Table](https://github.com/sunnysidedenver/swpc_27day/blob/main/f10_error_table.png) 

Many really bad forecasts are seen here. Of concern are the outliers (> 2sd -- 5 percent of the forecasts -- from the mean or any forecast error > 47 sfu) or forecasts with errors greater than 10 sfu, the number of forecasts 3+ sd from the mean.  

![Plot2](https://github.com/sunnysidedenver/swpc_27day/blob/main/f10_errors(2).png)

Overall, error increases with time with increased solar activity.

![Plot1](https://github.com/sunnysidedenver/swpc_27day/blob/main/f10_errors(1).png)

However, other metrics like mean absolute percentage error, suggest the forecasts are at least good or fair overall.

## Future Efforts
ROC curves, which look at the relationship between hits and misses, should be considered as well as other hypothesis testing measures other than R-squared, like p-values.

Other tolerances for transformation of quantitative data into qualitative should be considered as well. These tolerances may not be the same during all parts of the solar cycle.

Heidke skill score may also be useful. This analysis compares the forecast against the long term average, which the daily forecasts outpeform, on average. A more accurate model could be trained based on solar input parameters. The [ADAPT model](https://gong.nso.edu/adapt/sift/adapt_f10_forecast.txt) could also be evaluated, and if determiend to be more consistently accurate, it could inform the Heidke skill score, or even replace the manual forecast process all together.

Last updated: Sep 2023

