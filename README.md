
gr-osmosdr-udp-support
======================

This patch adds UDP sink and UDP source blocks to gr-osmosdr.

To apply the patch, clone a recent gr-osmosdr repo and 
then run "git apply" on the included diff file.

    $ git clone git://git.osmocom.org/gr-osmosdr
    $ cd gr-osmosdr
    $ git apply ../gr-osmosdr.diff

Use the UDP source to read a complex IQ stream from a UDP socket.
Say you have a SDR radio that sends its stream to a particular 
UDP socket.  To read this stream, use a UDP source.  On 
the other hand the UDP sink is used to send a complex IQ stream
to a UDP socket.  

Both UDP sink and source blocks use the following
parameters.

    host="<hostname of UDP socket>"
    port=<port number of the UDP socket>
    throttle=<set to true or false>
    freq=<frequency of the complex IQ stream>
    rate=<sample rate of the complex IQ stream>

For example in GQRX to read a complex IQ stream that is being
sent to a UDP socket located on your host on port 7777 with
a frequency of 100 MHz and a sampling rate of 1 MSPS, set the
device string to:

    udp,host="0.0.0.0",port=7777,freq=100e6,rate=1e6,throttle=false

It is recommended to disable the throttle.

Copyright (c) 2017 roseengineering

