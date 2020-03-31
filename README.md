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
