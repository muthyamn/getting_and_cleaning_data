This document describes the metadata of files and variables used in program run_analysis.R.

Downloads the given url to the given destiny file. It also creates data dir if it doesn't exist.
extractUciHarFile

Extract a file from the zipped UCI HAR file.
uciHarDataFile

Read dataset files from UCI HAR to given name and prefix. Know names are "train" and "test". Known prefixes are "X", "y" and "subject".

A few examples:

    UCI HAR Dataset/train/X_train.txt
    UCI HAR Dataset/train/y_train.txt
    UCI HAR Dataset/train/subject_train.txt

loadUciHarData

Loads data, labels and subjects from UCI HAR dataset to a data.frame. The returned data.frame contains a column Activity with labels integer codes, a column Subject with subjects integer codes and all other columns from data.
Constants

Some fixed values like dataDir, outputDir and outputFile used in the other parts of the code.
Downloading and loading data

    Downloads the UCI HAR zip file if it doesn't exist
    Reads the activity labels to activityLabels
    Reads the column names of data to features
    Reads the test data.frame to testData
    Reads the trainning data.frame to trainningData

Manipulating data

    Merges test data and trainning data to Data
    Indentifies the mean and std columns (plus Activity and Subject) to meltdata
    Transforms the column Activity into a factor.
    Uses activityLabels to name levels of Activity factor.
    
Final data frame tidy data looks like this:

> head(tidy_data[, 1:5], n=6)
  subject     Activity_Label tBodyAcc-mean()-X tBodyAcc-mean()-Y tBodyAcc-mean()-Z
1       1             LAYING         0.2215982      -0.040513953        -0.1132036
2       1            SITTING         0.2612376      -0.001308288        -0.1045442
3       1           STANDING         0.2789176      -0.016137590        -0.1106018
4       1            WALKING         0.2773308      -0.017383819        -0.1111481
5       1 WALKING_DOWNSTAIRS         0.2891883      -0.009918505        -0.1075662
6       1   WALKING_UPSTAIRS         0.2554617      -0.023953149        -0.0973020

Writing final data to txt file


