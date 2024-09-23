# HAR system with_smartphone data
## About the Dataset
The Human Activity Recognition database was built from the recordings of 30 study participants performing activities of daily living (ADL) while carrying a waist-mounted smartphone with embedded inertial sensors. The objective is to classify activities into one of the six activities performed.

### Description of experiment
The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

### Attribute information
For each record in the dataset the following is provided:

  - Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.

  - Triaxial Angular velocity from the gyroscope.

  - A 561-feature vector with time and frequency domain variables.

  - Its activity label.

  - An identifier of the subject who carried out the experiment.

### Relevant papers
Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra, Jorge L. Reyes-Ortiz. Energy Efficient Smartphone-Based Activity Recognition using Fixed-Point Arithmetic. Journal of Universal Computer Science. Special Issue in Ambient Assisted Living: Home Care. Volume 19, Issue 9. May 2013

Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. 4th International Workshop of Ambient Assited Living, IWAAL 2012, Vitoria-Gasteiz, Spain, December 3-5, 2012. Proceedings. Lecture Notes in Computer Science 2012, pp 216-223.

Jorge Luis Reyes-Ortiz, Alessandro Ghio, Xavier Parra-Llanas, Davide Anguita, Joan Cabestany, Andreu Català. Human Activity and Motion Disorder Recognition: Towards Smarter Interactive Cognitive Environments. 21st European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, ESANN 2013. Bruges, Belgium 24-26 April 2013.

## Models Used
## ROCKET and Arsenal
The ROCKET (Random Convolutional Kernel Transform) and Arsenal models were implemented using the sktime library. ROCKET is a state-of-the-art method for time series classification that utilizes random convolutional kernels to generate a vast set of features from the input data. These features are subsequently used by a linear classifier, allowing for efficient and scalable classification with excellent accuracy. ROCKET's ability to transform raw sensor signals into meaningful features made it an ideal candidate for handling the complex time series data generated from the smartphone sensors.

Arsenal builds upon the ROCKET framework by leveraging an ensemble of multiple ROCKET models. Each model in the Arsenal ensemble is trained with different random convolution kernels, leading to more robust and generalized predictions. This approach enhances classification performance by capturing a wider variety of patterns in the time series data. Arsenal was particularly effective in handling the variability between different participants and activities, ensuring higher accuracy in predicting human activity across the dataset.

Both models were applied to the 561-feature vector derived from the accelerometer and gyroscope signals, using 70% of the data for training and 30% for testing. ROCKET and Arsenal were selected for their computational efficiency, making them well-suited for real-time applications on mobile devices.

## Spiking Neural Networks (SNN)
In addition to ROCKET and Arsenal, Spiking Neural Networks (SNNs) were developed using PyTorch and snntorch. SNNs are biologically inspired models designed to handle temporal data by processing information through discrete spikes, mimicking the behavior of neurons in the brain. This spike-based approach enables energy-efficient computation, making SNNs an attractive option for applications with power constraints, such as wearable devices or smartphones.

The SNN models were trained on the pre-processed sensor data (accelerometer and gyroscope signals) to classify the six human activity types. The network architecture involved spike encoding techniques that converted the continuous sensor signals into spike trains, followed by layers designed to capture the temporal relationships in the data. The event-driven nature of SNNs allowed for efficient processing of the time series data, further reducing computational overhead.

### Relevant papers
Dempster, Angus, François Petitjean, and Geoffrey I. Webb. “Rocket: exceptionally fast and accurate time series classification using random convolutional kernels.” Data Mining and Knowledge Discovery 34.5 (2020)

Middlehurst, Matthew, James Large, Michael Flynn, Jason Lines, Aaron Bostrom, and Anthony Bagnall. “HIVE-COTE 2.0: a new meta ensemble for time series classification.” arXiv preprint arXiv:2104.07551 (2021).

Fang, Haowen, Amar Shrestha, and Qinru Qiu. “Multivariate Time Series Classification Using Spiking Neural Networks.” arXiv preprint arXiv:2007.03547 (2020).
