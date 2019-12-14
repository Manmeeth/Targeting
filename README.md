# Targeting
Python and Opencv Code to track the movement.

Delta Frame:
For the delta frame, as it is in a grey frame it has the values 0 to 255 right? 0 - back, 255 - completely white, so here I am recording a frame and looking at the other frame, comparing these and getting the absolute value, which is the delta value and so it shows me only the parts that are moving in the frame. So for the non-different value, it will be pure black and as the differences has some value, it will be seen in a non-black color.

Threshold frame:
For threshold frame, we take the delta frame and anytime there is a value which is over 15, it goes to 255, so it becomes white and if it is 15 or below, it goes to zero and when we move, we are able to  see all those grayscaled pixels on the delta frame based on which we are able to see the blobs - blob more or blob little, using the opencv's threshold function. 
Dilate the thresholded image to fill in holes.

Erode -  this thins the blob to avoid too much wide contours being formed.

Dilation frame:
For the dilation, we have the blobs from the threshold frame and they get blobbed together and the dilation hapens as these are being blobbed together, which is the expansion of these spaces a little. Now there are values associated with it so we can control the level of blobbing - blob it out a lot or blob it out a little less.
find contours on thresholded image.

Contouring frame:
For the Frame 6 which is contouring, we know that a contour is a shape or an outline of an object and I have used the concept here, to the frame which is dilated so that when the blobbing happens, it generates the contours around the moving pixels and so the red colored contours are generated. Now I have used these individual blobs around the moving surface to calculate each centroid within the contour which the green point specifies/indicates, within the rectangle.
So we can set the Contour level to be ignored or concentrated by using the ContourArea function as it can be decided about upto how much level of contours do we want to ignore and after which level do we want to focus on, using the cv2.contourArea() function, I have taken 500 here as I do not want the Contours of less than 500 pixels to be concentrated much.
