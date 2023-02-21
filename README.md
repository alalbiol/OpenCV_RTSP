# OpenCV RTSP:

This repository if a fork of the original opencv <https://github.com/opencv/opencv>
that adds the functionalty of extracting timestamps from rtsp streams.
The patches have been added to the tagged version n3.2.3 of opencv. 
Work needs to be done to incorportate this changes to newer versions.

In order to get timestamps from libavcodec it is also required to 
link opencv agaist a patched version of ffmpeg which can be obtained 
in <https://github.com/alalbiol/FFMpeg_RTSP>



## OpenCV: Open Source Computer Vision Library

### Resources

* Homepage: <https://opencv.org>
  * Courses: <https://opencv.org/courses>
* Docs: <https://docs.opencv.org/4.x/>
* Q&A forum: <https://forum.opencv.org>
  * previous forum (read only): <http://answers.opencv.org>
* Issue tracking: <https://github.com/opencv/opencv/issues>
* Additional OpenCV functionality: <https://github.com/opencv/opencv_contrib> 


### Contributing

Please read the [contribution guidelines](https://github.com/opencv/opencv/wiki/How_to_contribute) before starting work on a pull request.

#### Summary of the guidelines:

* One pull request per issue;
* Choose the right base branch;
* Include tests and documentation;
* Clean up "oops" commits before submitting;
* Follow the [coding style guide](https://github.com/opencv/opencv/wiki/Coding_Style_Guide).
