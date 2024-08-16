# Getting started with Alveo V70s in OCT

In this tutorial, we will guide you through the process of allocating a node with an AMD Alveo V70 in OCT and walk through the steps of running an example using a Vitis AI Docker container.

## Prerequisites

If you haven’t joined the OCTFPGA project yet, you can get started by following [this](https://github.com/OCT-FPGA/OCT-Tutorials/tree/master/cloudlab-setup) tutorial.

## Experiment setup
After logging into the CloudLab account, select Experiments -> Start Experiment, and click `Change Profile`.

![plot](images/v70-change-profile.png)

Type `oct-v70` in the profile search box.
 
Select the profile `oct-v70`.

![plot](images/v70-select-prof.png)

Click Next.

![plot](images/v70-select-prof2.png)

In this tutorial, you will use the Ubuntu 20.04 image with the PyTorch Docker image. Leave the default selection as is, and click Next.

![plot](images/v70-customize-prof.png)

Select the project `OCTFPGA` and click Next.

![plot](images/v70-select-proj.png)

Then click `Finish` to start the experiment. 

Note: If you see a warning that not enough resources are available to start the experiment, you can safely ignore it.

![plot](images/v70-schedule-exp.png)

You will notice that a node is being allocated and starting up.

![plot](images/v70-allocate-exp.png)

![plot](images/v70-node-boot.png)

After the node has finished booting up, a startup service will run that installs necessary tools like Docker and a VNC server, which are required to run the example in this tutorial. The green node icon will display a check mark once the startup service has completed. **IMPORTANT: Do not log into the node until the startup service has finished running, as the tools required for this tutorial may not yet be installed.**

![plot](images/v70-node-ready.png)

![plot](images/v70-node-ready2.png)

Once the node has finished running the startup script, you can log into the node using SSH: `ssh -i <private key> <user name>@<cloudlab IP>`

![plot](images/v70-node-login.png)


## Launch VNC

Launch the VNC server on the node you allocated for the experiment: `vncserver -localhost no -geometry 1920x1080`

![plot](images/v70-start-vnc.png)

You can use any VNC client to access the graphical desktop of the node you just allocated. In this example, we'll use RealVNC, which can be downloaded [here](https://www.realvnc.com/en/connect/download/viewer/). Configure the VNC client settings on your machine as shown, and connect to the VNC server.

After opening the VNC client, select File, then click New Connection. Enter the VNC server address as `<cloudlab IP>:<VNC port>`.

![plot](images/v70-vnc-client1.png)

Click OK.

![plot](images/v70-vnc-client2.png)

![plot](images/v70-vnc-client3.png)

## Start Docker 

After logging into the graphical desktop of the V70 node, go to the Vitis-AI directory and start the Docker container.

![plot](images/v70-docker-start.png)

![plot](images/v70-docker-start2.png)

![plot](images/v70-docker-ready.png)

Once you’re inside the Docker container, you can proceed with the V70 example provided [here](https://xilinx.github.io/Vitis-AI/3.5/html/docs/quickstart/v70.html). 
Since the initial steps for setting up the Docker container are already completed, you can go straight to [here](https://xilinx.github.io/Vitis-AI/3.5/html/docs/quickstart/v70.html#docker-container-environment-variable-setup) and continue.




