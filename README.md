# <center>27 Day F10.7 cm "Solar Flux" Forecast Performance Evaluation (2020-2023)</center>
[Click here to access the full project notebook file.](https://github.com/sunnysidedenver/swpc_27day/blob/main/27%20Day%20F10%20Forecast%20Verification%20for%202020_2023%20(1)%20.ipynb) </br>
Perfomance metrics and visualizations are outputed here.

## Background
The Space Weather Prediction Center produces 27-day geomagnetic (Kp and Ap) and radio (F10.7 cm) forecasts found in [Weekly Highlights and 27-day Forecast](https://www.swpc.noaa.gov/products/weekly-highlights-and-27-day-forecast). These forecasts are perishable and are not archived in any database. They can only be found in PDF documents, which are [archived](ftp.swpc.noaa.gov/pub/warehouse/) by year. 

*Example 27 Day F10.7 cm Forecast Table found in a "Weekly" PDF file*

![Example Forecast from Weekly](https://github.com/sunnysidedenver/swpc_27day/blob/main/Example%20Forecast.PNG) 

## Purpose
This study will evaluate F10.7 cm forecasts from 2020-2023 in order to determine how good or bad the forecasts are. 

## Hypothesis
Null: The forecasts are skillful and become more accurate with increased solar activity. </br>
Alternate: The forecasts are not skillful and become less accurate with increased solar activity.

## Data
In order to test this hypothesis, the forecasts have to be extracted from 185 PDF "Weekly" files into a readable format. This Python program will extract the forecasts from these files (found on pages 4, 5, 6 or 7) then convert them into text files. The text files will then be read into Pandas dataframes for additional analysis with almost 5000 daily forecasts corresponding to observations. [Observed F10.7 cm flux data](ftp.seismo.nrcan.gc.ca/spaceweather/solar_flux/daily_flux_values/fluxtable.txt) were collected from the Government of Canada. 

The notebook file, linked above, is best referenced to understand how the data were staged, acquired and transformed into a useable format for analysis.

### Analysis Period
These forecasts were compared against observed values in order to obtain a "skill score" and other statistical performance metrics. Some analysis techniques required the subjective transformation of quanitatitve data into qualitative (hit or miss). For purposes of this study, if a forecast was within 5 sfu, it was considered a hit. Detailed analysis can be found in the linked notebook above.

The period of study was chosen carefully to minimize the size of the dataset and yet still be representative of solar minimum (2020) and maximum (2023) conditions and the years in between. 

This [plot](https://www.swpc.noaa.gov/products/solar-cycle-progression) shows previous and forecast solar activity. It has edited to highlight the years analyzed in this study. The y-axis shows sunspot number, an indicator of solar activity, and the x-axis show years. 2020 is generally considered to be the end of the previous SC24 and the start of SC25 with minimum activity. A sharp rise in activity is observed between 2020-23 with solar maximum forecast to occur in around 2025 as indicated by the red line. However, updated forecasts not reflected on this plot indicate [SC25 will peak in 2024](https://www.space.com/sun-solar-maximum-may-arrive-early). The gray shading indicates error bars. Note SC25 peak activity has already surpassed SC24.
![2020-2023 Study Period](https://github.com/sunnysidedenver/swpc_27day/blob/main/study%20period.png)
## Findings & Conclusions
The forecasts suffer from a high degree of variability, with low accuracy and high false alarm. Forecast error increases from 2020-2023 as solar activity increased. 

![Plot 3](https://github.com/sunnysidedenver/swpc_27day/blob/main/yearlyf10_errors.PNG)

R-squared, a statistical representation of variance, allows for reasonable rejection of Ho and acceptance of Ha. However, other metrics like mean absolute percentage error, suggest the forecasts are at least good or fair overall.

![Table](https://github.com/sunnysidedenver/swpc_27day/blob/main/f10_error_table.png) 

The average error was off by nearly 14 sfu with a large standard deviation (sd) of 17 sfu. When you move just 1 sd away from the mean, representing 68% of forecasts, the error jumps another 17 sfu. There is also a tendency to underforecast. </br>

Forecast errors are normally distributed, meaning one can assess the following:

- 95 percent (2 sd) of the forecasts have an error < 47 => 5 percent, or about 250 forecasts, have an error > 47 (3 sd+ "outliers") </br>
- 68 percent (1 sd) of the forecasts have an error < 31 </br>

![Plot2](https://github.com/sunnysidedenver/swpc_27day/blob/main/err_hist.PNG) 

Errors can also be evaluated for each day of the forecast. Note errors are already 12 sfu on day 1, increasing to 16 sfu by day 5, before decreasing to around 13 sfu. They increase back up to 15 sfu by the end of the forecast period.

![Plot4](https://github.com/sunnysidedenver/swpc_27day/blob/main/dailyf10_errors.PNG)

Overall, error increases with time and increased solar activity.

![Plot1](https://github.com/sunnysidedenver/swpc_27day/blob/main/f10_errors(1).png)

## Future Efforts
Daily condfidence intervals should be calculated.

ROC curves, which look at the relationship between hits and misses, should be considered as well as other hypothesis testing measures other than R-squared, like p-values.

Other tolerances for transformation of quantitative data into qualitative should be considered. These tolerances may not be the same during all parts of the solar cycle.

Heidke skill score may also be useful if these forecasts can be compared against a more accurate reference model. This analysis compares the forecast against the long term average, which the daily forecasts outpeform, on average. A more accurate model could be trained based on solar input parameters and/or the [ADAPT model](https://gong.nso.edu/adapt/sift/adapt_f10_forecast.txt) could also be evaluated, and if determiend to be more consistently accurate, it could serve as a reference for skill score calculation. If it is significantly better ADAPT could even replace the manual forecast process all together.

Finally, this project remains a work in progress. More work should be done to subset the data by years and create additional visualizations. This work will springboard the analysis of 27-day Kp forecasts, also found in the Weekly.

## Recommendations

Recommendations were made to provide a range of daily forecast values based on confidence intervals rather than attempting to forecast discrete values that are subject to large errors.

Last updated: Oct 2023

