FROM ubuntu:14.04

RUN apt-get update -y && \
    apt-get install -y --force-yes curl && \
    apt-get install -y --force-yes xz-utils
#PYTHON 3
# remove several traces of installed python
RUN apt-get -y --force-yes install python3 python3-setuptools python3-pip python3-matplotlib cython3 zlib1g-dev  make libncurses5-dev r-base libxml2-dev
RUN alias python=python3


ENV MAGICK_VERSION 6.9.3-6

RUN apt-get install -y --no-install-recommends \
    libpng-dev libjpeg-dev libtiff-dev libopenjpeg-dev git \
  && apt-get remove -y imagemagick

RUN cd /tmp && curl -SLO "http://imagemagick.org/download/releases/ImageMagick-${MAGICK_VERSION}.tar.xz" \
  && tar xf "./ImageMagick-${MAGICK_VERSION}.tar.xz"


# http://www.imagemagick.org/script/advanced-unix-installation.php#configure
RUN cd "/tmp/ImageMagick-${MAGICK_VERSION}" \
  && ./configure \
    --disable-static \
    --enable-shared \

    --with-jpeg \
    --with-jp2 \
    --with-openjp2 \
    --with-png \
    --with-tiff \
    --with-quantum-depth=8 \

    --without-magick-plus-plus \
    # disable BZLIB support
    --without-bzlib \
    # disable ZLIB support
    --without-zlib \
    # disable Display Postscript support
    --without-dps \
    # disable FFTW support
    --without-fftw \
    # disable FlashPIX support
    --without-fpx \
    # disable DjVu support
    --without-djvu \
    # disable fontconfig support
    --without-fontconfig \
    # disable Freetype support
    --without-freetype \
    # disable JBIG support
    --without-jbig \
    # disable lcms (v1.1X) support
    --without-lcms \
    # disable lcms (v2.X) support
    --without-lcms2 \
    # disable Liquid Rescale support
    --without-lqr \
     # disable LZMA support
    --without-lzma \
    # disable OpenEXR support
    --without-openexr \
    # disable PANGO support
    --without-pango \
    # disable WebP support
    --without-webp \
    # disable XML support
    --without-xml \
  && make \
  && make install \
  && ldconfig /usr/local/lib

RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


RUN pip3 install pika==0.10.0
RUN pip3 install pymongo==3.2.0