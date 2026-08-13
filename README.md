# PCAP-Network-Traffic-Analysis
cybersecurity project analysing PCAP NETWORK TRAFFICUSING A-PAckets, including DNS, IP addresses, ports, HTTP GET/POST requests, and basic security observations.
# PCAP Network Traffic Analysis

## Project Overview

This project demonstrates my beginner-level network traffic analysis skills using a public PCAP capture.

The analysis was performed using **A-Packets**, a browser-based PCAP analysis platform, without installing Wireshark.

The objective was to identify network devices, IP addresses, protocols, ports, DNS activity and HTTP requests and understand how devices communicated across the network.

## Tools Used

* A-Packets Online PCAP Analyzer
* Public PCAP capture
* Web browser
* GitHub

## Skills Demonstrated

* PCAP analysis
* IPv4 and IPv6 identification
* Private vs public IP identification
* DNS and mDNS analysis
* Network connection analysis
* Port analysis
* HTTP analysis
* GET and POST request analysis
* HTTP header analysis
* Basic network security analysis

## 1. Network Traffic Overview
![Network Traffic Overview](screenshots/01-network-overview.png)

I first examined the overall network traffic contained in the PCAP.

The capture contained multiple network connections and both IPv4 and IPv6 traffic.

Examples of private IPv4 addresses observed included:

`192.168.1.1`

`192.168.1.175`

## 2. DNS Analysis
![DNS Analysis](screenshots/02-dns-analysis.png)

![mDNS Analysis](screenshots/03-mdns-analysis.png)

I examined the DNS section to understand name-resolution activity.

The observed DNS transactions did not report DNS resolution errors.

I also identified **mDNS (Multicast DNS)** traffic.

mDNS allows devices on the same local network to discover hosts and services without relying on a traditional DNS server.

Multicast addresses observed included:

* `224.0.0.251` — IPv4 mDNS multicast address
* `ff02::fb` — IPv6 mDNS multicast address

## 3. Connection Analysis
![Network Connections](screenshots/04-connections.png)

One connection observed was:

`192.168.1.1 → 192.168.1.175`

Approximately **13.99 KB** of traffic was transferred in this direction.

Both addresses are private IPv4 addresses.

Traffic was also observed in the opposite direction:

`192.168.1.175 → 192.168.1.1`

The capture also contained connections involving IPv6 addresses.

## 4. Open Port Analysis
![Port 80 HTTP](screenshots/05-open-port-80.png)

The analysis identified:

`192.168.1.1 → Port 80 → HTTP`

Port **80** is commonly associated with HTTP web services.

HTTP normally transmits application-layer information without the encryption provided by HTTPS/TLS.

Further HTTP analysis indicated that `192.168.1.1` was providing a web-based diagnostic interface.

## 5. HTTP Method Analysis
![HTTP Methods](screenshots/06-http-methods.png)

The PCAP contained three HTTP requests:

* **2 GET requests**
* **1 POST request**

A **GET** request is normally used to request or retrieve a resource from a server.

A **POST** request is commonly used to submit data or request an action from a server.

## 6. HTTP GET Analysis
![HTTP GET Request](screenshots/07-http-get-analysis.png)

One HTTP request observed was:

`GET /api/diagnostics/tracing/details.jst HTTP/1.1`

The destination host was:

`192.168.1.1`

The User-Agent indicated:

* Android 10
* Chrome-based mobile browser

The Referer pointed to:

`http://192.168.1.1/status-and-support/diagnostic-utility.jst`

This provided evidence that a client was interacting with a web-based diagnostic utility hosted on the local network device.

## 7. HTTP POST Analysis
![HTTP POST Request](screenshots/08-http-post-analysis.png)

The POST request identified was:

`POST /api/diagnostics/tracing/delete.jst HTTP/1.1`

Important information included:

* **Host:** `192.168.1.1`
* **HTTP Version:** `HTTP/1.1`
* **Content-Length:** `75 bytes`
* **Content-Type:** `application/x-www-form-urlencoded`
* **Client:** Android 10 / Chrome

The endpoint name suggests that the POST request was performing a delete operation related to diagnostic tracing data.

## 8. Security Observation

During the HTTP analysis, a session-related cookie was visible within the captured HTTP headers.

The actual cookie value is intentionally excluded from this report.

Because the communication used HTTP rather than HTTPS, application-layer information could be observed in the packet capture.

This demonstrates an important security difference between HTTP and HTTPS. HTTPS uses TLS to protect application traffic while it is transmitted across the network.

## 9. What I Learned

Through this project, I learned how to:

* Identify source and destination IP addresses
* Distinguish private and public IP addresses
* Recognize IPv4 and IPv6 traffic
* Identify DNS and mDNS traffic
* Analyze communication between network devices
* Identify ports and associated services
* Understand HTTP GET and POST methods
* Analyze HTTP headers
* Identify client information using the User-Agent
* Recognize security concerns associated with unencrypted HTTP traffic

