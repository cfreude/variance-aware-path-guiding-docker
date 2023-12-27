FROM ubuntu:18.04 as base

# needs scons scripts update to python3
#FROM ubuntu:20.04 as base

FROM base as stage1

ENV DEBIAN_FRONTEND=noninteractive

### mitsuba dependencies
RUN apt-get update \
    && apt-get install -y \
    build-essential \
    scons \
    qt5-default \ 
    libqt5opengl5-dev \
    libqt5xmlpatterns5-dev \
    libcollada-dom-dev \
    git \
    libpng-dev \
    libjpeg-dev \
    libilmbase-dev \
    libxerces-c-dev \
    libboost-all-dev \    
    libboost-python-dev \
    libopenexr-dev \
    libglewmx-dev \
    libxxf86vm-dev \
    libpcrecpp0v5 \
    libeigen3-dev \
    libfftw3-dev \
    && apt-get clean \
    && apt-get autoclean \
    && apt-get autoremove

FROM stage1

WORKDIR /code
ENV MITSUBA_DIR=/code/mitsuba

ENV PYTHONPATH $MITSUBA_DIR/dist/python:/mitsuba/mitsuba/dist/python/2.7:
ENV PATH $MITSUBA_DIR/wrapper:$MITSUBA_DIR/dist:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV LD_LIBRARY_PATH $MITSUBA_DIR/dist:

CMD tail -F anything