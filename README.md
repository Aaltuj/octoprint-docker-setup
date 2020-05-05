# Octoprint with mjpg-streamer support | Docker based

1. open terminal
1. clone this repo `git clone https://github.com/Aaltuj/octoprint-docker-setup.git`
2. cd into `cd octoprint-docker-setup`
3. run `docker-compose up -d`
4. after some minutes **octoprint** is running on `http://localhost:5000` and **mjpg-streamer** on `https://localhost:8080/?action=stream`
5. Navigate to `http://localhost:5000` and fill out the welcome wizard
6. When arrived at the webcam part fillout the following values:
- Stream URL: `http://{IP or HOSTNAME}:8080/?action=stream` 
- Snapshot URL: `http://{IP or HOSTNAME}:8080/?action=snapshot`
- Path to FFMPEG: `/opt/ffmpeg/ffmpeg`

> TIP: use `docker inspect {container-name of mjp-stream}` to find the IP adress for the **snapshot url**

you should now have a working Octoprint with webcam support. 
Don't forget to update the usb devices and webcam locations if necessary 
