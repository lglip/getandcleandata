Variables of 'data' and 'data2' from the run\_analysis.R script
---------------------------------------------------------------

The following data frame provides an overview of the variables in data
table `data` and `data2`. The former was first merged and tidied,
containing the train and test data of the **Human Activity Recognition
Using Smartphones Dataset**. The latter was constructed by using `data`
as input.

    ##                            Data Variables
    ## 1                                 Subject
    ## 2                                Activity
    ## 3                      timeBodyAcc.mean.X
    ## 4                      timeBodyAcc.mean.Y
    ## 5                      timeBodyAcc.mean.Z
    ## 6                   timeGravityAcc.mean.X
    ## 7                   timeGravityAcc.mean.Y
    ## 8                   timeGravityAcc.mean.Z
    ## 9                  timeBodyAccJerk.mean.X
    ## 10                 timeBodyAccJerk.mean.Y
    ## 11                 timeBodyAccJerk.mean.Z
    ## 12                    timeBodyGyro.mean.X
    ## 13                    timeBodyGyro.mean.Y
    ## 14                    timeBodyGyro.mean.Z
    ## 15                timeBodyGyroJerk.mean.X
    ## 16                timeBodyGyroJerk.mean.Y
    ## 17                timeBodyGyroJerk.mean.Z
    ## 18                    timeBodyAccMag.mean
    ## 19                 timeGravityAccMag.mean
    ## 20                timeBodyAccJerkMag.mean
    ## 21                   timeBodyGyroMag.mean
    ## 22               timeBodyGyroJerkMag.mean
    ## 23                     freqBodyAcc.mean.X
    ## 24                     freqBodyAcc.mean.Y
    ## 25                     freqBodyAcc.mean.Z
    ## 26                 freqBodyAcc.meanFreq.X
    ## 27                 freqBodyAcc.meanFreq.Y
    ## 28                 freqBodyAcc.meanFreq.Z
    ## 29                 freqBodyAccJerk.mean.X
    ## 30                 freqBodyAccJerk.mean.Y
    ## 31                 freqBodyAccJerk.mean.Z
    ## 32             freqBodyAccJerk.meanFreq.X
    ## 33             freqBodyAccJerk.meanFreq.Y
    ## 34             freqBodyAccJerk.meanFreq.Z
    ## 35                    freqBodyGyro.mean.X
    ## 36                    freqBodyGyro.mean.Y
    ## 37                    freqBodyGyro.mean.Z
    ## 38                freqBodyGyro.meanFreq.X
    ## 39                freqBodyGyro.meanFreq.Y
    ## 40                freqBodyGyro.meanFreq.Z
    ## 41                    freqBodyAccMag.mean
    ## 42                freqBodyAccMag.meanFreq
    ## 43            freqBodyBodyAccJerkMag.mean
    ## 44        freqBodyBodyAccJerkMag.meanFreq
    ## 45               freqBodyBodyGyroMag.mean
    ## 46           freqBodyBodyGyroMag.meanFreq
    ## 47           freqBodyBodyGyroJerkMag.mean
    ## 48       freqBodyBodyGyroJerkMag.meanFreq
    ## 49          angle.timeBodyAccMean.gravity
    ## 50  angle.timeBodyAccJerkMean.gravityMean
    ## 51     angle.timeBodyGyroMean.gravityMean
    ## 52 angle.timeBodyGyroJerkMean.gravityMean
    ## 53                    angle.X.gravityMean
    ## 54                    angle.Y.gravityMean
    ## 55                    angle.Z.gravityMean
    ## 56                      timeBodyAcc.std.X
    ## 57                      timeBodyAcc.std.Y
    ## 58                      timeBodyAcc.std.Z
    ## 59                   timeGravityAcc.std.X
    ## 60                   timeGravityAcc.std.Y
    ## 61                   timeGravityAcc.std.Z
    ## 62                  timeBodyAccJerk.std.X
    ## 63                  timeBodyAccJerk.std.Y
    ## 64                  timeBodyAccJerk.std.Z
    ## 65                     timeBodyGyro.std.X
    ## 66                     timeBodyGyro.std.Y
    ## 67                     timeBodyGyro.std.Z
    ## 68                 timeBodyGyroJerk.std.X
    ## 69                 timeBodyGyroJerk.std.Y
    ## 70                 timeBodyGyroJerk.std.Z
    ## 71                     timeBodyAccMag.std
    ## 72                  timeGravityAccMag.std
    ## 73                 timeBodyAccJerkMag.std
    ## 74                    timeBodyGyroMag.std
    ## 75                timeBodyGyroJerkMag.std
    ## 76                      freqBodyAcc.std.X
    ## 77                      freqBodyAcc.std.Y
    ## 78                      freqBodyAcc.std.Z
    ## 79                  freqBodyAccJerk.std.X
    ## 80                  freqBodyAccJerk.std.Y
    ## 81                  freqBodyAccJerk.std.Z
    ## 82                     freqBodyGyro.std.X
    ## 83                     freqBodyGyro.std.Y
    ## 84                     freqBodyGyro.std.Z
    ## 85                     freqBodyAccMag.std
    ## 86             freqBodyBodyAccJerkMag.std
    ## 87                freqBodyBodyGyroMag.std
    ## 88            freqBodyBodyGyroJerkMag.std

