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

4. ### Assign Memory
   - Allocate **at least 4096 MB (4 GB)** of memory for a smooth setup.
   - Enable **Dynamic Memory** if you want Hyper-V to adjust the memory usage dynamically.

5. ### Configure Networking
   - Choose an existing **virtual switch** for network connectivity or create a new one.
   - This network will allow Proxmox VE to access the internet or other local resources.

6. ### Connect the Virtual Hard Disk
   - Create a **virtual hard disk** with at least **32 GB** of storage for Proxmox VE.

7. ### Install Options
   - Select **Install an operating system from a bootable image file**.
   - Browse to the **Proxmox VE ISO file** you downloaded, and click **Next**.

8. ### Finish the Setup
   - Review the settings and click **Finish**.

---

Continue to follow the setup instructions in your Proxmox VE console after starting the VM. For more detailed configuration and usage instructions, refer to the official [Proxmox VE documentation](https://pve.proxmox.com/wiki/Main_Page).

Happy virtualizing!
