Getting-and-Cleaning-Data-Course-Project
========================================
Getting and Cleaning Data Course 

### Script 

## Step 1: Setting the Current working directory to Data Folder.
    setwd("UCI HAR Dataset")-- 
## Step 2: Reading Descriptive Variable names from features.txt and Activity Names from activity_labels
            columns <- read.table("./features.txt")
             x_col<-columns[,2]
            activity <- read.table("./activity_labels.txt")
    
## Step 3:  Merges the training and the test sets to create one data set and Appropriately labels the data set with                      descriptive variable names   
    
    # Merging Subject Data- reading test and train data in respective Data frames and Joining two data frames using 
      Rbind() function of R
    train_subject <- read.table("./train/subject_train.txt",col.names = c("subject"))
    test_subject <- read.table("./test/subject_test.txt",col.names = c("subject"))
    all_data_subject <- data.frame(rbind(train_subject,test_subject))
    
    # Merging mesearument Data - reading test and train data in respective Data frames and Joining two data frames using 
      Rbind() function of R
    train_X <- read.table("./train/X_train.txt",col.names = x_col)
    test_X <- read.table("./test/X_test.txt",col.names = x_col)
    all_data_X <- data.frame(rbind(train_X,test_X))
    
    # Merging Activity Y data- reading test and train data in respective Data frames and Joining two data frames using 
      Rbind() function of R
    train_activity <- read.table("./train/y_train.txt",col.names = c("Activity"))
    test_activity <- read.table("./test/y_test.txt",col.names = c("Activity"))
    all_data_activity <- data.frame(rbind(train_activity,test_activity))

    # Combining Activiy and X Data and Subject Datausing Cbind() function or R
    all_data_X_activity <- data.frame(cbind(all_data_subject,all_data_activity,all_data_X)) 

    
## Step 4: Extracts only the measurements on the mean and standard deviation for each measurement. using grepl function to get the varibale name which contain either mean or std in their name
    
    alldata_mean_std <- all_data_X_activity[, grepl("mean|std", names(all_data_X_activity))]
   
    
## Step 5: Using descriptive activity names to name the activities in the data set
    all_data_X_activity$Activity <- factor(all_data_X_activity$Activity, labels = activity[,2])
   
## Step 6: From the data set in step 4, creates a second, independent tidy data set with the average of each variable for               each activity and each subject.
*Created a Melted Data Set using Subject and Activity as Id variable and Converting all the 561 measurement variables         into narrow tidy Data set. 
    alldatamelt <- melt(all_data_X_activity,id=c("subject","Activity"),measure.vars= names(train_X))
*Using Meted Data Set created above, I applied ddply() funciton of R and calculated mean for all the variables for all        the activity for every subject. 
    finaltidyset <- ddply(alldatamelt,.(subject,Activity,variable),summarise,mean=mean(value))
*Write back the Tidy set to file
    write.table (finaltidyset, file="FinalTidySet.csv", row.name=FALSE)

    
    setwd(cwd)
    
}  
