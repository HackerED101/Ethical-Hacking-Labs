# Tutorial: Sniffing Traffic from slate.nu.edu.pk using Ettercap

## Overview
In this tutorial, we'll use Ettercap to sniff network traffic from slate.nu.edu.pk. Ettercap is a powerful tool for man-in-the-middle attacks and network sniffing.


## Configuring Kali Linux Network Settings in VirtualBox

### Overview
This guide will help you configure Kali Linux in VirtualBox with the network settings specified.

### Configuring Network in VirtualBox

1. **Open VirtualBox:**
   Launch VirtualBox on your host machine.

2. **Select Kali Linux VM:**
   - Select your Kali Linux virtual machine from the VirtualBox Manager.

3. **Access Settings:**
   - Right-click on the Kali Linux VM and select `Settings`.

4. **Configure Network Settings:**

   - In the VM settings window, go to the `Network` tab.

   - Under `Attached to`, select `Bridged Adapter`.

   - Under `Name`, choose your network driver from the dropdown list. This typically corresponds to your physical network adapter.

   - Check the box for `Promiscuous Mode` and select `Allow All` from the dropdown menu.

5. **Apply Settings:**
   - Click `OK` to apply the network settings.

6. **Start Kali Linux:**
   - Start the Kali Linux VM by clicking on `Start` in the VirtualBox Manager.

7. **Verify Network Configuration:**
   - Once Kali Linux boots up, open a terminal.

   - Use the following command to check network interfaces:
     ```bash
     ip addr show
     ```
     Ensure that your network interface (`eth0`, `eth1`, `wlan0`, etc.) is listed and configured correctly.


### Checking IP Address on Kali Linux

1. **Open a Terminal:**
   - Launch a terminal window on your Kali Linux machine. You can do this by clicking on the terminal icon in the desktop environment or by using the keyboard shortcut `Ctrl+Alt+T`.

2. **Use the `ip` Command:**
   - In the terminal, type the following command and press Enter:
     ```bash
     ip addr show
     ```
   - This command will display detailed information about all network interfaces configured on your Kali Linux machine.

3. **Identify the IP Address:**
   - Look for the IP address associated with the network interface you are interested in. For example, if you're using Ethernet, you might see an interface named `eth0`, or if you're using Wi-Fi, you might see an interface named `wlan0`.
   - The IP address is typically listed under the `inet` section next to the corresponding network interface. It will look something like `192.168.1.100`.


### Checking IP Address on Host Machine (Windows)

1. **Open Command Prompt:**
   - On Windows, open Command Prompt. You can do this by pressing `Win + R`, typing `cmd`, and pressing Enter.

2. **Use the `ipconfig` Command:**
   - To check the IP address of your host machine, use:
     ```cmd
     ipconfig
     ```
   - Look for the `IPv4 Address` under the network adapter you are using (`Ethernet adapter` for wired or `Wireless LAN adapter` for wireless).

### Checking Gateway IP Address (Windows)

1. **Use the `ipconfig` Command:**
   - To find the gateway (router) IP address that your host is using on Windows, use:
     ```cmd
     ipconfig /all
     ```
   - Look for the `Default Gateway` under the network adapter you are using (`Ethernet adapter` for wired or `Wireless LAN adapter` for wireless).


### Steps to Ping Your Host Machine from Kali Linux

1. **Find the IP Address of Your Host Machine:**
   - First, find out the IP address of your host machine (the machine you want to ping). You can do this by following the steps mentioned earlier for checking the IP address on your host machine.

2. **Open a Terminal on Kali Linux:**
   - Launch a terminal on your Kali Linux machine. You can do this by clicking on the terminal icon or using the shortcut `Ctrl+Alt+T`.

3. **Ping Your Host Machine:**
   - In the terminal, use the `ping` command followed by the IP address of your host machine. For example:
     ```bash
     ping <host_ip_address>
     ```
   - Replace `<host_ip_address>` with the actual IP address of your host machine.

4. **Interpreting Ping Results:**
   - Once you execute the command, Kali Linux will start sending ICMP echo requests to your host machine.
   - You should see responses (ICMP echo replies) coming back from your host machine if the ping is successful.
   - Press `Ctrl+C` to stop the ping process when you're done. It will also display statistics about the ping results.

