### Experimental design and background
The purpose of this project is to demonstrate your ability to collect, work with, and clean a data set. 
The goal is to prepare tidy data that can be used for later analysis. 

One of the most exciting areas in all of data science right now is wearable computing. 
Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. 
The data represent data collected from the accelerometers from the Samsung Galaxy S smartphone. 
The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. 
Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. 
Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. 
The experiments have been video-recorded to label the data manually. 
The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 



### Code Book
I have  created a Narrow Tidy data Set, Where Each row represent a value for a variable.

My Tidy Data set had 4 Columns
*1. Subject - Represent the subject/person under test, Value ranging for 1-30.
*2. Activity - Represent the activity performed by the Subject,Value are from one of the valid activity. 
		1 WALKING.
		2 WALKING_UPSTAIRS.
		3 WALKING_DOWNSTAIRS.
		4 SITTING.
		5 STANDING.
		6 LAYING.

*3. Variable - Represent the Descriptive description of type of Measurement, It contains only measurement having Mean or Standard Deviation for a activity.

*4. Mean - Represent mean/ average value of measurements. 
