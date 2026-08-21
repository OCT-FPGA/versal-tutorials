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

`docker pull xilinx/vitis-ai-pytorch-cpu:latest`

`./docker_run.sh xilinx/vitis-ai-pytorch-cpu:latest`

`source /workspace/board_setup/vck5000/setup.sh DPUCVDX8H_8pe_normal`

`vitis-ai-user@pc178:/workspace$ source /workspace/board_setup/vck5000/setup.sh DPUCVDX8H_8pe_normal
------------------
VAI_HOME = /vitis_ai_home
------------------
Autocomplete not enabled for XRT tools
XILINX_XRT        : /opt/xilinx/xrt
PATH              : /opt/xilinx/xrt/bin:/opt/vitis_ai/conda/envs/vitis-ai-wego-torch/bin:/opt/vitis_ai/conda/bin:/opt/vitis_ai/conda/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
LD_LIBRARY_PATH   : /opt/xilinx/xrt/lib:/opt/xilinx/xrt/lib:/usr/lib:/usr/lib/x86_64-linux-gnu
PYTHONPATH        : /opt/xilinx/xrt/python
---------------------
XILINX_XRT = /opt/xilinx/xrt
---------------------
XILINX_XRM      : /opt/xilinx/xrm
PATH            : /opt/xilinx/xrm/bin:/opt/xilinx/xrt/bin:/opt/vitis_ai/conda/envs/vitis-ai-wego-torch/bin:/opt/vitis_ai/conda/bin:/opt/vitis_ai/conda/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
LD_LIBRARY_PATH : /opt/xilinx/xrm/lib:/opt/xilinx/xrt/lib:/opt/xilinx/xrt/lib:/usr/lib:/usr/lib/x86_64-linux-gnu
---------------------
XILINX_XRM = /opt/xilinx/xrm
---------------------
---------------------
LD_LIBRARY_PATH = /opt/xilinx/xrm/lib:/opt/xilinx/xrt/lib:/opt/xilinx/xrt/lib:/usr/lib:/usr/lib/x86_64-linux-gnu
---------------------
[0000:0d:00.1]  :  xilinx_vck5000_gen4x8_qdma_base_2  05DCA096-76CB-730B-8D19-EC1192FBAE3F  user(inst=129)  Yes            
vck5000_ card detected
---------------------
XCLBIN_PATH = /opt/xilinx/overlaybins/DPUCVDX8H/8PE
XLNX_VART_FIRMWARE = /opt/xilinx/overlaybins/DPUCVDX8H/8PE/dpu_DPUCVDX8H_8PE_350M_xilinx_vck5000_gen4x8_qdma_base_2.xclbin`
