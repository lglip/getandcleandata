### run\_analysis.R

**run\_analysis.R** is retrievable from the following URL:
<https://github.com/lglip/getandcleandata/blob/master/run_analysis.R>.

This script executes the following steps:

1.  It loads and neatly stores the training and test datasets from the
    **Human Activity Recognition Using Smartphones Dataset**, as well as
    the list of unique features and the activity labels.
2.  It merges the training and the test datasets to create one data set
    called `data`.
3.  It extracts the columns regarding the mean and standard deviation
    for each entry based on the text strings *"mean()"* and *"std()"*.
4.  It uses descriptive activity names to label the activities in the
    merged data set.
5.  It labels the data set with descriptive variable names, replacing
    any redudant symbols and describing the variables more clearly.
6.  It creates a second, independent tidy dataset called `data2` with
    the average of each variable for each activity and each subject.

### CodeBook.Rmd

**CodeBook.Rmd** is retrievable from the following URL:
<https://github.com/lglip/getandcleandata/blob/master/CodeBook.md>

The codebook includes more details on the variables, the data, and most
of the transformations that has been performed during the clean-up.
