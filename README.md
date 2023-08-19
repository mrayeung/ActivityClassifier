### Activity Data 

**Author**

#### Executive summary

Over 95% of US population own a smartphone and over 25% of adults now owns a wearable like a smartwatch. These communication devices are equipped with sensors such as accelerometer, gyroscope and magnetic sensor to determine orientiation and movement. Naturally many of these sensor data are used in mobile application such as mobile games and health applications.

Using these sensor data from accelerometer and gyroscope, the device can leverage a classification model to predict the user's activity such as walking, running, laying down, etc.              
These model can be applied to consumer devices such as smartwatch or smartphone, wearable, fitness tracker with the prediction output shared to application used for healthcare and wellness purposes or even personal assistant.

#### Data Sources
The data originated from UCI machine learning repository where an experiment is carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone on the waist. Using its embedded accelerometer and gyroscope, the device captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. 

#### Methodology
1. Data Exploration
	- Data Relationship
	- Data Visualization by Activity and Subjects 
	- Trend and Pattern Discoverary
1. What models should be used by Activity Classifier?
	- Linear Regression
 	- SVM
	- KNN
	- Random Forest
	- LSTN (Keras)


#### Data Exploration
The device has 2 sensors: accelerometer and gyroscope. The raw data generated from the sensor are time-series signals data of 3 axis: X, Y, Z. The data then transformed into frequency domain using fourier transform. We can do so because the time-series signal is periodic. The sensor acceleration signal, which has gravitational and body motion components.

data type        	count
fBodyGyro		79
fBodyAcc		79
fBodyAccJerk		79
tBodyAcc		40
tBodyAccJerk		40
tBodyGyro		40
tBodyGyroJerk		40
tGravityAcc		40
fBodyBodyGyroJerkMag	13
fBodyBodyGyroMag	13
fBodyBodyAccJerkMag	13
fBodyAccMag		13
tBodyGyroJerkMag	13
tBodyGyroMag		13
tBodyAccJerkMag		13
tGravityAccMag		13
tBodyAccMag		13
angle			7
subject			1

Note: the first letter denote the type of data: time-domain as t and frequency-domain as f.

Since the data is capture based on a subject's activity which is the target predication for the model, PCA analysis and TSNE analysis are applied to reduce the dimensionality. The reason for those 2 algorithm, PCA can preserves the variance in the data, whereas t-SNE preserves the relationships between data points in a lower-dimensional space to help visualizing complex data.

When PCA = 2 and PCA = 3, the resulting plot shows a clear cluster of data. 

When TSNE (t-distributed stochastic neighbor embedding) is applied, one can see clear clustering of data grouped by activities. 

There are 3 groups are clustered together in the same area:
1) 'WALKING': 4
2) 'WALKING_DOWNSTAIRS': 5
3) 'WALKING_UPSTAIRS': 6

The other 3 groups are clustered in different part of the graph
1) LAYING':1 , 
2) 'STANDING': 2, 
3) 'SITTING': 3

It is understandable that walking activies for the partcipant would exhitbit similar signal pattern that resemble a period signal with body movement varies when left and right foot are in movement. The main difference between then are the evalation going upstair and downstair. 

As for the other 3 activities, laying, standing and sitting are stationary but using different height reference to center of mass. Therefore one would see clear seperation of data due to such reason. 


Based on the signal the following catagory is created:
1) Time domain data only 
2) Time domain 
3)


#### Next steps
	- Apply both classic (Scikit) and modern modeling (Tensorflow) if possible to find the best model for the Activity Classifier.

