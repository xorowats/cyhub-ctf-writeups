# Torrent pcap

We've got a pcapng packet capture file, so lets open it up with wireshark and see whats inside.
![Banner](images/tp1.PNG?raw=true "tp1")
So the first thing that catches the eye are the packets which are BitTorrent protocol handshakes, number 14 and 25. 
Looking at the hint we can assume that a file is beeing transfered using the bittorrent protocol. There are two handshakes, one between 192.168.0.102 and 192.168.0.103, one 192.168.0.102 and 192.168.0.101.
Knowing a bit about how the torrent protocol works we can assume that 192.168.0.102 is the one downloading and 103 and 101 are the seeds. 
If we look at the later packets we can that 1. There are (I'm guessing) request packets from 102 to the others with a small size of 62 followed by a response packet with size 1480 whick I'm guessing are data packets.
Lets sort the packets by size and we see there are about a 100 data packets. It's going to take some time to look for a file in there so let's dump the data packets in a file and run binwalk on it to see if we find any files in there.