The first two variables in the data table are *Subject* and *Activity*,
representing the subject number (integer between 1 and 30) and the
activity (Walking, Walking Upstairs, Walking Downstairs, Sitting,
Standing, Laying), respectively. The other 86 variables were selected by
evaluating the name of each variable in the merged dataset and retaining
only those variables containing the string *"mean()"* or *"std()"* via
the `dplyr::select` function.

Transformations of 'data' from the run\_analysis.R script
---------------------------------------------------------

After having assigned the appropriate column names to the variables of
the dataset, the values (integer) of *Activity* were replaced by their
respective activity label. The data frame below represents the *matching
table* used in the process. The matching itself was performed through a
*for* loop and by using the `replace` function.

    ##    ID           Activity
    ## 1:  1            WALKING
    ## 2:  2   WALKING_UPSTAIRS
    ## 3:  3 WALKING_DOWNSTAIRS
    ## 4:  4            SITTING
    ## 5:  5           STANDING
    ## 6:  6             LAYING

Eventually, the variable names were tidied using the `gsub` function,
replacing any unwanted symbols like **"-"**, **","**, **"("** and
**")"**. Where appropriate, the **t**s and **f**s were replaced by
*time* and *freq*, respectively.

Transformations of 'data2' from the run\_analysis.R script
----------------------------------------------------------

