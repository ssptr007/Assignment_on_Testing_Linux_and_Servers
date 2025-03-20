![image](https://github.com/user-attachments/assets/ae6af9e9-c608-4cc8-aa8c-d4fc2f79ab9f)

**Task 1: System Monitoring Setup****

**nmon (Nigel’s Monitor)** is a performance monitoring tool for Linux and AIX systems. It provides real-time CPU, memory, disk, network, and other system performance metrics in a simple terminal interface.

  **Installation of nmon**
  
    #sudo apt update && sudo apt upgrade -y
![image](https://github.com/user-attachments/assets/21030fad-ca46-425d-affc-6d8803bb6284)

    #sudo apt install -y nmon
 ![image](https://github.com/user-attachments/assets/3613861e-7ad8-4bb0-8616-54a121d0532f)

    #nmon
 ![image](https://github.com/user-attachments/assets/c6667067-6ae7-4b57-b24e-6ba87df12964)

The above command will give several option to get system resource utilization. All the options are listed below

c - CPU information

 ![image](https://github.com/user-attachments/assets/41a35fee-213a-489a-aa5a-4e93f9afa3b7)
    
C - CPU information in detail

 ![image](https://github.com/user-attachments/assets/e0b92aee-bd23-4815-bc8b-ceb746efa120)
    
m - Memory information

![image](https://github.com/user-attachments/assets/3b514dc2-deab-463b-9be8-6b90f9bc6632)

d - Disk I/O 

![image](https://github.com/user-attachments/assets/5671f86a-6580-4629-8e09-bcccd5e73fb9)

r - Resources Linux & Processor 

![image](https://github.com/user-attachments/assets/9bb15607-58f4-4107-be89-2d4fb4917d75)

k - Kernel and Load Average

![image](https://github.com/user-attachments/assets/6fbe7e6a-b561-437b-a565-862b104a022c)

U - CPU Utilisation Stats 

![image](https://github.com/user-attachments/assets/0d3a3655-58b3-4155-a6d3-4222b6611146)

V - Virtual memory

![image](https://github.com/user-attachments/assets/da94f210-cc4c-4901-8f0e-6baf3401e6ec)

n - Network I/O

![image](https://github.com/user-attachments/assets/a566825b-6724-46b0-9382-160674862d58)

t - Top-processes

![image](https://github.com/user-attachments/assets/3d2725be-6ea4-40f2-9883-39f78d00f4ca)

    #nmon -f -s 10 -c 30
      
It will create a .nmon file. The file name will be having hostname of the machine, followed by today's date and current time. For eg hostname_YYYYMMDD_HHMM.nmon
 
 -f --> Creating the nmon extention file
 
 -s --> Sample data every 10 seconds
 
 -c --> Collects the 30 samples

 To analyze .nmon files we are using nmonchart.

 **nmonchart Installation**

    #wget https://raw.githubusercontent.com/aguther/nmonchart/master/nmonchart

    #chmod +x nmonchar

    #sudo apt-get install mksh

    #./nmonchart your_nmon_file.nmon output_report.html

After getting the html file. Open that in web browser. We will get the graphical represention of system vitals utilization.

![image](https://github.com/user-attachments/assets/f804c9e2-2882-4879-9be7-0e0039ce248b)

**df(disk free) command** --> df(Disk Free) command used to get the information about disk utilization.

![image](https://github.com/user-attachments/assets/a1fbc427-6ef1-4e51-aa13-2cf9a3dc31d1)

    #df -h
This command is used to get the disk utilization information in human readable format.

![image](https://github.com/user-attachments/assets/f4d8ef39-0136-4f55-bcf1-f58842ebd887)

    #df -h /
  -h - Is used to get the output in human readable format.
  
 This command is used to get the disk utilization information root root filesystem.

![image](https://github.com/user-attachments/assets/48958a24-92ac-4e5a-b27f-6d630c303fa7)

**du(Disk Use) command** --> du(Disk Use) command is used to get usage of disk from perticular file or folder.

![image](https://github.com/user-attachments/assets/86000541-eb8d-4c82-a223-954a06bd7df0)

eg:

    #du -sh filename

![image](https://github.com/user-attachments/assets/87dcf2f8-55e1-4577-9a14-e7dfe0c49822)

**<font size="20">Task 2: User Management and Access Control</font>**
 
 **Configuaring the complex password to the user**

Edit the file /etc/pam.d/system-auth. We need to the change line number 20 as like given below

password    requisite                                    pam_pwquality.so retry=3 minlen=12 dcredit=-1 ucredit=-1 lcredit=-1 ocredit=-1 enforce_for_root

![image](https://github.com/user-attachments/assets/1a276026-47d5-481e-ad5d-5fdc4ca611b5)

After the we need to restart the sshd
    #systemctl restart sshd

We have tried to change password with weak password. We got the error. After we have given strong password it accepted. Please find the screenshot below.

![image](https://github.com/user-attachments/assets/0dc53d28-f557-4c04-8cdd-f4547dff595f)











 













    


    


