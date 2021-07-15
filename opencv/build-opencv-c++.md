### Update Ubuntu system package

```console
sudo apt-get update && sudo apt-get upgrade
```

### Install required tools and packages

```console
sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
```

### Download opencv sources using git

```console
sudo -s
```

```console
cd /opt
```

```console
git clone https://github.com/Itseez/opencv.git

```

```console
git clone https://github.com/Itseez/opencv_contrib.git
```

### Build and install opencv

```console
cd opencv
``` 

```console
mkdir release
```

```console
cd release
```

```console
cmake -D BUILD_TIFF=ON -D WITH_CUDA=OFF -D ENABLE_AVX=OFF -D WITH_OPENGL=OFF -D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=ON -D BUILD_TBB=ON -D WITH_EIGEN=OFF -D WITH_V4L=OFF -D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D OPENCV_GENERATE_PKGCONFIG=ON -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/opt/opencv_contrib/modules /opt/opencv/
```

```console
make -j4
```

```console
make install
```

```console
ldconfig
```

```console
exit
cd ~
```

### Find and set "opencv.pc" file path

```console
ls /usr/local/lib/pkgconfig/
```

```console
sudo cp /usr/local/lib/pkgconfig/opencv4.pc  /usr/lib/x86_64-linux-gnu/pkgconfig/opencv.pc
```

```console
pkg-config --modversion opencv
```

### Build file with opencv

```console
g++ m.cpp -o app `pkg-config --cflags --libs opencv`
```
