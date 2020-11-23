# Torrent pcap

We've got a pcapng packet capture file, so let's open it up with wireshark and see what's inside.
![Banner](images/tp1.PNG?raw=true "tp1")
So the first thing that catches the eye are the packets which are BitTorrent protocol handshakes, number 14 and 25. 
Looking at the hint we can assume that a file is being transfered using the bittorrent protocol. There are two handshakes, one between 192.168.0.102 and 192.168.0.103, one 192.168.0.102 and 192.168.0.101.
Knowing a bit about how the torrent protocol works we can assume that 192.168.0.102 is the one downloading and 103 and 101 are the seeds. 
If we look at the later packets we can that 1. There are (I'm guessing) request packets from 102 to the others with a small size of 62 followed by a response packet with size 1480 which I'm guessing are data packets.
Let's sort the packets by size, and we see there are about a 100 data packets. While I was looking through the data packets I was lucky to notice a png header in the packet 201, so It's a png image. The proper way to find that header would probably be dumping all the data from the packets to a file, then running bin walk on it, it should find the header. 
![Banner](images/tp2.PNG?raw=true "tp2")
Previously I tried looking with other packet analyzer tools, but found nothing, guess not a lot of people are looking at bittorrent protocol. After finding the header of the file which is the start, it was a matter of finding the order in which the parts of the image were transmitted. After reading a bit about the torrent protocol a looking around for a bit I noticed that there is one byte in the packets at position 0x3B that was increasing by one on every other data packet. Example in packet 201 it's value was 43, in 204 - 44, in 206 - 45. And between some packets the data had some overlap, some bytes from the end of 211 for example were in the start of 213. 
![Banner](images/tp3.PNG?raw=true "tp3")
![Banner](images/tp4.PNG?raw=true "tp4")
Using the overlaps I managed to reconstruct the image by hand :D But I'm sure with these findings I could write a script to automate this. And here's the flag.

![Banner](images/tp2.PNG?raw=true "tp5")