The second, independent tidy data set was named `data2` and contains the
average of each variable for each activity and each subject. Before
summarising by `mean()` using the `dplyr::summarise_all` function, the
data were grouped by *Subject* and *Activity* through the
`dplyr::group_by` function. A data table containing the first five rows
(with truncated columns) of `data2` is shown below.

    ## # A tibble: 5 x 88
    ## # Groups:   Subject [1]
    ##   Subject Activity timeBodyAcc.mea~ timeBodyAcc.mea~ timeBodyAcc.mea~
    ##     <int> <chr>               <dbl>            <dbl>            <dbl>
    ## 1       1 LAYING              0.222         -0.0405            -0.113
    ## 2       1 SITTING             0.261         -0.00131           -0.105
    ## 3       1 STANDING            0.279         -0.0161            -0.111
    ## 4       1 WALKING             0.277         -0.0174            -0.111
    ## 5       1 WALKING~            0.289         -0.00992           -0.108
    ## # ... with 83 more variables: timeGravityAcc.mean.X <dbl>,
    ## #   timeGravityAcc.mean.Y <dbl>, timeGravityAcc.mean.Z <dbl>,
    ## #   timeBodyAccJerk.mean.X <dbl>, timeBodyAccJerk.mean.Y <dbl>,
    ## #   timeBodyAccJerk.mean.Z <dbl>, timeBodyGyro.mean.X <dbl>,
    ## #   timeBodyGyro.mean.Y <dbl>, timeBodyGyro.mean.Z <dbl>,
    ## #   timeBodyGyroJerk.mean.X <dbl>, timeBodyGyroJerk.mean.Y <dbl>,
    ## #   timeBodyGyroJerk.mean.Z <dbl>, timeBodyAccMag.mean <dbl>,
    ## #   timeGravityAccMag.mean <dbl>, timeBodyAccJerkMag.mean <dbl>,
    ## #   timeBodyGyroMag.mean <dbl>, timeBodyGyroJerkMag.mean <dbl>,
    ## #   freqBodyAcc.mean.X <dbl>, freqBodyAcc.mean.Y <dbl>,
    ## #   freqBodyAcc.mean.Z <dbl>, freqBodyAcc.meanFreq.X <dbl>,
    ## #   freqBodyAcc.meanFreq.Y <dbl>, freqBodyAcc.meanFreq.Z <dbl>,
    ## #   freqBodyAccJerk.mean.X <dbl>, freqBodyAccJerk.mean.Y <dbl>,
    ## #   freqBodyAccJerk.mean.Z <dbl>, freqBodyAccJerk.meanFreq.X <dbl>,
    ## #   freqBodyAccJerk.meanFreq.Y <dbl>, freqBodyAccJerk.meanFreq.Z <dbl>,
    ## #   freqBodyGyro.mean.X <dbl>, freqBodyGyro.mean.Y <dbl>,
    ## #   freqBodyGyro.mean.Z <dbl>, freqBodyGyro.meanFreq.X <dbl>,
    ## #   freqBodyGyro.meanFreq.Y <dbl>, freqBodyGyro.meanFreq.Z <dbl>,
    ## #   freqBodyAccMag.mean <dbl>, freqBodyAccMag.meanFreq <dbl>,
    ## #   freqBodyBodyAccJerkMag.mean <dbl>,
    ## #   freqBodyBodyAccJerkMag.meanFreq <dbl>, freqBodyBodyGyroMag.mean <dbl>,
    ## #   freqBodyBodyGyroMag.meanFreq <dbl>,
    ## #   freqBodyBodyGyroJerkMag.mean <dbl>,
    ## #   freqBodyBodyGyroJerkMag.meanFreq <dbl>,
    ## #   angle.timeBodyAccMean.gravity <dbl>,
    ## #   angle.timeBodyAccJerkMean.gravityMean <dbl>,
    ## #   angle.timeBodyGyroMean.gravityMean <dbl>,
    ## #   angle.timeBodyGyroJerkMean.gravityMean <dbl>,
    ## #   angle.X.gravityMean <dbl>, angle.Y.gravityMean <dbl>,
    ## #   angle.Z.gravityMean <dbl>, timeBodyAcc.std.X <dbl>,
    ## #   timeBodyAcc.std.Y <dbl>, timeBodyAcc.std.Z <dbl>,
    ## #   timeGravityAcc.std.X <dbl>, timeGravityAcc.std.Y <dbl>,
    ## #   timeGravityAcc.std.Z <dbl>, timeBodyAccJerk.std.X <dbl>,
    ## #   timeBodyAccJerk.std.Y <dbl>, timeBodyAccJerk.std.Z <dbl>,
    ## #   timeBodyGyro.std.X <dbl>, timeBodyGyro.std.Y <dbl>,
    ## #   timeBodyGyro.std.Z <dbl>, timeBodyGyroJerk.std.X <dbl>,
    ## #   timeBodyGyroJerk.std.Y <dbl>, timeBodyGyroJerk.std.Z <dbl>,
    ## #   timeBodyAccMag.std <dbl>, timeGravityAccMag.std <dbl>,
    ## #   timeBodyAccJerkMag.std <dbl>, timeBodyGyroMag.std <dbl>,
    ## #   timeBodyGyroJerkMag.std <dbl>, freqBodyAcc.std.X <dbl>,
    ## #   freqBodyAcc.std.Y <dbl>, freqBodyAcc.std.Z <dbl>,
    ## #   freqBodyAccJerk.std.X <dbl>, freqBodyAccJerk.std.Y <dbl>,
    ## #   freqBodyAccJerk.std.Z <dbl>, freqBodyGyro.std.X <dbl>,
    ## #   freqBodyGyro.std.Y <dbl>, freqBodyGyro.std.Z <dbl>,
    ## #   freqBodyAccMag.std <dbl>, freqBodyBodyAccJerkMag.std <dbl>,
    ## #   freqBodyBodyGyroMag.std <dbl>, freqBodyBodyGyroJerkMag.std <dbl>
