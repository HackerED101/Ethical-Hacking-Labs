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
