# Driver-Drowsiness-Detection
PROPOSED SYSTEM

Drowsiness detection can be divided into three main categories 
(1) Vehicle based 
(2) Behavioural based 
(3)Physiological based 
Drowsiness detection is based on these three parameters. A detailed review on these measures will provide insight on the present systems,issues associated with them and the enhancements that need to be done to make a robust system.Vehicle based measures: A number of metrics, including deviations from lane position, movement of the steering wheel, pressure on the acceleration pedal, etc., are Vandna Saini et al, / (IJCSIT) International Journal of Computer Science and Information Technologies, constantly monitored and any change in these that crossesa specified threshold indicates a significantly increased probability that the driver is drowsy.

Behavioural based measures: The behaviour of the driver,including yawning, eye closure, eye blinking, head pose etc.is monitored through a camera and the driver is alerted if any of these drowsiness symptoms are detected.Physiological based measures: The correlation between physiological signals ECG (Electrocardiogram) and EOG (Electrooculogram). Drowsiness is detected through pulse rate, heartbeat and brain information.

DROWSINESS DETECTION TECHNIQUES
If car technologies are going to prevent or at least warn of driver fatigue, what symptoms does the driver give off that can be detected? According to research, there are multiple categories of technologies that can detect driver fatigue. The first is the use of cameras to monitor a person’s behaviour. This includes monitoring their pupils, mouth for yawning, head position, and a variety of other factors. The next of these technologies is voice recognition. Often a person’s voice can give off clues on how fatigued they are.
The detail explanation of the underlying techniques of drowsiness detection that are mostly used for the detection purpose:
• ECG and EEG
• LBP (Local Binary Pattern)
• Steering Wheel Movement (SWM)
• Optical Detection

Model Used : ER SVM
Ensemble methods  combine several decision trees to produce better predictive performance than utilizing a single decision tree. The main principle behind the ensemble model is that a group of weak learners come together to form a strong learner.
Binary SVM Decision Tree is a tree based architecture that utilizes support vector machines for solving multiclass problems. It takes advantage of both the efficient computation of the decision tree architecture and the high classification accuracy of SVMs. 

1. Detecting Eye blinks with Facial Landmarks

Eye blinks can be detected by referencing significant facial landmarks. Many software libraries can plot significant facial features within a given region of interest. Python’s dlib library uses Kazemi and Sullivan’s One Millisecond Face Alignment  with an Ensemble of Regression Trees to implement this feature.

The program uses a facial training set to understand where certain points exist on facial structures. The program then plots the same points on region of interests in other images, if they exists. The program uses priors to estimate the probable distance between keypoints .
detect = dlib.get_frontal_face_detector()
predict = dlib.shape_predictor("E:\Github projects\Drowsiness_Detection_fork\shape_predictor_68_face_landmarks.dat")# Dat file is the crux of the code.

The library outputs a 68 point plot on a given input image.

For eye blinks we need to pay attention to points 37-46, the points that describe the eyes.

In Real Time Eye Blinking Using Facial Landmarks, Soukupová and Čech derive an equation that represents the Eye Aspect Ratio. The Eye Aspect Ratio is an estimate of the eye opening state.
The eye aspect ratio can be defined by the below equation.

2. Condition
It checks 20 consecutive frames and if the Eye Aspect ratio is less than 0.25, Alert is generated.
A program can determine if a person’s eyes are closed if the Eye Aspect Ratio falls below a certain threshold.

def eye_aspect_ratio(eye):
A = distance.euclidean(eye[1], eye[5])
B = distance.euclidean(eye[2], eye[4])
C = distance.euclidean(eye[0], eye[3])
ear = (A + B) / (2.0 * C)
return ear
thresh = 0.25
frame_check = 20
