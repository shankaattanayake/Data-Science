# Face Tracking and Face Filtering 

## Objective
In this Project, I had to use the Laptop Camera to track and place a picture of a Cartoon Mask on my face in real time while considering the movements of my face, and the increase and decrease of the size of my face as I get closer and move away from the camera. 

## Procedure:
Initially, each frame that was captured by the camera was stored and converted into a Grayscale image.

Next, the Grayscale image was blurred and sent to a contour finder to find information about the face, such as Height, Width, and Location of the face.

Finally, the information of the face is used to insert objects into the camera feed such that the interested areas of the camera feed are given more focus. 

For the specific code used for this project, it can be seen in the Jupyter Notebook file in this folder. (Task6_Cartoon Filter_Solution.ipynb)

| ![ezgif com-gif-maker (4)](https://github.com/shankaattanayake/Data-Science/blob/main/Computer%20Vision/Images/reduze%20finale%20face.gif) |


Finally, to add the cartoon face mask filter on top of the face, the face information obtained in the above steps were used to size and move the cartoon face mask image to the correct location of the camera feed.

| ![ezgif com-gif-maker (4)](https://github.com/shankaattanayake/Data-Science/blob/main/Computer%20Vision/Images/reduze%20finale.gif) |
