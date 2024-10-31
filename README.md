# Installing Proxmox VE on Hyper-V

This guide provides step-by-step instructions to set up a Proxmox Virtual Environment (VE) on a Hyper-V virtual machine.

## Prerequisites

- **Windows OS with Hyper-V** enabled.
- **Proxmox VE ISO**: [Download from Proxmox’s official website](https://www.proxmox.com/en/downloads).
- **System Resources**: Ideally, have at least 4 GB of RAM and 2 CPU cores for the VM.

---

## Step 1: Set Up a New Virtual Machine in Hyper-V

1. ### Open Hyper-V Manager
   - Launch **Hyper-V Manager** from the Windows Start menu.

2. ### Create a New Virtual Machine
   - In Hyper-V Manager, click on **Action > New > Virtual Machine**.


     ![image](https://github.com/user-attachments/assets/620f53d3-78ff-42b9-a192-f5ca7556e5fa)

   - **Name the VM** (e.g., "Proxmox VE Server").


     ![image](https://github.com/user-attachments/assets/c5695371-82eb-48e0-880f-65562f45b94f)

   - **Choose a location** to store the VM files or accept the default location.

3. ### Specify Generation
   - Select **Generation 1** (recommended for compatibility) and click **Next**.


     ![image](https://github.com/user-attachments/assets/dba8ad31-26e7-4703-a0bc-49c5bf5952e4)


4. ### Assign Memory
   - Allocate **at least 4096 MB (4 GB)** of memory for a smooth setup.
   - Enable **Dynamic Memory** if you want Hyper-V to adjust the memory usage dynamically.


     ![image](https://github.com/user-attachments/assets/bef988e2-b5c3-4893-94fd-2a3c8a6b448a)


5. ### Configure Networking
   - Choose an existing **virtual switch** for network connectivity or create a new one.
   - This network will allow Proxmox VE to access the internet or other local resources.
  
     
     ![image](https://github.com/user-attachments/assets/cf1ceb99-cf42-4a07-9c20-0c5bee93fe89)


6. ### Connect the Virtual Hard Disk
   - Create a **virtual hard disk** with at least **32 GB** of storage for Proxmox VE.

   
     ![image](https://github.com/user-attachments/assets/ba260e9d-b38c-4688-ae90-500021329b04)


8. ### Install Options
   - Select **Install an operating system from a bootable image file**.
   - Browse to the **Proxmox VE ISO file** you downloaded, and click **Next**.

  
     ![image](https://github.com/user-attachments/assets/d31c0d5d-d681-4865-bb37-5b8bbdb304f3)


9. ### Finish the Setup
   - Review the settings and click **Finish**.

   
![image](https://github.com/user-attachments/assets/3aed8bd2-15d2-4541-b4bd-12d08975be55)

---

## Step 2: Configure Virtual Machine Settings

1. **Processor Configuration**:
   - In Hyper-V Manager, right-click the VM and select **Settings**.
   - Go to **Processor** and allocate at least **2 virtual processors**.


![image](https://github.com/user-attachments/assets/8c5c7a01-6c6b-47dc-83ee-49dfc4d9f75d)


2. **Network Adapter Settings**:
   - If necessary, adjust the network adapter settings for optimal performance.

3. **Configure the Boot Order**:
   - Go to **Firmware** and ensure the CD/DVD (ISO) drive is first in the boot order to boot from the Proxmox ISO.

---

## Step 3: Start the Proxmox Installation

1. **Power On the VM**:
   - Start the VM by right-clicking it and selecting **Connect**, then **Start**.

2. **Begin the Installation**:
   - You should see the Proxmox installer boot up. Select **Install Proxmox VE (Graphical)** and press **Enter**.


     ![image](https://github.com/user-attachments/assets/44f2cd46-e2e8-411b-a5c5-6fdec84286e0)

     

3.**Nested Virtualization**

If Proxmox VE requires hardware virtualization support (Intel VT-x or AMD-V), which isn’t currently enabled or detected.

![image](https://github.com/user-attachments/assets/491df2e0-f634-43b1-87ee-3aaa26d20d03)

 Here’s how to resolve it: 
 
 - Shutdown the VM
 - Open PowerShell as Administrator.
 - Run the following command, replacing "Proxmox VE Server" with the name of your VM:
   
 ```
Set-VMProcessor -VMName "Proxmox VE" -ExposeVirtualizationExtensions $true

 ```

![image](https://github.com/user-attachments/assets/4a6639b8-eda7-413a-8b23-459cb1a0f13f)

This command enables nested virtualization, allowing Proxmox to detect virtualization capabilities.
   

4. **Follow Installation Prompts**:
   - Accept the license agreement.
   - Select the target hard disk (usually the one you created in Hyper-V).
   - Configure the **country, time zone, and keyboard layout**.
   - Set a strong password and provide an email address for recovery or notifications.
   - Set up network configuration:
      - Choose a hostname and configure the network adapter.

5. **Complete the Installation**:
   - Proxmox will now install on the virtual disk. Wait for the installation to complete.
   - Once complete, you’ll be prompted to reboot the VM.

---

## Step 4: Initial Configuration and Access Proxmox Web Interface

1. **Reboot the VM**:
   - After installation, remove the ISO from the VM by going to **Settings > DVD Drive** and choosing **None**.
   - Reboot the VM to boot into Proxmox VE.

 ![image](https://github.com/user-attachments/assets/70d685be-26a4-415a-8088-9b2688952597)

2. **Access Proxmox Web Interface**:
   - Open a browser on the host machine and go to `https://[Proxmox-VM-IP]:8006`.

 
  ![image](https://github.com/user-attachments/assets/f0578e4b-ffe5-488c-b525-8d13cab56dd3)

   - Log in using `root` and the password you set during installation.

2. **Verify Configuration**:
   - Once logged in, you can begin configuring Proxmox, creating virtual machines, or exploring its features.

---


Continue to follow the setup instructions in your Proxmox VE console after starting the VM. For more detailed configuration and usage instructions, refer to the official [Proxmox VE documentation](https://pve.proxmox.com/wiki/Main_Page).

Happy virtualizing!
