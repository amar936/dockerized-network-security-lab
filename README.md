# Dockerized Network Security Lab

## Project Overview
A containerized network security lab built using Docker Compose to practice network scanning and HTTP service testing in an isolated Docker network.

## Tools & Technologies
- Docker Desktop
- Docker Compose
- Nmap
- Netshoot
- Nginx
- Linux shell commands

## Architecture
The lab contains two containers connected through a private Docker network:

- **lab-target:** Nginx web server used as the target.
- **lab-tester:** Netshoot container used for network troubleshooting and security testing.

## Setup
1. Install Docker Desktop.
2. Clone or download this repository.
3. Open a terminal in the project directory.
4. Start the containers:

   `docker compose up -d`

5. Enter the tester container:

   `docker exec -it lab-tester sh`

## Testing

Check HTTP response:

`curl -I http://target`

Expected result: HTTP `200 OK` when the target is reachable and Nginx is responding.

Scan selected ports:

`nmap -sT -p 22,80,443 target`

## What I Learned
- Containerization using Docker.
- Creating services with Docker Compose.
- Container-to-container communication.
- Using Nmap for port scanning.
- Testing HTTP services using curl.
- Isolating lab services on a private Docker network.

## Disclaimer
This lab is intended for learning and authorized security testing only.

Output:

PS C:\Users\Wifonic\dockerized-network-security-lab> docker exec -it lab-tester sh
~ #
~ # nmap -sT -p 22,80,443 target
Starting Nmap 7.99 ( https://nmap.org ) at 2026-10-23 10:22 +0000
Nmap scan report for target (172.18.0.2)
Host is up (0.00029s latency).
rDNS record for 172.18.0.2: lab-target.security-lab

PORT    STATE  SERVICE
22/tcp  closed ssh
80/tcp  open   http
443/tcp closed https
MAC Address: 3E:3C:4A:A5:8F:C6 (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 0.86 seconds
~ # curl -I http://target
HTTP/1.1 200 OK
Server: nginx/1.31.8
Date: Fri, 23 Oct 2026 10:23:35 GMT
Content-Type: text/html
Content-Length: 896
Last-Modified: Wed, 21 Oct 2026 17:54:44 GMT
Connection: keep-alive
ETag: "6ad8fc64-380"
Accept-Ranges: bytes
