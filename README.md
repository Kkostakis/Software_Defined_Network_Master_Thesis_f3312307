# **Analysis & Security of Software-Defined Networks -- Master's Thesis for the Athens University of Economics and Business**
## **Master's Thesis For Software-Defined Networking** 

![ΑΣΟΕ Logo](https://www.aueb.gr/press/logos/1_AUEB-pantone-HR.jpg)

### **Use-Cases – SDN Open-Source Tools’ Table**

| Open-Source Tools	| Use-Case/Description - Usage |
| --- | --- |
| Mininet SDN Framework	| It will be the platform that will provide a virtual testing environment for our Software-Defined Network - Use-Case: C.4 |
| SDN Controller FloodLight |	Java-Based OpenFlow Controller for SDN which will be utilized as one of the primary tools for Distributed Denial-of-Service Attack in our virtual SDN environment - Use-Case: C.4 |
| Open Virtual Switch (OVS) |	This is a multi-layer virtual switch supporting Apache 2.0 and it will be utilized to produce and manage our virtual switching devices - Use-Case: C.4 |
| SFlow-RT | Real-Time analysis open-source tool, utilized for network traffic monitoring and metric, specifically for Software-Defined Network environment and it will be utilized to monitor the state of the controller - Use-Case: C.4 |


## **Installation Guide – Open-Source Tools (In Ubuntu/Kali Linux)**
The use-case C.4 will be demonstrated in the Operating System Ubuntu (22.04 LTS), however it can be applied to the Kali Linux environment as well. The use-case is executed in Virtual Environment hosted by the VirtualBox (more specifically by the physical host machine, due to the hypervisor). For further details regarding the installation of the VirtualBox are found in the link description https://www.virtualbox.org/ as well as for the VMs Ubuntu and Kali Linux from the following links: https://medium.com/@maheshdeshmukh22/how-to-install-ubuntu-22-04-lts-on-virtualbox-in-windows-11-6c259ce8ef60, https://www.kali.org/get-kali/#kali-platforms. 

The installation process is the same for either of the two OS, as follows:

* Mininet SDN Framework: Open a terminal instance after VirtualBox and a Kali Linux/Ubuntu virtual machine have been setup and afterwards execute the commands sudo apt-get update -y and sudo apt-get install mininet -y.
 

* SDN Controller FloodLight: In the terminal’s command line, it is vital to install ant via the command sudo apt install build-essential ant python2-dev openjdk-8-jdk maven git and afterwards clone the FloodLight repository from github, sudo git clone https://github.com/floodlight/floodlight.




Then, head to the website of maven repository https://mvnrepository.com and install the jar files for the libraries libthrift ver 0.14.1 and netty-all ver 4.1.66.Final. Head to the terminal, and from there to the ~/floodlight/lib directory and there remove the jar files libthrift-0.9.0.jar, netty-all-4.0.31.final (it is not necessary for them to be in the aforementioned versions). 


Build the file using gedit build.xml to ensure that the jar files have been removed and copy the downloaded jar files ro rhe directory ~/floodlight/lib via the commands sudo cp libthrift-0.14.1.jar ~/floodlight/lib, sudo cp netty-all-4.1.66.Final.jar ~/floodlight/lib/. Inside the floodlight directory (cd ..) check whether there are any issues with the jar versions and initialize, update the modules with the commands sudo git submodule init, sudo git submodule update. Furthermore, it is essential to ensure to execute git pull in order to fetch the latest updates from the master branch of the remote repository origin (floodlight) and merge them to our current branch. Clear the lingering files in the target sub-directory with sudo ant clean then compile the source Java code, and link the existing libraries according to the directives of the build.xml file via the command sudo ant. Finally, launch the floodlight SDN controller after everything have been setup correctly with the command sudo java -jar target/floodlight.jar.

* Open Virtual Switch (OVS): Open a new terminal instance and execute the commands sudo apt-get update -y and then sudo apt-get install openvswitch-switch -y.

* SFlow-RT: In the terminal execute wget in order to acquire the software package from inmon, wget https://inmon.com/products/sFlow-RT/sflow-rt.tar.gz, extract the file into a directory via sudo tar -xvzf sflow-rt.tar.gz. Afterwards, redirect to the website https://sflow-rt.com/download.php, which entails further instructions regarding application packages for SFlow-RT. With the command ./sflow-rt/get-app.sh sflow-rt [application_name], applications such as browse-metrics, ddos-protect can be installed in the current tool and after a restart ./sflow-rt/start.sh the applications will be working properly.

* Additional Files – Use-Case: It is noteworthy to mention that all the results of the captured packets via Wireshark found in the third section of the thesis are found in the file Wireshark_Findings_Use_Case_#1.zip.


