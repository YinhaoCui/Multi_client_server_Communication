
## How to Run

To run my program, navigate to the folder and run the command "python3 program.py"

## Program Description

This program is a streaming video server and client that communicate and send data
using the following two protocols, respectively: Real-Time Streaming Protocol (RTSP) and Real-time
Transfer Protocol (RTP).

## Program Design

Client, ClientLauncher

The ClientLauncher starts the Client and the user interface which you use to send RTSP commands, and which is used to display the video. when the buttons are pressed. it will implement SETUP ,PLAY, PAUSE and TEARDOWN.

ServerWorker, Server

These two modules implement the server which responds to the RTSP requests and streams back the video. The RTSP interaction is already implemented and the ServerWorker calls methods from the RtpPacket class to packetize the video data. 
On the server side, it will need to implement the packetization of the video data into RTP packets. it
will need to create the packet, set the fields in the packet header and copy the payload (i.e., one video frame)
into the packet.
When the server receives the PLAY-request from the client, the server reads one video frame from the file
and creates an RtpPacket-object which is the RTP-encapsulation of the video frame. It then sends the frame
to the client over UDP every 50 milliseconds.
For the encapsulation, the server calls the encode function of the RtpPacket class.

RtpPacket
This class is used to handle the RTP packets. It has separate methods for handling the received packets at the client side . The Client also de-packetizes (decodes) the data。

VideoStream
This class is used to read video data from the file on disk. 


## Submission Notes

I completed the bonus and the regular section!

For bonus part I have two plans. The first plan is to merge the SETUP and PLAY buttons. Although this is not quite right, it still meets the requirements of the problem. In this case, SETUP will be executed when the PLAY button is used for the first time. After that, the other buttons are in normal use. The first plan is obviously not perfect. The purpose of removing a button is not to allow you to use the other buttons one more time. My second plan, and the plan I finally executed, is to directly execute the SETUP command after connecting the SETUP client to the server, so that no extra clicks and three buttons are needed to perform tasks.

