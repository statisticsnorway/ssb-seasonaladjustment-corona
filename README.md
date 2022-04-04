
#### *Below is the note about last corona outlier of 15 March 2022,  the update note of 17 December 2020 and the memo of 30 March 2020.This is also available as pdf files in English and Norwegian within this repository. See also the [notice about new old outliers](https://github.com/statisticsnorway/SeasonalAdjustmentCorona/blob/master/New_old_outliers_side_effect.md) of 14 April 2021.*  


***

***


Below is an abbreviated and translated note, originally in Norwegian, with recommendations for the statistical units in Statistics Norway compiled by a corona time series working group within division for methodology. This document is available at https://github.com/statisticsnorway/SeasonalAdjustmentCorona 



### Statistics Norway - Division for methods - 15 March 2022

# Seasonal adjustment during the Corona crisis – March or 1st quarter 2022 will be the last outlier

### Background

The memo of 30 March 2020 gave recommendations on special seasonal adjustments during the crisis for Norwegian statistics. Later, 17 December 2020, a new memo pointed out that continuous updating with outliers continues in 2021. 

Now it's finally time to end special handling of seasonal adjustments. Below is more information.

The Norwegian government introduced strict national COVID-19 measures from around mid-March 2020. After a while there were some easing of the restrictions. First in September 2021, they decided that Norway will move to a normal everyday life with increased preparedness. Due to the Omicron variant of the coronavirus (COVID-19) a second period of strict national COVID-19 measures was imposed from December 2021 to mid-February 2022.

Note in particular that we, for outlier detection, recommend that fixed critical t-value limits be used.

###  March or 1st quarter 2022 will be the last outlier
We assume that the chosen method is continuous updating with outliers. Then the last month to have a corona outlier is the first month that is considered normal. This will ensure that the trend after the crisis period has the right starting point. 

When the April figure is in place, it is important that the March outlier is converted to level shift (LS) if an additive outlier (AO) was specified. 

For quarterly statistics, the recommendation is that the first quarter of 2022 will be the last quarter with a corona outlier. When the second quarter of 2022 is in place, the first quarter of 2022 must be converted to LS if AO was specified.

The reason for the choice of March is that we assume that March is a completely normal month. Strictly speaking, a similar assessment would lead to the second quarter of 2022 also becoming an outlier (first completely normal quarter). But the recommendation is a little different after considering the pros and cons. 

This is a common recommendation. More outliers can be added if knowledge indicates this.

### More details

#### Trend throughout the corona period

Calculation of trend has ceased during the corona period. If a trend was desired, the solution was to use level shifts for all outliers so that the trend and the seasonally adjusted figures coincided. Better trend estimates can subsequently be achieved with a re-modeling of the entire corona period, including the seasonal adjustment. If this is to be done, it is better to wait with such modeling until more observations are in place.

A simpler approach is to keep seasonally adjusted figures and rather find a trend by smoothing the seasonally adjusted figures afterwards. E.g. by moving average (3 or 5 months) or another smoothing filter.

#### Other seasonal pattern after the corona period?

Seasonal adjustment is about correcting for a known seasonal pattern. If the seasonal pattern is not known, then we cannot perform seasonal adjustment. We need to take a break, at least three years,  from the seasonal adjustment. 

On the other hand, gradual changes in the seasonal pattern are built into the seasonal adjustment method. A season filter is automatically selected based on the length and properties of the series. The shorter the filter, the more abrupt changes in the seasonal pattern are handled.

If a series that has had a stable seasonal pattern has a relatively abrupt change after the corona period, it may mean that the automation will eventually change the filter length. But it may take two years before the information is clear enough for the automation to change.

If you are sure that there are bigger changes in the seasonal pattern than before, it is possible to stay ahead. The automation can be overridden in the sense that seasonal filters can be specified manually, e.g. by, `x11{seasonalma = S3X3}`, so that a short  filter is selected. Overall, a manual control of the seasonal filter can give less revision than otherwise, provided that the assumption that a relatively big change in the seasonal pattern is correct. The easiest way is to continue without such override and in many cases it will also be best.

