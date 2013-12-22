Libgnuemu_packet
================

Lib for sending packets and queue messages written in C . based on pcap

#Sending simple packet 
make sur that you have <b>libgnuemu_packets.dll</b> in same folder as your application.

than in your main project application add :

Fisrt define the MAX_ADAPTER  

use #define MAX_ADAPTER 1024 
and then add this :

     HINSTANCE DLLHandle;
     typedef int(*lib)(char [MAX_ADAPTER]);
     lib libgnuemu_packet;
     DLLHandle = LoadLibrary("libgnuemu_packets.dll");

     libgnuemu_packet = (lib)GetProcAddress(DLLHandle,"send_test_packets");
     libgnuemu_packet("testing adapter");

     FreeLibrary(DLLHandle);

     return;
     
