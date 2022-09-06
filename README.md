# Fibbee_streaming
Use Jsmpeg for rtsp streaming over NAT

![Fibbee](https://user-images.githubusercontent.com/43553016/188693618-7805b4e4-e52c-44bc-a2b9-b0467f5a7d4b.png)


1) Port forwarding

     `ssh -L 8888:192.168.1.22:554 -p port user@host.com`

2) Install ffmpeg https://ffmpeg.org/


3) Clone repo into your project folder
4) 
`git clone https://github.com/JutsFunFor/fibbee_streaming.git`

4) Inside jsmpeg folder:
5) 
`node websocket-relay fibbee 9100 9000`

5) Run ffmpeg decoding session:
6) 
`ffmpeg -rtsp_transport tcp -i rtsp://admin:pipipi@localhost:8888/h264Preview_01_sub
-f mpegts -codec:v mpeg1video -framerate 25
-s 640x480 -b:v 1500k -bf 0 http://localhost:9100/fibbee`

6) Now you can use stream in your html page!
7) 
`<script type="text/javascript" src="jsmpeg/jsmpeg.min.js"></script>`
 `<div class="jsmpeg" data-url="ws://localhost:9000/" data-loop="true" data-autoplay="true"></div>`

