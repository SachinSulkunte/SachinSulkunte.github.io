## Machine Learning Internship at Praxis Engineering
**Project description:** I worked on the creation of the VAST system: Video Analytics with Speech and Text. Over the course of the internship, I worked on several different tasks including a custom OCR (optical character recognition) program using open-source technologies, automated metadata extraction and location mapping, and object recognition tasks.

### 1. Optical Character Recognition
The biggest challenge with this program was that it involved natural scene detection which poses an additional set of challenges due to the lack of clarity. In order to combat this, I manipulated images using OpenCV and augmented the training dataset to better results with text on objects like waving flags and angled signs. I utilized the EAST text detector to isolate regions of interest in video frames. Through OpenCV functions, I manipulated these regions (using thresholding, binarization, and blurring) to better isolate the text from the noisy background. I also analyzed skew angles of text and deskewed them in order to get better results. These manipulated regions of interest were then passed into the open-source Tesseract OCR engine and the text output was fed to our Elasticsearch database.
<img src="../images/ocr.png?raw=true"/>


### 2. Object Detection and Headcounter Program
Utilizing a Yolov3 model for object detection along with a Resnet50 model for the headcounter, the programs were able to be run on extracted frames from the videos of interest. The headcounter program utilized density maps to estimate the number of people in the frame. The resulting data was fed to our Elasticsearch database.
<img src="../images/density.png?raw=true"/>
<img src="../images/yolo.png?raw=true"/>

### 3. Other Processing and Workflow
I also aided in the development of other video processing models such as our sentiment analysis model and our audio analysis model. I made the following visuals to illustrate the overall workflow and tech stack.
<img src="../images/workflow.png?raw=true"/>
<img src="../images/techstack.png?raw=true"/>
