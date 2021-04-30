
Below is an abridged and translated version of a notice made available internally in Statistics Norway on 14 April 2021. 
This is a comment on the recommendations at https://github.com/statisticsnorway/SeasonalAdjustmentCorona


## New old outliers can be a side effect of the recommendations

* This can lead to unwanted revisions during the crisis.
* The problem increases as more and more corona outliers are added.
* The problem is caused by a bug in the X-13ARIMA-SEATS program

Automatic outlier detection (in X12/X13) is done with a fixed critical t-value limit or with the default automatic limit that depends on the number of observations. When treating the corona crisis by 
continuously updating with prespecified outliers, the reg-arima estimates remain almost unchanged. One would expect correspondingly small changes in the associated standard errors. This is also the case if the X12/X13 method is run in JDemetra+. But unfortunately, this is not the case in X-13ARIMA-SEATS and this is simply caused by a bug in the program. 

The t-value of all the reg-arima estimates gradually increase over time as more and more corona outliers are added. This is caused by standard errors (denominator in t-values) being systematically too small. The consequence is that automatic outlier detection can detect too many outliers in the periods before the corona crisis. Changes in outliers lead to revisions in the seasonal pattern. The bias in t-values appears to be proportional to: The square root of ("total number of observations" / "number of observations before the crisis"). Thus, the problem increases as more corona outliers are added. The problem is also worst for short series.

We can solve this problem in X-13ARIMA-SEATS by turning off the automatic outlier detection and use prespecified outlier instead. This is in line with best practice, according to ESS guidelines, also when there is no crisis (partial concurrent adjustment).

<sub>Many thanks to Magnus Helliesen who saw the outlier problem.</sub>

<sub>Contact Øyvind Langsrud (oyl at ssb.no) for questions and suggestions.</sub>