### Example
If the IP address of your host machine (Windows example) is `192.168.1.101`, you would run:
```bash
ping 192.168.1.101
```

### Troubleshooting Tips
- **Firewall Issues:** If you don't receive responses, check the firewall settings on your host machine. Ensure that ICMP traffic (ping requests) is allowed.
- **Network Configuration:** Double-check that both Kali Linux and your host machine are connected to the same network segment and subnet.
- **IP Address:** Verify that you're using the correct IP address of the host machine.


## Opening Ettercap GUI

1. **Open a Terminal:**
   - Launch a terminal on your Kali Linux machine. You can do this by clicking on the terminal icon or using the shortcut `Ctrl+Alt+T`.

2. **Run Ettercap with Graphical Interface:**
   - To start Ettercap in graphical mode, use the following command:
     ```bash
     sudo ettercap -G
     ```
   - This command launches Ettercap with the graphical interface (`-G`) and grants it elevated privileges (`sudo`).

3. **Graphical Interface Usage:**
   - Once Ettercap starts, you will see its graphical interface.

4. **Note:** Depending on your Kali Linux setup, you might need to install Ettercap if it's not already installed. You can install it using the following command:
   ```bash
   sudo apt update
   sudo apt install ettercap-graphical
   ```

5. **Additional Options:**
If it isn't working, you can check if the network is in network mode by running iwconfig.


### Steps to Search for Hosts and Perform ARP Poisoning in Ettercap

1. **Select Network Interface:**
   - Click on `Sniff` in the top menu and select `Unified Sniffing`.
   - Choose the appropriate network interface (e.g., `eth0` for Ethernet, `wlan0` for Wi-Fi) and click `OK`.

2. **Scan for Hosts:**
   - Click on `Hosts` in the top menu and select `Scan for Hosts`.
   - Ettercap will scan the network to discover active hosts. Wait for the scan to complete.

3. **View Host List:**
   - After scanning, click on `Hosts` in the top menu and select `Host List`.
   - This will display a list of discovered hosts along with their IP addresses and MAC addresses.

4. **Select Target Host:**
   - Identify the IP address of your host machine (the one you want to perform ARP poisoning on) from the host list.

5. **Perform ARP Poisoning:**
   - Click on `Mitm` in the top menu and select `ARP Poisoning`.
   - In the ARP poisoning dialog box:
     - Select `Sniff remote connections`.
     - Select `Poison only one way`.
     - Click `OK` to start ARP poisoning.

6. **Monitor ARP Poisoning:**
   - Ettercap will start poisoning the ARP cache of the selected host, redirecting its traffic through your Kali Linux machine.

### Caution:
- **Legal and Ethical Considerations:** Ensure you have proper authorization to perform these actions on the network. Unauthorized access or monitoring of network traffic can violate laws and ethical guidelines.
- **Use Responsibly:** ARP poisoning is a technique used in security testing and should only be used in controlled environments and with permission.


#### Capture Login Credentials

1. **Start Capturing Data:**
   - Click on `Start` in the top menu and select `Start sniffing`.
   - Ettercap will now intercept and capture network traffic passing through your Kali Linux machine.

#### Access Login Page and Enter Credentials

2. **Access Website Login Page:**
   - On your host machine (not on Kali Linux), open a web browser and navigate to the login page of any website where you want to capture credentials.

3. **Enter Username and Password:**
   - Enter a username and password on the login page. For example, this could be on a social media platform or any website with login functionality.

#### Monitor Captured Credentials

4. **View Captured Data:**
   - In the Ettercap graphical interface, click on `View` in the top menu and select `Connections`.
   - This will display captured connections and any plaintext data, such as usernames and passwords, that were intercepted.

### Ethical Considerations

- **Legal Permission:** Ensure you have explicit authorization to perform such tests on the network. Unauthorized interception of data is illegal and unethical.
- **Use in Controlled Environments:** Practice these techniques in environments you control or where you have permission to perform security testing.
- **Protect Privacy:** Handle captured data responsibly and ensure it is not exposed to unauthorized individuals.
