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
     
TCP SYN scan
     
     nmap -sS 192.168.1.1
     
Scan UDP ports	

     nmap -sU 192.168.1.1
     
     nmap -sU -p 123,161,162 192.168.1.1
    
ACK Scan
     
     nmap -sA 192.168.1.1
     
Scan selected ports - ignore discovery	
     
     nmap -Pn -F 192.168.1.1
          
# Service and OS Detection

Detect OS and Services

     nmap -A 192.168.1.1
 
# OS Identification

Nmap can also identify the OS of the target machine by comparing its responses to a database of OS fingerprints.

To activate this functionality, you can use the -O option.

     nmap -O scanme.nmap.org

![174544805-d00171b7-bb95-49b9-b515-a5b224a10f18](https://user-images.githubusercontent.com/106522935/202688440-48630a12-90ca-4180-becb-2dca3f37d11e.png)

# OS Version Detection

One other useful feature is version detection, which you can enable using the -sV option.

     nmap -sV scanme.nmap.org
     
![174544911-36b20e20-4829-4846-9e33-77ccad418e74](https://user-images.githubusercontent.com/106522935/202689317-838fa3df-55fe-4480-aefa-41bc61bd467c.png)
   
# Output

By default, Nmap displays the results of the scan in the standard output (stdout). But you can also specify other types of output.

If you add the option -oN followed by a file name, then the output will be saved to the given file name.
![nmap-output-file-768x393](https://user-images.githubusercontent.com/106522935/174545126-3534b755-d03b-4223-8a14-2f1ed0ab38a8.png)

Normal output to a file

The above command generates the following file:

![nmap-resulted-normal-file](https://user-images.githubusercontent.com/106522935/174545446-80ddf3e1-9888-4eea-8e1d-deb72a88fed4.png)

Although this is a good format for humans to read, it isn’t as easily understandable by scripts if you ever decide to send the output to another tool.

For this reason, Nmap also supports XML, which can be easily parsed by another program.

If you want to retrieve an XML file as an output, you can use the option -oX.

![nmap-xml-output (1)](https://user-images.githubusercontent.com/106522935/174545647-ffca05e7-ba84-45f7-bf2e-6769de522b09.png)

Output to an XML file

And here is the generated XML file:

![nmap-resulted-xml-file (1)](https://user-images.githubusercontent.com/106522935/174545757-c1778f4a-dab6-406b-84f8-f364e1d95fb9.png)


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
      
# Simple Command for Scanning your Local Network (Class C or /24):

     nmap -sV -p 1-65535 192.168.1.1/24
 
# Detect Heartbleed SSL Vulnerability

Heartbleed Testing	
     
     nmap -sV -p 443 --script=ssl-heartbleed 192.168.1.0/24
     
Heartbleed detection is one of the available SSL scripts. It will detect the presence of the well known Heartbleed vulnerability in SSL services. Specify alternative ports to test SSL on mail and other protocols.

# IP Address information

Find Information about IP address	

     nmap --script=asn-query,whois,ip-geolocation-maxmind 192.168.1.0/24
     
Gather information related to the IP address and netblock owner of the IP address. Uses ASN, whois and geoip location lookups. See the IP Tools for more information and similar IP address and DNS lookups.

# Summary 

You should now have a basic understanding of Nmap and how you can use it. You can perform your own scans and experiment by combining the options that you’ve learned here.

Of course, Nmap supports other options that we didn’t cover in this post. In fact, we’ve only scratched the surface here.

For further reading, you can refer to the official Nmap reference guide, and if you ever need help while typing a command, just type in the following command: nmap --help.

