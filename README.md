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

# Usage:

    $ nmap [options] target
    

# Host Discovery

Discovering the target host(s) is the first step towards network reconnaissance. There are multiple ways through which we can determine if the hosts are alive or not.

If you want to test for open ports in your local network, scanning the entire IP address range might take a lot of time. In this case, you should start first with a host discovery phase in which you detect the available machines.

For instance, if you had to scan the network associated with the IP address 192.168.1.1/24, and only three machines are available, then it wouldn’t make sense to test for open ports in every IP address in that range.

This is where host discovery can be useful. It helps you focus your scanning efforts and, instead of 255 addresses, you will only scan the three addresses belonging to the available machines.

To perform host discovery, simply add the -sn option.

In the following test, I used Nmap to scan for available hosts in my local network.

By providing 192.168.1.0-255 as the target, Nmap will scan all addresses ranging from 192.168.1.0 to 192.168.1.255.

![174541926-a5715b53-407b-4865-b705-13c8301e335c (1)](https://user-images.githubusercontent.com/106522935/202656453-9516cb01-71c6-4adc-b474-d46336a3f177.png)

Nmap – Host Discovery as shown in this output, Nmap detected 5 hosts that are connected to my network.

This type of scan is also called a ping sweep.

# Single IP Scan
To scan a single ip we simply give one ip as follows:

     sudo nmap -sn 192.168.100.9
     

# Nmap Target Selection

Scan a single IP

     nmap 192.168.1.1
     
Scan a domain	

     nmap www.domaimname.com
     
Scan a range of IPs

     nmap 192.168.1.1-20

Scan a subnet

     nmap 192.168.1.0/24
     
Scan targets from a text file

     nmap -iL list-of-ips.txt
     
These are all default scans, which will scan 1000 TCP ports. Host discovery will take place.

# Nmap Port Selection

Scan a single Port	

     nmap -p 22 192.168.1.1
     
Scan a range of ports	

     nmap -p 1-100 192.168.1.1
     
Scan 100 most common ports (Fast)	

     nmap -F 192.168.1.1
     
Scan all 65535 ports	

     nmap -p- 192.168.1.1
    
# Nmap Port Scan types

Scan TCP ports

     nmap -sT 192.168.1.1
     
Scan using TCP SYN scan
     
     nmap -sS 192.168.1.1
     
Scan UDP ports	

     nmap -sU 192.168.1.1
     
     nmap -sU -p 123,161,162 192.168.1.1
     
Scan selected ports - ignore discovery	
     
     nmap -Pn -F 192.168.1.1
          
# Service and OS Detection

Detect OS and Services

     nmap -A 192.168.1.1
 

# Nmap Output Formats

Save default output to file
     
     nmap -oN outputfile.txt 192.168.1.1
     
Save results in a format for grep	

     nmap -oG outputfile.txt 192.168.1.1
     
     
# HTTP Service Information

     Usage : nmap -sV --script=http-enum <target>
     
Gather page titles from HTTP services	
     
     nmap --script=http-title 192.168.1.0/24
     
Get HTTP headers of web services	
     
     nmap --script=http-headers 192.168.1.0/24
     
Find web apps from known paths	

     nmap --script=http-enum 192.168.1.0/24

     
# Scan All TCP UDP Ports
 
      sudo nmap -sU -sT -p0-65535 192.168.122.1
      
# Simple command for scanning your local network (class C or /24):

     nmap -sV -p 1-65535 192.168.1.1/24
 
# Detect Heartbleed SSL Vulnerability

Heartbleed Testing	
     
     nmap -sV -p 443 --script=ssl-heartbleed 192.168.1.0/24
     
Heartbleed detection is one of the available SSL scripts. It will detect the presence of the well known Heartbleed vulnerability in SSL services. Specify alternative ports to test SSL on mail and other protocols.

# IP Address information

Find Information about IP address	

     nmap --script=asn-query,whois,ip-geolocation-maxmind 192.168.1.0/24
     
Gather information related to the IP address and netblock owner of the IP address. Uses ASN, whois and geoip location lookups. See the IP Tools for more information and similar IP address and DNS lookups.


