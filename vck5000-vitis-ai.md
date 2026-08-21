# Getting Started with Vitis AI on VCK5000s in OCT

This tutorial provides step-by-step instructions for allocating a VCK5000 node and running a simple Vitis AI application on the Open Cloud Testbed (OCT).    

## Prerequisites

If you haven’t joined the OCTFPGA project yet, you can get started by following [this](https://github.com/OCT-FPGA/OCT-Tutorials/tree/master/cloudlab-setup) tutorial.

## Experiment setup
After logging into the CloudLab account, select Experiments -> Start Experiment, and click `Change Profile`.

![plot](images/vitis-ai-change-profile.png)

Type `oct-vck5000` in the profile search box.
 
Select the profile `oct-vck5000`.

![plot](images/vitis-ai-vck5000.png)

Click Next.

![plot](images/vitis-ai-profile-selected.png)

Specify the node(s) with VCK5000s under "List of nodes". For this experiment, one node will be used. Node availability can be checked at the cluster status page: https://cloudlab.us/cluster-status.php. Scroll to the bottom of the cluster status page to see the "Mass Nodes" table. The nodes pc176 through pc179 are designated for VCK5000s. Any available node from this set can be selected and its ID should be entered (for example, pc179).

You will use the Vitis-AI flow in this tutorial. Make sure that you select the Vitis-AI workflow. 

![plot](images/vitis-ai-parameterize.png)

Select the project `OCTFPGA` and click Next.

![plot](images/vitis-ai-finalize.png)

![plot](images/vitis-ai-finalize-2.png)

Set the experiment duration and click `Finish` to start the experiment. 

![plot](images/vitis-ai-finish.png)

You will notice that a node is being allocated and starting up.

![plot](images/vitis-ai-provisioning.png)

![plot](images/vitis-ai-booting.png)

After the node has finished booting up, a startup service will run that installs runtime tools which are required to run the example in this tutorial. The gree node icon shows that statup services are still running.

![plot](images/vitis-ai-booted.png)

The startup status indicator will change to a check mark once the startup service has completed. **IMPORTANT: Do not log into the node until the startup service has finished running, as the tools required for this tutorial may not yet be installed.**

![plot](images/vitis-ai-ready.png)

Once the node has finished running the startup script, you can click on the node and open the shell or if you prefer, you can use external tools such as PuTTY to ssh into the node.

![plot](images/vitis-ai-ssh.png)

![plot](images/vitis-ai-shell.png)

## Examples

The original quick start tutorial can be found [here](https://xilinx.github.io/Vitis-AI/3.0/html/docs/quickstart/vck5000.html). 

`cd /docker/Vitis-AI`
