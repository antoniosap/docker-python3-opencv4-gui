[![Docker Automated buil](https://img.shields.io/docker/automated/antoniosap/docker-python3-opencv4-gui.svg)]()

Docker image with python 3.7 and opencv 4.0.1 + contrib + GUI interface

Usage:

    docker run -it antoniosap/docker-python3-opencv4-gui ipython
    >>> import cv2

Docker image built with [contrib modules](https://github.com/opencv/opencv_contrib/)

+ ipython
+ jupyter
+ moviePy

for example:

docker run -d \
  -it \
  --net=host \
  --env="DISPLAY" \
  --volume="$HOME/.Xauthority:/root/.Xauthority:rw" \
  --name docker-python3-opencv4-gui \
  --mount type=bind,source=/home/aldebaran/4TBAGO18/docker-mounts,target=/mnt \
  docker-python3-opencv4-gui bash

  
docker attach docker-python3-opencv4-gui


# ipython
Python 3.7.2 (default, Dec 29 2018, 07:16:08) 
Type 'copyright', 'credits' or 'license' for more information
IPython 7.2.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import cv2                                                                                                  

In [2]: video = cv2.VideoCapture("/mnt/kubrick-2001.avi")                                                           

In [3]: while True: 
   ...:     # Read a new frame 
   ...:     ok, frame = video.read() 
   ...:     if not ok: 
   ...:         break 
   ...:  
   ...:     # Display result 
   ...:     cv2.imshow("Tracking", frame) 
   ...:    
   ...:     # Exit if ESC pressed 
   ...:     k = cv2.waitKey(1) & 0xff 
   ...:     if k == 27: 
   ...:         break 
   ...:                 


THIS DOCKED SOLVE TECNICAL PROBLEM:
OpenCV(4.0.1) /opencv-4.0.1/modules/highgui/src/window.cpp:627: 
error: (-2:Unspecified error) The function is not implemented. 
Rebuild the library with Windows, GTK+ 2.x or Cocoa support. 
If you are on Ubuntu or Debian, install libgtk2.0-dev and pkg-config, 
then re-run cmake or configure script in function 'cvShowImage'
