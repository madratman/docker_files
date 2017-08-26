FROM osrf/ros:indigo-desktop-full-trusty
MAINTAINER Ratnesh Madaan <ratneshmadaan@gmail.com>

RUN apt-get update && \
  apt-get install -y software-properties-common python-software-properties

## ceres 
RUN apt-get install -y cmake \
  libgoogle-glog-dev \
  libatlas-base-dev \
  libeigen3-dev \
  libsuitesparse-dev
RUN add-apt-repository ppa:bzindovic/suitesparse-bugfix-1319687 && \
  apt-get update && \
  apt-get install -y libsuitesparse-dev

RUN git clone https://ceres-solver.googlesource.com/ceres-solver \
  && cd ceres-solver \
  && mkdir release \
  && cd release \
  && cmake .. \
  && make -j8 \
  && make test \
  && make install

# need opencv >3.2 for stereo SBM api issues # todo checkout some fixed version  
RUN git clone https://github.com/opencv/opencv.git \
  &&  cd opencv \
  &&  mkdir release \
  &&  cd release \
  &&  cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local .. \
  &&  make -j8 \
  &&  make install

RUN apt-get install tmux screen

WORKDIR "/root"




## Refs
# http://ceres-solver.org/installation.html
# https://github.com/subokita/docker-opencv-ceres/blob/master/Dockerfile
