---
name: 1.4 Practical
---

[toc]

## Module 1 Practical Introduction
#### Getting Started with AWS

In this activity you will log in to Amazon Web Services using a QUT student account, create a Linux virtual machine in the cloud, use a secure shell client to connect to the virtual machine, and implement a "Hello World" web application. Finally - and _importantly_ - you will terminate the virtual machine.

Note that there are a number of ways you can connect to the VM - it is not necessary for you to use all of them today. Please talk to your tutor if you run into difficulties or you are unsure of what to do. 



#### Prerequisites and References

- Complete **Week 0: Accessing the Cloud** module (starting with <pagelink>0.1 Overview</pagelink>) and be familiar with accessing AWS.
- AWS: [What is an EC2 (VM)](https://aws.amazon.com/ec2/ )
- AWS: [Guide to Build an EC2](https://aws.amazon.com/getting-started/launch-a-virtual-machine-B-0/)
- QUT AWS SSO link: [https://d-97671c4bd0.awsapps.com/start#/](https://d-97671c4bd0.awsapps.com/start#/)


----------------------------------------------------- 

## Exercise 1

#### Step 1: Log in to the QUT AWS cloud.
A dedicated AWS workspace has been created to allow you to access cloud resources  using your QUT credentials. This workspace is to be used strictly for academic purposes. Please check <pagelink>0.2 Logging on to QUT AWS Cloud</pagelink> for more information on how to access.


#### Step 2: Create a Linux virtual machine in the QUT AWS cloud
After completing this step you will have a machine running, ready for remote connection and management. We will use Ubuntu 22.04 for this year. You may use later/Older versions if you wish and if you have some Linux expertise. 

Background: You will use an Amazon t2 micro instance running Ubuntu 22.04 to complete the rest of this activity. Always use the smallest instance that allows you to complete the task. Higher spec machines cost more and you won't often need their capabilities.

Please check <pagelink>0.3 Creating an EC2 Instance</pagelink> for more information on how to create an EC2 instance.


#### Step 3: Connect to your VM with the web-based Session Manager

After completing this step, you can work on your VM in a browser tab.

**Background**: The AWS web-based Session Manager provides convenient interactive access to the VM command line environment.

1. Start your virtual machine and navigate to the AWS Instances page.
2. Select your running instance and click “Connect”.
![Finding EC2 Instance](img_1_4_1_finding_ec2.png "Finding EC2 Instance")

3. Go to the “Session manager” tab, and click “Connect”
![Connect to AWS using Session Manager](img_1_4_2_session_manager.png "Connect to AWS using Session Manager")

4. Successful log in will lead to a Linux bash session on the VM, hosted in your browser. Use the command cd ~to go to your home directory to start work.

![Connected to Session Manager](img_1_4_3_ssh_session.png "Connected to Session Manager")
At this point you may proceed to Step 6 (hosting a simple HTTP server) should you wish. The intermediary steps explore alternative ways of connecting to the VM.

#### Step 4: Get yourself set up with a secure shell (SSH) client

This step describes the pre-requisites needed to connect to your VM via SSH using a command shell or GUI client. Once you have completed these instructions, Step 5 tells you how to put this into practice to actually connect to the machine. 

These steps provide an important alternative to the approach in Step 3 above. 

**Background**: Secure shell (SSH) is the primary management tool for Linux virtual machines. File transfer can be achieved using SFTP or SCP.

Secure shell (SSH) is the primary management tool for Linux virtual machines. File transfer can be achieved using SFTP or SCP.

- MacOS, Linux (including WSL2):
  - You may find that a SSH client is installed already. To verify that you have the tool, open a terminal window,and enter the command: `which ssh`
  - If ssh is present the response will be something along the lines of:`/usr/bin/ssh`
  - If the command is not found, you can use your system’s package manager to install an OpenSSH client. In Ubuntu the installation command is: `sudo apt install openssh-client`
- Windows
  - Plenty of choices are available, but we have provided software and detailed instructions for some simple and practical options.
    - Modern Windows versions provide the Windows Subsystem for Linux (WSL2). This is a good choice if you would like a reasonably full Linux experience.
    - Git is a source code control system which originated in Linux. The Windows port includes a powerful subset of the Minimal GNU for Windows (MINGW) Unix-like environment.
      - The MINGW ssh and scp clients understand your VM’s.pemfile without further processing.
      - The MINGW terminal providesbash, a good script host which will be handy in later learning activities.
    - Putty is a dedicated terminal emulation program for Windows which includes separate SFTP and SCP clients. Putty does not understand.pemfiles, so you’ll have to use theputtygenprogram to convert your.pemfile to a.ppkfile for use with Putty.
  



#### Step 5 (Prereq): Use a secure shell (SSH) client (Putty) to connect to the running VM

Using the VM’s private access key with your SSH client allows you to log on to the VM, install software, and execute programs.

1. Start a VM via the AWS management console, and make sure you have access to the .pemprivate keyfile.
2. To be concrete, in this walk through we use a key file which has been saved locally as `Q:\CAB432\2021_02\AWS_Keys\LawrenceCAB432_key2.pem`
3. Go the EC2 instances page and copy the public IP of your instance. In this walkthrough, the public IP address is `13.211.103.201`
![Getting Public IP](img_1_4_4_public_ip.png "Getting Public IP")


#### Step 5a: Use a secure shell (SSH) client (Putty) to connect to the running VM

1. Ensure you have putty installed.
2. Run puttygento convert the OpenSSH key file to a Putty key file
3. Import your.pemprivate key file

![Import Putty](img_1_4_5_import_putty.png "Import Putty")

4. Save the private key file. In this example, we saved as `Q:\CAB432\2021_02\AWS_Keys\LawrenceCAB432_key2.ppk`
![PuttyGen](img_1_4_6_putygen.png "PuttyGen")

5. Run putty, and on the session tab, insert public IP address of VM

![Public IP input putty](img_1_4_7_putty_ip.png "Public IP input putty")

6. On the connections tab, open the private key (.ppk) file.

![Adding Key](img_1_4_8_putty_auth.png "Adding Key")

7. You are now set. Open the connection, accept the prompts if any.
8. Login as the user `ubuntu` when prompted. This will open a linux bash session on the VM.

#### Step 5b: Use a secure shell (SSH) client (Bash) to connect to the running VM

1. Make sure you have a suitable command line environment set up, e.g., Linux, MacOS, or something like MINGW
2. Open a terminal window with access to ssh
3. Use the saved private key file and IP address to connect to the VM. For example: `ssh -i /Q/CAB432/2021_02/AWS_Keys/LawrenceCAB432_key2.pem -l ubuntu 13.211.103.201`
4. Replace the file name and IP address with values corresponding to your situation. When prompted to save the key, enter yes. Successful log in will lead to a Linux bash session on the VM



#### Step 6: Host a simple web application on the VM

After completing this step, you will be able to access a basic web site hosted on the VM. Installing Python lets you host a simple HTTP web site.

To undertake this step, you must have connected to the VM using one of the methods described above.


1. Install Python:`sudo apt-get install python`
2. Make a new directory for the website and change into it: `mkdir server && cd server`
3. Create a small HTML document. If you know a Linux editor already you can create the file and include the html given below. If not, this shell echo statement will create a file for you:
 
~~~~
echo >hello.html '<html><body><h1>HelloCAB432!!!</h1></body></html>'
~~~~
5. Host the web site: `python -m http.server 3000`
6. Stay logged on to the VM and open a new browser tab. 
7. Navigate to your document on the VM. In the concrete example used for this walk-through, the address is `http://13.211.103.201:3000/hello.html`. Replace with the IP address of your own VM.

**A note on security:** The Python HTTP Server is a great tool for testing, local development and quick learning exercises like this one. However, it's not designed with security in mind and lacks the robustness required for a production environment. In future weeks we will explore web servers that are specifically designed to host production-level applications.

#### Step 7: Terminate the instance
Even stopped instances continue to incur AWS charges, so when you complete the exercise, terminate the instance.

1. Use the Terminate option on the Instance state menu to delete the VM.

----------------------------------------------------- 

## Exercise 2: Preparing Linux Environment

**If you are using a Linux machine, you can skip this step.**


In some earlier versions of this unit we supported Docker under both Linux and Windows.
- Docker Windows 7 does not play nicely. Use the cloud machines or the Virtual Box approach outlined below or update to Windows 10 or Windows 11.  WSL or Windows 10+ are just fine in my experience. 
- Docker for Windows 10/11 is much better and it is known also to work well in the Windows Subsystem for Linux – though there are configuration issues which mean this isn’t the case for QUT lab machines. 


**Setting up WSL**

We will be using the following instructions to set up WSL on Windows 11.

- [https://learn.microsoft.com/en-gb/windows/wsl/install](https://learn.microsoft.com/en-gb/windows/wsl/install)
- [https://code.visualstudio.com/docs/remote/wsl](https://code.visualstudio.com/docs/remote/wsl)

1. Ensure Windows Subsystem for Linux is enabled. Go to Settings > Apps > Optional Features > More Windows Features and ensure Windows Subsystem for Linux is enabled.

![WSL Setting](img_2_4_1_wsl_setting.png "WSL Setting")

2. Open PowerShell in Admin mode. Run the following command to install WSL 2.

~~~~
wsl --install -d ubuntu-22.04
~~~~

If this dosen't work, you can check the following:
- Ensure that the setting is turned on in Exercise 1. You might need to restart the computer.
- Ensure Admin mode is set for your PowerShell instance
- Check if an existing wsl is running. If so, you can run the following command to terminate it. `wsl --shutdown`
- Check if your Windows Store can download things properly - the WSL installation is done through the Windows Store. If you can't download anything from the Windows Store, you might need to check your network settings.
  - If your Windows Store cannot install WSL, try `SFC /scannow` in PowerShell to check for any system file corruption. You might need to restart the computer after this.
  - Try reset windwos store via `wsreset` in PowerShell.
  - You can also try reinstalling the Windows Store app. You can do this by running the following command in PowerShell. `Get-AppXPackage -allusers | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}`


3. On VSCode, Install the WSL extension. You can do this by going to the Extensions tab on the left side of the screen and searching for "WSL". Click install.

![WSL](img_2_4_2_wsl_extension.png "WSL")

4. Open Ubuntu via Start Menu - we are going to configure our username/password. A new terminal should open. After installing, it should prompt a username and passcode.

![Opening WSL Terminal](img_2_4_3_wsl_open.png "Opening WSL Terminal")
![Config Username First time](img_2_4_4_wsl_config.png "Config Username First time")

5. Once you are in WSL, you can install VSCode. You can do this by running the following command in the terminal `code .`. This will install/open the current dir in VScode. You might want to trust the current workspace. On the bottom left hand side, you can see that the vscode terminal is connected to the WSL environment. 


![Install and Open VScode](img_2_4_5_wsl_vscode.png "Install and Open VScode")

**Virtual Box Approach**

Oracle’s Virtual Box is a very widely used VM manager for Windows. It is very convenient and really doesn’t take too much time to set up and use productively. The downloads are found at: [https://www.virtualbox.org/](https://www.virtualbox.org/) 

When you look at the page, as shown above, you will also see a link to pre-built images. These are for Oracle’s versions of Linux, so for consistency with our cloud images, do not click on this link. Instead, follow the download and installation instructions that you find in this blog below: [http://www.beopensource.com/2018/02/Install-Ubuntu-18.04-Virtual-Box.html](http://www.beopensource.com/2018/02/Install-Ubuntu-18.04-Virtual-Box.html)
 
We have not updated this material for some time as we now recommend the WSL approach if you are working under Windows. Please let us know if there are any issues and we can probably help you out. 

-----------------------------------------------------

#### What questions remain?

If you have questions about this practical, please post them on the <discussion>Practical 1 questions</discussion> discussion board.