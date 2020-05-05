# DOCKER-VERSION 0.3.4
FROM    ubuntu

MAINTAINER Charles Nguyen <chuckleb@gmail.com>

# Based off of instructions by Miguel Grinberg 
# http://blog.miguelgrinberg.com/post/how-to-build-and-run-mjpg-streamer-on-the-raspberry-pi

# Turn off intaractive mode to reduce noise and errors
ENV	DEBIAN_FRONTEND noninteractive

# Update path
ENV	PATH	/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV LD_LIBRARY_PATH	/usr/local/lib

# Run updates and install base libs & tools
RUN	apt-get -y update
RUN	apt-get -y install cmake build-essential \
	libjpeg8-dev imagemagick libv4l-dev git

# MJPG-Streamer looks for videodev.h instead of videodev2.h
RUN ln -s /usr/include/linux/videodev2.h /usr/include/linux/videodev.h

RUN git clone https://github.com/jacksonliam/mjpg-streamer.git && \
	cd mjpg-streamer/mjpg-streamer-experimental && \
	make && \
	make install && \
	cd / ; rm -rf mjpg*

VOLUME ["/data"]
EXPOSE 8080

RUN echo 'ls -la /dev/video0 && mjpg_streamer -o "output_http.so -w ./www -p 8080" -i "input_uvc.so mjpg_streamer -r VGA -f 10"' > /start.sh && chmod a+rx /start.sh

ENTRYPOINT /start.sh
