Download link :https://programming.engineering/product/lab-4-instructions-confidence-intervals-hypothesis-testing/


# LAB-4-INSTRUCTIONS-CONFIDENCE-INTERVALS-HYPOTHESIS-TESTING
LAB 4 INSTRUCTIONS CONFIDENCE INTERVALS &amp; HYPOTHESIS TESTING
In the lab instructions, we will explore how to create confidence intervals and perform hypothesis tests using statistical tools in Excel to make inferences for one and two-sample problems.

For Activating the Data Analysis Add-In or Inserting Excel Output into a Word Document, see the Lab 1 instructions.

1. One-Sample Confidence Intervals in Excel

The purpose of a confidence interval is to estimate an unknown population parameter with an indication of how accurate the estimate is and of how confident we are the result is correct. The confidence interval has the following form.

estimator ± (critical value) × (standard error)

margin of error

The critical value is determined from the confidence level. The confidence level states the success rate of the method used to construct a confidence interval containing the population parameter. That is, if you use 95% confidence intervals often, in the long run, 95% of your intervals will contain the true parameter value. You cannot know whether a particular confidence interval contains the parameter. The estimator and standard error are typically determined from the sample data. The margin of error is the product of the critical value and standard error.

The standard error can sometimes be based off parameter values, such as the population standard deviation (σ); if it is known, the z-distribution is used to determine the critical value. More realistically, however, the standard error is estimated from the sample, using both the sample standard deviation (s) and the sample size (n); in these situations, the t-distribution is used to determine the critical value.

Below is the exact same output as seen in the Lab 1 Instructions with the addition of the margin of error for a two-sided 95% confidence interval. Thus, the two-sided 95% confidence interval can be displayed as 68.92 ± 4.812662; quick calculations produce the lower and upper bounds of the interval to re-display the interval as (64.10734, 73.73266).

Scores

Mean

68.92

Standard Error

2.394865

Median

72.5

Mode

75

Standard Deviation

16.93425

Sample Variance

286.769

Kurtosis

-0.21749

Skewness

-0.60693

Range

71

Minimum

28

Maximum

99

Sum

3446

Count

50

Confidence Level(95.0%)

4.812662

Note: When inputting a confidence level, Excel assumes the corresponding confidence interval will be two-sided. If creating a one-sided confidence interval/bound, careful consideration will be needed. For example, if a one-sided 95% confidence interval/bound is needed, then the desired confidence level should be 90%.

1.2 One-Sample Confidence Intervals using Excel functions

First review the Lab 1 Instructions to see how to respectively use the AVERAGE, STDEV, and COUNT functions for the sample mean, sample standard deviation, and sample size.

Note that if constructing a confidence interval where σ is known, the sample standard deviation is not required in the calculations; rather, a population standard deviation value is needed, likely stated somewhere in the question. Also, this confidence interval permits the use of the NORM.S.INV or NORMSINV functions. Please review the Lab 3 Instructions to see how to use them fully, yet a brief example is provided here for guidance.

For a 95% two-sided confidence interval, 1 – α = 0.95 and zα/2 = z0.025. In other words, P(Z < z) = 0.025.

Thus, z = NORM.S.INV(0.025) = –1.95996 or, alternatively, z = NORM.S.INV(1 – 0.025) = 1.95996.

As the confidence interval is two-sided, either critical value calculation will work since they have the exact same magnitude despite different signs. If the confidence interval is one-sided, carefully consider what sign would apply.

Using the Scores output above, 68.92 ± (1.95996)×(2.394865) = 68.92 ± 4.693850 = (64.22615, 73.61385). This interval does not equal the one above since this uses the z-distribution, not the t-distribution. The margin of error is notably lower (as expected) due to theory relating these two distributions.

If constructing a confidence interval where σ is unknown, then the T.INV or TINV functions can be used. Either function takes two arguments as described below or via Microsoft (T.INV and TINV). Note that the two functions do not work exactly the same.

T.INV(probability,deg_freedom)

The T.INV function syntax has the following arguments:

probability The probability associated with the Student’s t-distribution.

deg_freedom The number of degrees of freedom with which to characterize the distribution.

Example:

Using the Scores output above, construct a 90% two-sided confidence interval.

For a 95% two-sided confidence interval, 1 – α = 0.95 and tα/2, n – 1 = t0.025, 49.

Thus, t = T.INV(0.025, 49) = –2.009575 or, alternatively, t = T.INV(1 – 0.025, 49) = 2.009575.

Using the Scores output above, 68.92 ± (2.009575)×(2.394865) = 68.92 ± 4.812662 = (64.10734, 73.73266). This interval is exactly the same as the one produced by the Descriptive Statistics feature because the exact same margin of error is produced from both methods.

TINV(probability,degrees_freedom)

