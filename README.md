# Fibbee_streaming
Use Jsmpeg for rtsp streaming over NAT


1) Port forwarding

     `ssh -L 8888:192.168.1.22:554 -p port user@host.com`

2) Install ffmpeg https://ffmpeg.org/


3) Clone repo into your project folder
`git clone https://github.com/phoboslab/jsmpeg.git`

4) Inside jsmpeg folder:
`node websocket-relay fibbee 9100 9000`

5) Run ffmpeg decoding session:
`ffmpeg -rtsp_transport tcp -i rtsp://admin:pipipi@localhost:8888/h264Preview_01_sub -f mpegts -codec:v mpeg1video -framerate 25 -s 640x480 -b:v 1500k -bf 0 http://localhost:9100/fibbee`

6) Now you can use stream in your html page!
`<script type="text/javascript" src="jsmpeg/jsmpeg.min.js"></script>`
 `<div class="jsmpeg" data-url="ws://localhost:9000/" data-loop="true" data-autoplay="true"></div>`

