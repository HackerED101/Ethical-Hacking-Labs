## Footprinting with Windows Command Line


### 1. Ping the Website

#### Description
Pinging a website is a fundamental network troubleshooting command that sends ICMP echo requests to the specified destination to check connectivity and measure round-trip time.

#### Command
Open Command Prompt or PowerShell and use the `ping` command followed by the website URL:

```cmd
ping www.example.com
```


### 2. Finding the Maximum Frame Size of the Network

#### Description
Determining the Maximum Transmission Unit (MTU) or maximum frame size of a network helps optimize data transmission efficiency and troubleshoot network issues related to packet size.

#### Command
Use the `ping` command with the `-f` (do not fragment) and `-l` (size) parameters to incrementally test frame sizes until you find the maximum supported by the network:

```cmd
ping www.example.com -f -l 1500
```


### 3. Test Different Frame Sizes

#### Description
Continuing from the previous step, adjusting the frame size (`-l`) parameter allows you to find the largest packet size without fragmentation, which aids in network optimization and troubleshooting.

#### Command
Iterate through different `-l` values until you determine the maximum supported frame size:

```cmd
ping www.example.com -f -l 1472
```


### 4. Investigate Time-to-Live (TTL)

#### Description
Time-to-Live (TTL) is a value in IP packet headers that specifies the maximum number of hops (routers) a packet can traverse before being discarded. Investigating TTL values provides insights into network topology.

#### Command
Use the `-i` (TTL) parameter with the `ping` command to analyze TTL values:

```cmd
ping www.example.com -i 3
```
- Here, `3` can be replaced with any value between `1` to `255` to observe the TTL behavior.


### 5. Trace Route to the Website

#### Description
Traceroute (tracert) is a command-line tool that displays the route and measures transit delays of packets across an IP network. It helps identify network path and potential bottlenecks.

#### Command
Open Command Prompt or PowerShell and use the `tracert` command followed by the website URL to trace the route:

```cmd
tracert www.example.com
```


### 6. Checking the Lifespan of a Packet

#### Description
Determining the Time-to-Live (TTL) value required for a packet to reach the destination IP address helps understand the network's topology and routing configuration.

#### Command
Open a new Command Prompt or PowerShell window and use the `ping` command with the `-i` (TTL) parameter to incrementally test TTL values until reaching the destination:

```cmd
ping www.example.com -i 2 -n 1
```
- Increase the `-i` value until you match the IP address obtained from the `tracert` command.


### 7. Using nslookup Command

#### Description
Nslookup is a command-line administrative tool for querying the Domain Name System (DNS) to obtain domain names, IP addresses, and other DNS records.

#### Command
Open Command Prompt or PowerShell and use the `nslookup` command to perform various DNS queries:

- **Query IP Address (A Record):**
  ```cmd
  nslookup
  > set type=A
  > www.example.com
  ```

- **Query Authoritative Name Server (CNAME Record):**
  ```cmd
  nslookup
  > set type=CNAME
  > www.example.com
  ```

- **Query IP Address from Specific DNS Server (A Record):**
  ```cmd
  nslookup
  > set type=A
  > www.example.com
  ```

