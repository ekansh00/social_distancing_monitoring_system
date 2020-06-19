# social_distancing_monitoring_system
In the fight against the corona virus, social distancing has proven to be an effective measure to slow down the spread of the disease. I have made a model that will help to monitor social distancing with the help of surveillance devices. 

The main objective is to detect the real-time distance between any two pedestrians present in a video or image taken from overhead surveillance devices. 
The major steps to be worked upon were Pedestrian Detection in the given image (frame of video) and Distance Calculation between the objects detected.

The workflow of the model is it receives a video input from the surveillance system and converts this video input into image sequences for further analysis.
The trained yolo v4 model runs detections on this image sequence and outputs the bounding boxes coordinates which are then fed to a function which calculates the distances between all the detections and mark the people not following social distancing norm. 
Once I know the people who are breaking the specified social distance threshold, I marked them through a red bounding box.
 
Pedestrian Detection
In surveillance system we have to select models with low computational power and high fps. We selected the following models:

•	Single Shot Detector (SSD) Inception
•	Single Shot Detector (SSD) Mobile Net
•	You Only Look Once (YOLO) v4
•	Tiny YOLO 
•	Faster RCNN
•	RFCN 

For Pedestrian detection our model is trained on Coco dataset and we have used Oxford Town Centre dataset for testing.
After getting our detections on these models we filtered out the detection for only the class “person”.  

Distance calculation

The model converts the given image sequence which is in perspective view to bird's eye view by creating a transformation matrix. 
The bottom centre coordinates of the bounding boxes are passed through the transformation matrix obtained from the above functions to get their respective mapped coordinates in bird’s eye view and the distances are calculated between these mapped coordinates through Euclidian distance formula. 
 
After getting the distances I obtain the ratio of the image by dividing any actual length with its length in converted image (bird’s eye view) and with the help of this ratio converted different distances and plotted a graph with these values. 

So far no ideal tool for monitoring social distancing has been implemented and this project is a small step which was made to reach this goal. With advanced pedestrian detection models and using advance algorithm for distance estimation I am able to make an accurate social distance monitoring system that can be deployed on surveillance systems like UAVs and CCTVs.

