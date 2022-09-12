# Fibbee Streaming
Use JSMpeg for RTSP streaming over NAT

![Fibbee](https://user-images.githubusercontent.com/43553016/188693618-7805b4e4-e52c-44bc-a2b9-b0467f5a7d4b.png)

We need 3 separate terminals: port forwarding, ffmpeg decoding session, websocket-relay

1) Port forwarding

`ssh -L 8888:192.168.1.22:554 -p port user@host.com`

2) Install ffmpeg https://ffmpeg.org/


3) Clone jsmpeg repo into your project folder

`git clone https://github.com/phoboslab/jsmpeg.git`

4) In new terminal inside jsmpeg folder:
 
`node websocket-relay.js fibbee 9100 9000`

5) In new terminal run ffmpeg decoding session:

`ffmpeg -rtsp_transport tcp -i rtsp://admin:pipipi@localhost:8888/h264Preview_01_sub
-f mpegts -codec:v mpeg1video -framerate 25
-s 640x480 -b:v 1500k -bf 0 http://localhost:9100/fibbee`

6) Now you can use stream in your html page!

`<script type="text/javascript" src="jsmpeg/jsmpeg.min.js"></script>`
 `<div class="jsmpeg" data-url="ws://localhost:9000/" data-loop="true" data-autoplay="true"></div>`
You can find simple example of html page: jsmpeg/view_stream.html or fibbee.html in current project
