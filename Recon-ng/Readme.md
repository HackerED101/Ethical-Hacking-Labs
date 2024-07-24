### Running Recon-ng and Creating a New Workspace

1. **Open the Terminal:**
   - In your Kali Linux, open the terminal.

2. **Launch Recon-ng:**
   - Type the following command and press Enter:
     ```bash
     recon-ng
     ```
   - This command starts Recon-ng, initializing the framework for reconnaissance activities.

3. **Create a New Workspace:**
   - Once Recon-ng is running, you need to create a new workspace. In this example, let's name it `CEH` (Certified Ethical Hacker):
     ```bash
     workspace create CEH
     ```
   - This command sets up a new workspace named `CEH` within Recon-ng. Workspaces help organize your reconnaissance data and activities.

4. **Verify Workspace Creation:**
   - To confirm that the workspace `CEH` was successfully created, you can list all available workspaces:
     ```bash
     workspaces list
     ```
   - You should see `CEH` listed among the workspaces, indicating it has been created and is active.

### Setting target domain exploring marketplace

1. **Set Target Domain:**
   - Once inside Recon-ng, you need to set the target domain for network reconnaissance. Replace `example.com` with your actual target domain:
     ```bash
     >db insert domains
     >certifiedhacker.com
     ```
   - You can view the added the domain by typing:   
     ```bash
     show domains
     ```

2. **Load Modules from the Marketplace:**
   - Recon-ng offers various modules through its marketplace for specific reconnaissance tasks. Here’s how you can load and use them:
   
     a. **List Available Modules:**
        - To list all available modules in the marketplace, use:
          ```bash
          marketplace search
          ```
        - This command displays a list of modules categorized by different types of reconnaissance activities.

     b. **Load a Specific Module:**
        - Choose a module relevant to your network reconnaissance needs. For example, we will use the hackertarget module in this tutorial:
          ```bash
          marketplace install hackertarget
          ```
          This command installs the `hackertarget` module which can be used to gather subdomains related to the specified domain.

          ```bash
          modules load hackertarget
          ```
          This will load that module, without loading you will be unable to use it.

3. **Set Target Domain:**
   - After loading the module, set the target domain for reconnaissance. Replace `certifiedhacker.com` with any target domain:
     ```bash
     options set SOURCE certifiedhacker.com
     ```
     - This command sets `certifiedhacker.com` as the target domain for the loaded module.

4. **Run the Module:**
   - Execute the module to perform reconnaissance on the target domain:
     ```bash
     run
     ```
     - This command starts the module and gathers information based on its functionality.

5. **Review Results:**
   - Recon-ng will display results based on the module's execution. Results might include subdomains, IP addresses, URLs, or other relevant information retrieved from the target domain.

### Additional Notes:
- **Explore Marketplace:** The Recon-ng marketplace offers a wide range of modules beyond basic domain and host reconnaissance. Explore modules tailored to your specific reconnaissance objectives.
- **Module Customization:** Each module may have specific options and configurations that can be customized using `options set` before running `run`.
- **Documentation:** Refer to Recon-ng's official documentation for detailed information on available modules and their usage. 
- **Output:** If your response is working correctly but with messy queries and values, just type show hosts for a clean output

 6. **Load brute_hosts from the Marketplace:**
     
     a. **Load a Specific Module:**
     - To install and use another module, you have to exit the first one:
          ```bash
          back
          ```
 - Choose a module relevant to your network reconnaissance needs.We will use brute_hosts module in this tutorial:
          ```bash
          marketplace install recon/domains-hosts/brute_hosts
          ```
- This command installs the `brute_hosts` module which can be used to brute force subdomains related to the specified domain.

            ```bash
          modules load recon/domains-hosts/brute_hosts
          ```
- This will load that module, without loading you will be unable to use it.

7. **Set Target Domain:**
   - After loading the module, set the target domain for reconnaissance. Replace `certifiedhacker.com` with any target domain:
     ```bash
     options set SOURCE certifiedhacker.com
     ```
- This command sets `certifiedhacker.com` as the target domain for the loaded module.
- You can source and wordlists by writing following command:
     ```bash
     info
     ```

8. **Run the Module:**
   - Execute the module to perform reconnaissance on the target domain:
     ```bash
     run
     ```
     - This command starts the module and gathers information based on its functionality.

Certainly! Here's how you can format the instructions in GitHub Markdown format for your README file:


### Generating a Report

Now that you have collected your data, you can create a report containing all the information.

1. **Install Reporting Module from Marketplace:**
   ```bash
   marketplace install reporting/html
   ```
   
2. **Load HTML Reporting Module:**
   ```bash
   modules load reporting/html
   ```
   - This loads the HTML reporting module. Without loading it, you won't be able to use it.

3. **Select Report Format:**
   - You can create a report in several formats. Check the marketplace for supported formats.

4. **Assign Required Values:**
   ```bash
   options set CREATOR <yourname>
   ```
   ```bash
   options set CUSTOMER <yourcustomername>
   ```
   ```bash
   options set FILENAME /home/kali/Desktop/Filename
   ```
   - Replace `<yourname>`, `<yourcustomername>`, and `/home/kali/Desktop/Filename` with appropriate values. `FILENAME` should specify the full path where you want to save the report.

5. **Run the Module:**
   - Execute the module to generate the report:
   ```bash
   run
   ```


### Recon-ng for Gathering Personal Information

#### Gather Contacts Associated with a Domain

This module gathers personal information associated with a domain using WHOIS data.

1. **Install WHOIS Contacts Module:**
   ```bash
   marketplace install recon/domains-contacts/whois_pocs
   ```

2. **Load WHOIS Contacts Module:**
   ```bash
   modules load recon/domains-contacts/whois_pocs
   ```

3. **Check Module Information:**
   - Verify the module's information and options before running:
   ```bash
   info
   ```

4. **Set Target Domain for WHOIS Lookup:**
   - Set the target domain for WHOIS lookup. Replace `facebook.com` with your target domain:
   ```bash
   options set SOURCE facebook.com
   ```

5. **Execute the Module:**
   - Run the module to gather WHOIS contact information:
   ```bash
   run
   ```

   #### Gather Contacts Associated with a Domain
   - We can use profiler to collect information about a person on worldwide internet.
   - To install and use another module, you have to exit the first one:
          ```bash
          back
          ```
 - Install the profiler module:
     ```bash
   marketplace install recon/profiles-profiles/profiler
   ```

- Load the profiler module:
   ```bash
   modules load recon/domains-contacts/whois_pocs
   ```
   
- Replace `MarkZuckerberg` with the username you want to target.
   ```bash
   options set SOURCE MarkZuckerberg
   ```
   - Execute the module to perform the operation:
   ```bash
   run
   ```
