Libgnuemu_packet
================

Lib for sending packets and queue messages written in C . based on pcap

Download libgnuemu_packet.dll and libgnuemu_packet.a 

<a href="http://www.multiupload.nl/7I8EY7PIOP">Link</a>

must have the pcap lib 

#Sending simple packet 
make sure that you have <b>libgnuemu_packets.dll</b> in the same folder as your application.

than in your main project application add :

First define the MAX_ADAPTER  

use #define MAX_ADAPTER 1024 
and then add this :

     HINSTANCE DLLHandle;
     typedef int(*lib)(char [MAX_ADAPTER]);
     lib libgnuemu_packet;
     DLLHandle = LoadLibrary("libgnuemu_packets.dll");

     libgnuemu_packet = (lib)GetProcAddress(DLLHandle,"send_test_packets");
     libgnuemu_packet("YOUR ADAPTER");

     FreeLibrary(DLLHandle);

     return;
     
#Sending queue message
tha same as sending simple packet but you must add this on your main project

     HINSTANCE DLLHandle;
     typedef int(*lib)(char [1024], char, char [MAX_ADAPTER]);
     lib libgnuemu_packet;
     DLLHandle = LoadLibrary("libgnuemu_packets.dll");

     libgnuemu_packet = (lib)GetProcAddress(DLLHandle,"send_queue_packet");
     libgnuemu_packet("queue_file" , "queue_msg", "Your_ADAPTER");

     FreeLibrary(DLLHandle);

     return;
     

     
     
