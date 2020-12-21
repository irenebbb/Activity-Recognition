# Activity-Recognition
Activity Recognition through Phone Sensor Data and Machine Learning

This is a project based on data collected using my Xiaomi Mi 9, through Phyphox. The phone was housed in a armband case, tied to my right arm.

### Data Loading and Preprocessing
Data (organized in separate folders), was loaded and prepocessed through a loop, which opened CSV files per folder, saved the data (Accelerometer x,y,z, time and gyroscope x,y,z) to a list. The first 10 seconds of each recordings are omitted, due to the artifacts created by the activation of the recording app. For the same reason, the last 10 seconds of each recording are also omitted.

Five classes of data were collected:
- Walking: data was collected in 14 10-minute sessions
- Squat data was recorder in 6 sessions, with 5-10 squats/session
- Meditation was used as additional activity, recorded in 5 separate 10-20 mins sessions
- Climbing stairs, up and down. Data was recorded in short 2 min intervals, alternating between climbing up and down.

Data structure: HW4_Data/NameOfClass/Class1/Accelerometer.csv

Data was pre-processed, using two scalers (MinMaxScaler and Standard Scaler) for testing accuracy on a pre-set model (Logistic Regression).

Optimal parameters for model tested were found through GridsearchCV.


### Results
Logistic Regression Cross-Validation Accuracy : 99.63%
Linear SVC Cross-Validation Accuracy          : 99.82% 
MLP Cross-Validation Accuracy                 : 97.97%

![Class inbalance graph](https://github.com/irenebbb/Activity-Recognition/blob/main/HW4_Data/photo5981064361856317106.jpg?raw=true)
Walking and Meditating had a much higher numbe of elements than the other 3 classes, contributing to class imbalance

### Conclusions
In all 3 models tested, accuracy was above 95% for all trials. For one model (Random Forest, not shown), accuracy ws sligtly lower (~94% on all trials). High accuracy could be due to class imbalance, as well as the choice of additional activity (meditation). To balance classes, more data points should be collected on squats, as 50 squats only made up ~15/20 minutes of results, while walking was registered for two hours. For better accuracy, the data was split in testing, training and validation sets, with a 20:60:20 split. This ensured that the data used for 10-fold cross-validation had not been yet used.