The TINV function syntax has the following arguments:

The test statistic (t0) follows a t-distribution with n – 1 degrees of freedom. There is no feature in Excel that allows calculating the value of the test statistic automatically. You have to enter the above formula into Excel worksheet to obtain the value of the test statistic for a given sample size (n). First obtain the value of the sample mean and sample standard deviation for the sample (see earlier in the Lab 4 Instructions). The statistic is based on the sample mean, which becomes approximately normal as the sample size gets larger even when the population does not have a normal distribution.

To calculate the p-value of the hypothesis test (to measure the strength of the evidence against the null hypothesis), the TDIST or T.DIST functions can be used. Either function takes three arguments as described below or via Microsoft (TDIST and T.DIST). Note that the two functions do not work the same and TDIST is preferred.

TDIST(x,degrees_freedom,tails)

The TDIST function syntax has the following arguments:

3. Two-Sample Hypothesis Tests in Excel

Consider two normal populations with unknown means µ1 and µ2. The Data Analysis menu in Excel includes the following four hypothesis testing procedures to test H0: µ1 – µ2 = δ0, where δ0 is the hypothesized difference.

t-Test: Paired Two Sample for Means

t-Test: Two-Sample Assuming Equal Variances

t-Test: Two-Sample Assuming Unequal Variances

z-Test: Two Sample for Means

In order to use any of the four testing procedures, first enter data into two columns in a spreadsheet, and then enter their ranges into a dialog box. Note that option (d) requires knowing the population variances, which is not realistic, so this option will not be reviewed.

3.1 Two Independent Sample Hypothesis Tests in Excel

Excel offers a choice between two t-tests for independent samples (options (b) and (c)). One is labeled for equal variances, the other for unequal variances. The unequal variances test is the two-sample t-test in which the population variances are unknown and not assumed equal. The test is valid whether or not the population variances are equal, yet the name remains misleading as it suggests “assuming unequal variances” rather than “not assuming equal variances”.

The other test is a special version of the two-sample t-test that assumes that the two population variances are equal. The test is based on a more accurate (pooled) estimate of the common standard deviation and produces slightly narrower confidence intervals and slightly more powerful tests. As the sample sizes get bigger, the advantages make less and less difference.

The two-sample t-test with a pooled standard deviation is slightly more powerful than the two-sample t-test without equal variances, but serious error can result if the standard deviations are not equal. You can “assume equal variances” and use the t-Test: Two-Sample Assuming Equal Variances option if all of the three following conditions hold. If at least one of the conditions does NOT hold, the non-pooled t-test is more appropriate.

The sample sizes are approximately equal (within 1-2 observations),

Both sample sizes are at least 15,

The ratio of the larger and smaller standard deviations is less than two (smax / smin < 2).

As in the Lab 1 Instructions, suppose the first 25 values of Scores came from Section A and the last 25 values came from Section B. Note that the sample sizes are equal, both are at least 15, and the standard deviation ratio produces a value less than 2 (19.99558/12.77693 ≈ 1.564795). Thus, it would be possible to assume equal variances.

Using the t-Test: Two-Sample Assuming Equal Variances feature within the Data Analysis feature and clicking on OK will present a dialog box exactly the same or similar to the following one. The Variable 1 Range should be the range presented by the cells containing Scores for Section A. The Variable 2 Range should be the range presented by the cells containing Scores for Section B. The ‘up’ arrow to the right of the box can be clicked to permit the mouse to select the data directly from the spreadsheet. The Hypothesized Mean Difference is typically a value of 0. The Labels box should be checked if labels are present. For the Output Options, it is preferred to select Output Range and choose a single cell to present the upper-left corner of all the corresponding output. Then click OK. To adjust the width of a column to fit the longest entry, double-click the column heading border between the column and the next column.


5

For comparison, using the t-Test: Two-Sample Assuming Unequal Variances feature within the Data Analysis feature and clicking on OK will present a dialog box exactly the same or similar to the following one. As seen, it’s essentially the same as the dialog box above.


Both outputs are produced below, yet note that the one on the left is more appropriate. Both outputs provide the sample means, sample variances, and sample sizes of each group. The “pooled procedure” also provides a pooled variance while the two also differ in their values for df due to different calculations. The equal sample sizes (because the standard error and difference between the means would be equal) permit the test statistics to be equal, yet the different df identify different one-tailed p-values as well as two-tailed p-values. Depending on the approach to make a conclusion regarding the hypotheses, the numbers for the current p-values may result in a variety of conclusions. Consult course notes to proceed further.


It is also possible to obtain a confidence interval of the differences by creating a new column of differences from the two existing columns of data. Since a single column of differences can be considered a single sample, return to the One-Sample Confidence Intervals in Excel section above to use either way of finding the confidence interval.

