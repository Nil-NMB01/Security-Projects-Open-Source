# Cybersecurity Incident Report

**In this project,** I investigated a fictive incident where the website **www.yummyrecipesforme.com** suddenly became unreachable for multiple users, displaying the error “destination port unreachable” after a timeout.

## Output tcpdump CLI
![alt text](https://raw.githubusercontent.com/Nil-NMB01/Security-Projects-Open-Source/refs/heads/main/media/Network%20Traffic%20Analysis%20November%202025.png)

## Network Traffic Analysis

| Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log. |
| --- |
| The UDP protocol reveals that port 53 is unreachable when attempting to send UDP packets succesfully through a query to the DNS of the website yummyrecipesforme.<br><br>This is based on the results of the network analysis, which show that the ICMP echo reply returned the error message: "UDP port 53 unreachable length"<br><br>The port noted in the error message is used for DNS service (UDP port 53)<br><br>The most likely issue is that the website is currently not accessible for everyone. It is possible that this is a indication of DoS attack or a outage. |

| Part 2: Explain your analysis of the data and provide at least one cause of the incident. |
| --- |
| The incident occurred this noon when several customers of clients reported that they are unable to access the client company website <www.yummyrecipesforme.com>, and saw the error "destination port unreachable" after waiting for the page to load.<br><br>I was tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, I attempted to visit the website and I also received the error "destination port unreachable."<br><br>To troubleshoot the issue, I read the log through tcpdump that was provided to me.<br><br>To load the webpage, my browser sent a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this was part of the DNS protocol.<br><br>My browser then used this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage. The analyzer showed that when I sent UDP packets to the DNS server, I received ICMP packets containing the error message: "udp port 53 unreachable."<br><br>The incident most likely is a result of a DoS attack or a outage. |
