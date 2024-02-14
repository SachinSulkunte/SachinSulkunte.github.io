# Gesture Controller for Desktop
The main purpose of this project is to enable users who might have trouble using a mouse to navigate their computers with ease. Using hand tracking modules from MediaPipe as well as gesture recognition models I trained, users are able to use a variety of recognized gestures to open up specific applications, adjust computer volume, or switch between tabs easily.

## Volume Control
Using a model to detect the location of the thumb and index finger, OpenCV is used to determine the position of the fingertips relative to the camera field-of-view. These 2D coordinate positions are used to compute the Euclidean distance between the thumb and index finger. This distance is scaled to enable different range of motions between users. Touching the two fingers together mutes the device while expanding them will gradually increase the volume.

Video:

<video src="https://user-images.githubusercontent.com/41236722/199888183-8954bf67-b065-46c4-a691-f04bdc520e4e.mp4" data-canonical-src="https://user-images.githubusercontent.com/41236722/199888183-8954bf67-b065-46c4-a691-f04bdc520e4e.mp4" controls="controls" muted="muted" class="d-block rounded-bottom-2 width-fit" style="max-height:300px;"></video>

## General Control
With the use of a convolutional neural network, certain gestures have been trained into a simple classification model. The code to manipulate what these gestures control is easily accessible for quick modification. Eventually, a GUI could be created that would allow users custom-configurations by altering what gestures control which actions. Current actions include opening the file explorer, browser, and the application menu. Here a quick demo of moving the mouse with a finger is shown with a gesture to function as a 'click'.


<video src="https://github.com/SachinSulkunte/SachinSulkunte.github.io/assets/41236722/681f92ff-507b-43f4-be13-029429aba824" data-canonical-src="https://github.com/SachinSulkunte/SachinSulkunte.github.io/assets/41236722/681f92ff-507b-43f4-be13-029429aba824" controls="controls" muted="muted" class="d-block rounded-bottom-2 width-fit" style="max-height:300px;"></video>