## Conclusion

This beginner PCAP analysis provided practical experience investigating network traffic.

By examining DNS activity, network connections, ports and HTTP requests, I was able to understand some of the communication occurring between a client device and a local web interface.

This project provided a foundation for further study in network security, packet analysis and cybersecurity incident investigation.
# PCAP Network Traffic Analysis

## Project Overview

This project demonstrates my beginner-level network traffic analysis skills using a public PCAP capture.

The analysis was performed using **A-Packets**, a browser-based PCAP analysis platform, without installing Wireshark.

The objective was to identify network devices, IP addresses, protocols, ports, DNS activity and HTTP requests and understand how devices communicated across the network.

## Tools Used

* A-Packets Online PCAP Analyzer
* Public PCAP capture
* Web browser
* GitHub

## Skills Demonstrated

* PCAP analysis
* IPv4 and IPv6 identification
* Private vs public IP identification
* DNS and mDNS analysis
* Network connection analysis
* Port analysis
* HTTP analysis
* GET and POST request analysis
* HTTP header analysis
* Basic network security analysis

## 1. Network Traffic Overview

I first examined the overall network traffic contained in the PCAP.

The capture contained multiple network connections and both IPv4 and IPv6 traffic.

Examples of private IPv4 addresses observed included:

`192.168.1.1`

`192.168.1.175`

## 2. DNS Analysis

I examined the DNS section to understand name-resolution activity.

The observed DNS transactions did not report DNS resolution errors.

I also identified **mDNS (Multicast DNS)** traffic.

mDNS allows devices on the same local network to discover hosts and services without relying on a traditional DNS server.

Multicast addresses observed included:

* `224.0.0.251` — IPv4 mDNS multicast address
* `ff02::fb` — IPv6 mDNS multicast address

## 3. Connection Analysis

One connection observed was:

`192.168.1.1 → 192.168.1.175`

Approximately **13.99 KB** of traffic was transferred in this direction.

Both addresses are private IPv4 addresses.

Traffic was also observed in the opposite direction:

`192.168.1.175 → 192.168.1.1`

The capture also contained connections involving IPv6 addresses.

## 4. Open Port Analysis

The analysis identified:

`192.168.1.1 → Port 80 → HTTP`

Port **80** is commonly associated with HTTP web services.

HTTP normally transmits application-layer information without the encryption provided by HTTPS/TLS.

Further HTTP analysis indicated that `192.168.1.1` was providing a web-based diagnostic interface.

## 5. HTTP Method Analysis

The PCAP contained three HTTP requests:

* **2 GET requests**
* **1 POST request**

A **GET** request is normally used to request or retrieve a resource from a server.

A **POST** request is commonly used to submit data or request an action from a server.

## 6. HTTP GET Analysis

One HTTP request observed was:

`GET /api/diagnostics/tracing/details.jst HTTP/1.1`

The destination host was:

`192.168.1.1`

The User-Agent indicated:

* Android 10
* Chrome-based mobile browser

The Referer pointed to:

`http://192.168.1.1/status-and-support/diagnostic-utility.jst`

This provided evidence that a client was interacting with a web-based diagnostic utility hosted on the local network device.

## 7. HTTP POST Analysis

The POST request identified was:

`POST /api/diagnostics/tracing/delete.jst HTTP/1.1`

Important information included:

* **Host:** `192.168.1.1`
* **HTTP Version:** `HTTP/1.1`
* **Content-Length:** `75 bytes`
* **Content-Type:** `application/x-www-form-urlencoded`
* **Client:** Android 10 / Chrome

The endpoint name suggests that the POST request was performing a delete operation related to diagnostic tracing data.

## 8. Security Observation

During the HTTP analysis, a session-related cookie was visible within the captured HTTP headers.

The actual cookie value is intentionally excluded from this report.

Because the communication used HTTP rather than HTTPS, application-layer information could be observed in the packet capture.

This demonstrates an important security difference between HTTP and HTTPS. HTTPS uses TLS to protect application traffic while it is transmitted across the network.

## 9. What I Learned

Through this project, I learned how to:

* Identify source and destination IP addresses
* Distinguish private and public IP addresses
* Recognize IPv4 and IPv6 traffic
* Identify DNS and mDNS traffic
* Analyze communication between network devices
* Identify ports and associated services
* Understand HTTP GET and POST methods
* Analyze HTTP headers
* Identify client information using the User-Agent
* Recognize security concerns associated with unencrypted HTTP traffic

## Conclusion

This beginner PCAP analysis provided practical experience investigating network traffic.

By examining DNS activity, network connections, ports and HTTP requests, I was able to understand some of the communication occurring between a client device and a local web interface.

This project provided a foundation for further study in network security, packet analysis and cybersecurity incident investigation.
