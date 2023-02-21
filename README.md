# OpenCV RTSP:

This repository if a fork of the original opencv <https://github.com/opencv/opencv>
that adds the functionalty of extracting timestamps from rtsp streams.
The patches have been added to the tagged version n3.2.3 of opencv. 
Work needs to be done to incorportate this changes to newer versions.

In order to get timestamps from libavcodec it is also required to 
link opencv agaist a patched version of ffmpeg which can be obtained 
in <https://github.com/alalbiol/FFMpeg_RTSP>



## Installation:

In this repository we want to install opencv into an anaconda environment.
In this guide it is assumed that you have anaconda installed in your system
and its files are located in `~/anaconda3`. If this is not the case you need
to change the paths accordingly.

So first we need to create an anaconda environment. We can do this by using
the provided environment.yml file that will create an environment called `rtsp`:

```bash
conda env create -f environment.yml
```

Then we need to activate the environment:

```bash
conda activate rtsp
```

Once the environment is activated we need to install a patched version of ffmpeg. 
This can be done as follows, in a separate folder:

```bash
git checkout  git@github.com:alalbiol/FFMpeg_RTSP.git 
cd FFMpeg_RTSP 
./configure --prefix=/home/alalbiol/anaconda3/envs/rtsp
make -j 32
make install

```

Finally we can install opencv. This can be done as follows, get into the opencv folder:

```bash
mkdir build
cd build
cmake -D WITH_CUDA=OFF -D BUILD_TIFF=ON -D BUILD_opencv_java=OFF -D WITH_OPENGL=OFF \
-D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=ON -D WITH_EIGEN=ON -D WITH_V4L=ON \
-D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D CMAKE_BUILD_TYPE=RELEASE \
-D BUILD_opencv_python2=OFF -D CMAKE_INSTALL_PREFIX=~/anaconda3/envs/rtsp \
-D PYTHON3_INCLUDE_DIR=$(python3 -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
-D PYTHON3_PACKAGES_PATH=$(python3 -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())") \
-D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=OFF -D OPENCV_ENABLE_NONFREE=ON \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D PYTHON3_EXECUTABLE=$(which python3) -D PYTHON_DEFAULT_EXECUTABLE=$(which python3)  \
-D BUILD_EXAMPLES=OFF ..

```

At this point you can modfiy the cmake command to your needs. For example, if you want to build opencv with cuda support you can do it by adding `-D WITH_CUDA=ON` to the cmake command, or remove other flags if you do not need them.

Now you can compile and install opencv:

```bash
make -j 32
make install 
```



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