#### Outlier detection and t-value error

When it comes to outliers other than corona outliers, the best practice is to freeze old outliers and only look for new ones at the end of the series (last year). This practice is only to some extent implemented in Statistics Norway. After the corona period, there is a good opportunity to make such change. Any outliers before the corona should be held fixed. 

At the same time, we recommend setting a fixed critical detection limit.

* In the **X-13ARIMA-SEATS: 4.25** or **4.00** for monthly and quarterly series, respectively. 
* In **JDemetra+: 4.00** or **3.75** for monthly and quarterly series, respectively

The reason why these critical limits are recommended is twofold.

*	The automatic critical limit depends on the number of observations considered. This means very low limits for short spans. Although the hypothesis testing theory behind this is correct, the actual consequence is that the outlier threshold is lowered enormously by fixing outliers. This is something we do not recommend. Automatic change of detection limit can also lead to revisions. For long series, the usual detection limit are approx. 4.00 or 3.75 for monthly and quarterly series, respectively.
*	We have previously (April 14, 2021) pointed out that an error in the X-13ARIMA-SEATS program causes a systematic error in t-values when we have corona outliers. This results in a lower threshold for automatic outliers, especially for short time series. It is possible to give specific calculations for this. A simplification is to introduce a rule of thumb that the limit should be increased by 0.25 so that the recommendation is 4.25 or 4.00.

For JDemetra+, how much consequence this recommendation has in practice is actually a bit unclear. There is a mismatch between what the documentation says (that the limit depends on the span length) and what the program actually does. 

If freezing of outliers and outlier spans are not used, we still recommend using fixed critical limits. This is especially recommended when using X-13ARIMA-SEATS due to the systematic error.

Contact Øyvind Langsrud (oyl@ssb.no) for questions and suggestions.



***

***


Below is an update note (originally in Norwegian) with recommendations for the statistical units in Statistics Norway compiled by a corona time series working group within division for methodology. The working group is set up by Xeni Dimakos (head of division) and consists of Øyvind Langsrud, Ane Seierstad, Jørn Ivar Hamre, Xiaoming Jansen and Dinh Pham. This document is available at https://github.com/statisticsnorway/SeasonalAdjustmentCorona 

### Statistics Norway - Division for methods - 17 December 2020

# Seasonal adjustment during the Corona crisis – continuation in 2021


### Background
The memo of 30 March 2020 gave recommendations on special seasonal adjustments during the crisis. One of the points in the memo was “How long will the crisis last?” with subsequent text “No one knows how long the situation we are in will last, or what effect it will have on Statistics Norway's statistics. The methods outlined in this memo will be able to handle the impact of data until the new year 2020/2021. This gives us plenty of time to re-evaluate the plans or establish alternative methods”.
In practice, the outlier method was chosen for most series in Statistics Norway.
We are now approaching the New Year and it is therefore time for an update.
Below we go straight to the point and mention the strategy for 2021 and afterwards some more discussions.

### Each observation as outlier continues in 2021
The strategy is as follows:

* Treat each observation as outlier at least until February – that is one year.
* And continue to treat each observation as an outlier if not
  * Large movements in the seasonal pattern by the outlier strategy has been detected.
  *  Or if, after very careful assessments, one can conclude that a series is not affected by the corona crisis at all.
The alternative to outliers will require much more effort. The strategy with outliers can, if necessary, last throughout 2021. 

### Three variations of seasonal adjustment
For the sake of discussion, we now include an additional variant as the first point. 

* **Constant seasonal factors**
The calendar factors take into account the new calendar in new years, but are otherwise based on fixed parameter estimates. The seasonal factors are kept completely fixed from year to year. This method is not straightforwardly available in X13-ARIMA.

