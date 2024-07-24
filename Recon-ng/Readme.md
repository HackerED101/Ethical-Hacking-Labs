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

To add a target domain and perform network reconnaissance using Recon-ng, you can extend the existing instructions in your GitHub README file. Here’s how you can do it:

5. **Set Target Domain:**
   - Once inside Recon-ng, you need to set the target domain for network reconnaissance. Replace `example.com` with your actual target domain:
     ```bash
     >db insert domains
     >certifiedhacker.com
     ```
    
    
