FROM ubuntu:22.04

ARG NODE_VERSION=20
ARG OPENCV_VERSION=4.11.0

# Install Pre-requisites
RUN apt-get update
RUN apt-get install -y curl wget build-essential g++ cmake unzip git
RUN apt-get install -y \
    pkg-config \
    libjpeg-dev \
    libpng-dev \
    libtiff-dev \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    libv4l-dev \
    libxvidcore-dev \
    libx264-dev \
    libgtk-3-dev \
    libatlas-base-dev \
    gfortran \
    python3-dev \
    python3-pip \
    python3-numpy \
    libgstreamer1.0-dev \
    libgstreamer-plugins-base1.0-dev \
    libgstreamer-plugins-good1.0-dev \
    libgstreamer-plugins-bad1.0-dev \
    libgstreamer-plugins-ugly1.0-dev \
    libgstreamer1.0-0 \
    libgstreamer1.0-0-dbg \
    libgstreamer1.0-0-udeb \
    libgstreamer1.0-dev \
    libgstreamer1.0-doc \
    gstreamer1.0-plugins-base \
    gstreamer1.0-plugins-base-apps \
    gstreamer1.0-plugins-base-dbg \
    gstreamer1.0-plugins-base-doc \
    gstreamer1.0-plugins-good \
    gstreamer1.0-plugins-good-dbg \
    gstreamer1.0-plugins-good-doc \
    gstreamer1.0-plugins-bad \
    gstreamer1.0-plugins-bad-dbg \
    gstreamer1.0-plugins-bad-doc \
    gstreamer1.0-plugins-ugly \
    gstreamer1.0-plugins-ugly-dbg \
    gstreamer1.0-plugins-ugly-doc \
    gstreamer1.0-libav \
    gstreamer1.0-doc \
    gstreamer1.0-tools \
    gstreamer1.0-x \
    gstreamer1.0-alsa \
    gstreamer1.0-gl \
    gstreamer1.0-gtk3 \
    gstreamer1.0-qt5 \
    gstreamer1.0-pulseaudio \
    gstreamer1.0-tools \
    gstreamer1.0-x \
    libgstream \
    ffmpeg \
    libeigen3-dev \
    libfreetype6-dev \
    libflatbuffers-dev

# Install Node.js
RUN apt-get update  && \
    curl -sL https://deb.nodesource.com/setup_${NODE_VERSION}.x | bash - && \
    apt-get install -y nodejs

# Download OpenCV
RUN mkdir -p opencv && \
    cd opencv && \
    wget -O opencv.zip https://github.com/opencv/opencv/archive/${OPENCV_VERSION}.zip && \
    unzip opencv.zip

# Download OpenCV Contrib
RUN cd opencv && \
    wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/${OPENCV_VERSION}.zip && \
    unzip opencv_contrib.zip

# Configure OpenCV
RUN cd opencv && \
    mkdir -p build && \
    cd build && \
    cmake \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D WITH_EIGEN=ON \
    -D WITH_FFMPEG=ON \
    -D WITH_FREETYPE=ON \
    -D WITH_GSTREAMER=ON \
    -D WITH_FLATBUFFERS=ON \
    -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib-${OPENCV_VERSION}/modules \
    ../opencv-${OPENCV_VERSION}

# Compile OpenCV
RUN cd opencv/build && \ 
    cmake --build .

# Install OpenCV
RUN cd opencv/build && \
    make install