* **Forecasted seasonal factors**
A more precise term is “forecasted calendar and seasonal factors”. This is a common seasonal adjustment method. The difference from the method above is that it takes into account that the seasonal pattern changes slightly over time. The forecast for the seasonal pattern for 2021 will be slightly different from the forecast for 2020. The program X13-ARIMA can provide forecasted factors three years ahead.

* **Continuous updating with outliers**
For each new observation, the seasonal pattern is updated. This is the most common method in Statistics Norway. Outliers in the crisis period ensure that the real observations do not affect the seasonal pattern. Fitted values from modelling based on other observations are used instead. Due to the algorithm in X13-ARIMA, the seasonal pattern obtained in this way is not exactly the same as the forecasted seasonal factors.

### Discussion
Time series forecasts far ahead are uncertain. If the dynamics modelled correspond to reality, such modelling can be useful. Constant seasonal factors, on the other hand, are a safer and easier choice. Such a method can in theory be used for all time to come. We then say that the seasonal pattern as it was in 2019 is what applies. But constant seasonal factors are not what the program gives us.
Forecasted seasonal factors one year ahead are considered a good seasonal adjustment method. Outliers for one year give in practice about the same result as forecasted factors. For each time series it is possible to compare to see how big the difference is.
When we enter special treatments for the second year, there are many comparisons that can be made. If the seasonal pattern for the second year (2021) is especially different from the seasonal pattern for the first year (2020), then there is reason to be sceptical. If there are substantial differences, then other approaches should be considered. A method other than outlier treatment, will, however, require more effort. Forecasted seasonal factors are an option. A more manual programming of the seasonal pattern is also possible.

Contact Øyvind Langsrud (oyl at ssb.no) for questions and suggestions.



***

***


Below is a memo (originally in Norwegian) with recommendations for the statistical units in Statistics Norway compiled by a corona time series working group within division for methodology. The working group is set up by Xeni Dimakos (head of division) and consists of Øyvind Langsrud, Ane Seierstad, Jørn Ivar Hamre, Xiaoming Jansen and Dinh Pham.


### Statistics Norway - Division for methods - 30 March 2020


# Seasonal adjustment during the Corona crisis


### Background
Seasonal adjustment is used to correct time series data for repetitive seasonal variations. The methods used take into account that a seasonal pattern may change gradually over time. The seasonal pattern is constantly updated with the latest data and very old data gradually disappear from the basis used to estimate the seasonal pattern.

During the crisis, it is still possible to do seasonal adjustment by correcting the data for normal seasonal variations. But it is not right to update the seasonal pattern with numbers from an abnormal period that has started abruptly and which will last a limited period. If we do so, it means that the changes we observe during the crisis are changes that we believe represent patterns that will recur in the years to come. In order to avoid unfortunate consequences, actions should be taken immediately in the ongoing seasonal adjustment in Statistics Norway. The actions proposed are in accordance with "ESS guidelines on seasonal adjustment" and other recognized sources in the field.

Programs that calculate seasonally adjusted figures also calculate trends. Sometimes such trends are published together with the seasonally adjusted figures.

The challenges posed by a crisis are more extensive for trend figures than for seasonally adjusted figures. Below we first assume that only seasonally adjusted figures are to be published and methodological solutions are described for this. Then follows a separate chapter that deals with methodological issues of trend estimation.

### Two variations of seasonal adjustment

Two common methods of seasonal adjustment are:

* **Forecasted calendar and seasonal factors:** For the sake of simplicity, we only use the term seasonal factors here. The method implies that a forecast is made for the correction factors one year ahead. The seasonal adjustment is based on this forecast, which is held fixed for one year. Then the seasonal adjustment modeling is reviewed and new forecasts are made.

* **Continuous updating:** This method is most commonly used in Statistics Norway. For each new observation, the seasonal pattern is updated.

### Seasonal adjustment during the crisis

