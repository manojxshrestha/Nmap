# Nmap

![nmap-logo-1-1024x597-01](https://user-images.githubusercontent.com/106522935/202653349-2b81f1fe-b6d7-4b05-9164-91806e6d1fcb.jpeg)


Nmap is a network utility tool  which is used to enumerate hosts in the network , perform  reconnaissance or information gathering , vulnerability detection , exploitation and much more. 

# Installation

    $ sudo apt-get install nmap

or

    $ sudo apt install nmap
    
    $ git clone https://github.com/nmap/nmap.git

    $ ./configure

    $ make

    $ make install


# Host Discovery

Discovering the target host(s) is the first step towards network reconnaissance. There are multiple ways through which we can determine if the hosts are alive or not.

# Single IP Scan
To scan a single ip we simply give one ip as follows:

     sudo nmap -sn 192.168.254.10
     
<img width="551" alt="Screen Shot 2021-03-06 at 09 57 08" src="https://user-images.githubusercontent.com/106522935/202651409-6e6afad2-258c-4d68-84ac-e77bad336a63.png">

     
     -sn means disable port scanning
 

# 