The method with forecasted seasonal factors is rarely used in Statistics Norway. However, if this is method was used and a revision was made in the beginning of 2020, you have been lucky. You will not have to take action now. The forecasted factors will work well and the problem of dealing with the crisis can be postponed to the turn of the year.
If you are using continuous updating, as most statistics do, then we recommend one of the following course of actions.

* **Either change the choice of method to forecasted seasonal factors:** Based on the latest observations before the crisis, it is possible to forecast seasonal factors from now on. This will most likely work well. However, it may not be easy / convenient to implement in the software currently used.

* **Or manually treat each observation as outlier from now on:**
Model the first observation of the crisis period as an outlier and continue treating the subsequent observations as outliers. Adding 12 outliers in a row will work well and gives results that are very similar to the method that forecasts seasonal factors one year ahead. When only seasonally adjusted figures are to be published, it does not matter whether additive outliers or level shifts are included. The result will be the same.

#### The recommendations apply to all series
Basically, these recommendations apply to all series that are seasonally adjusted. But if there are good reasons to believe that a series cannot be affected by the corona crisis at all, then it is a whole other matter.

#### Why not do automatic outlier detection?
It is obvious that the current situation will have a huge impact on a lot of data used in official statistics.  There is no need for a test to reveal it. We know that new observations are not suitable as a basis for seasonal patterns. An automatic test will add outliers for some series and not for others and comparisons will gets messy. Automatic outlier management will also lead to major revisions as time goes on. The automatic method will in many cases change the choice of which observations that are to be considered as outliers, and this in itself is problematic.

#### How wrong will it be if we let automaticity prevail?
If the automatic outlier detection method is used at the beginning of the crisis period (a single observation at the end), then the output will not be very affected. A major change causes an outlier to be detected automatically. Series where no major changes are observed will not have a significant or adverse effect on the seasonal pattern.  However, the unfortunate consequences will become bigger and bigger as time goes on, and more and more data points are added to the time series. The best possible series and least possible revision are achieved if manual change is introduced right from the start.

#### How long will the crisis last?
No one knows how long the situation we are in will last, or what effect it will have on Statistics Norway's statistics. The methods outlined in this memo will be able to handle the impact of data until the new year 2020/2021. This gives us plenty of time to re-evaluate the plans or establish alternative methods

#### Other seasonal patterns when the crisis is over?
When the crisis is over and if the proposed methods above have been used, then the seasonal adjustment processes can continue as before. But if the world is completely different and the seasonal pattern is completely different: What do we do? Seasonal adjustment is about correcting for a known seasonal pattern. If the seasonal pattern is not known, then we cannot perform seasonal adjustment. This may involve pausing doing seasonal adjustment for a certain period of time. However, this discussion is not urgent.

## Trend from the seasonal adjustment method

Trend is a suitable tool for describing underlying gradual change. In the case of sudden changes, changes will be smoothed out by normal trend estimation and the trend will not look as sudden as reality. When an outlier is defined as an additive outlier, it is assumed that the observation is a single event that deviates from the trend and that the next observation is back on the trend course. When an outlier is defined as a level shift, then a sudden change in trend happens once. Adding many additive outliers in a row doesn't really work very well with trend estimation. One option is to treat all outliers as level shifts. Then the trend and seasonally adjusted figures will coincide. Then you can alternatively smooth seasonally adjusted figures manually. A technical problem is that it is not possible to enter level shifts as the last observation.

In this crisis situation, calculating trend will probably turn out to be a problem for most economic timeseries. Having seasonal adjustment estimated along with a trend makes it extra challenging. The X-13ARIMA-SEATS program, which we use in Statistics Norway, may not have the functionality to solve this easily. It could be that there are opportunities in JDemetra +? In the Division for methods, we are looking for good practical solutions for the procedures that are in use. We will also follow international discussions and recommendations on how to deal with time series analyses during the current crisis.

Contact Øyvind Langsrud (oyl at ssb.no) for questions and suggestions.
