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

```bash
vitis-ai-user@pc178:/workspace$ source /workspace/board_setup/vck5000/setup.sh DPUCVDX8H_8pe_normal
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
XLNX_VART_FIRMWARE = /opt/xilinx/overlaybins/DPUCVDX8H/8PE/dpu_DPUCVDX8H_8PE_350M_xilinx_vck5000_gen4x8_qdma_base_2.xclbin
```

```bash
vitis-ai-user@pc178:/workspace$ wget https://www.xilinx.com/bin/public/openDownload?filename=resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz -O resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz
--2026-08-21 07:30:06--  https://www.xilinx.com/bin/public/openDownload?filename=resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz
Resolving www.xilinx.com (www.xilinx.com)... 23.49.250.188, 23.49.250.194
Connecting to www.xilinx.com (www.xilinx.com)|23.49.250.188|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://download.amd.com/opendownload/xlnx/resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz [following]
--2026-08-21 07:30:06--  https://download.amd.com/opendownload/xlnx/resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz
Resolving download.amd.com (download.amd.com)... 23.33.202.129
Connecting to download.amd.com (download.amd.com)|23.33.202.129|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 18343265 (17M) [application/x-gzip]
Saving to: ‘resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz’

resnet50-vck5000-DPUCVD 100%[===============================>]  17.49M  63.0MB/s    in 0.3s    

2026-08-21 07:30:06 (63.0 MB/s) - ‘resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz’ saved [18343265/18343265]
```

```bash
vitis-ai-user@pc178:/workspace$ tar -xzvf resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz
resnet50/
resnet50/meta.json
resnet50/resnet50.xmodel
resnet50/md5sum.txt
resnet50/resnet50.prototxt
```

`sudo mkdir -p /usr/share/vitis_ai_library/models`

`sudo cp resnet50 /usr/share/vitis_ai_library/models -r`

```bash
vitis-ai-user@pc178:/workspace$ wget -O vitis_ai_runtime_r3.0.0_image_video.tar.gz "https://www.xilinx.com/bin/public/openDownload?filename=vitis_ai_runtime_r3.0.0_image_video.tar.gz"
--2026-08-21 07:31:26--  https://www.xilinx.com/bin/public/openDownload?filename=vitis_ai_runtime_r3.0.0_image_video.tar.gz
Resolving www.xilinx.com (www.xilinx.com)... 23.49.250.188, 23.49.250.153, 23.49.250.160, ...
Connecting to www.xilinx.com (www.xilinx.com)|23.49.250.188|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://download.amd.com/opendownload/xlnx/vitis_ai_runtime_r3.0.0_image_video.tar.gz [following]
--2026-08-21 07:31:26--  https://download.amd.com/opendownload/xlnx/vitis_ai_runtime_r3.0.0_image_video.tar.gz
Resolving download.amd.com (download.amd.com)... 23.33.202.129
Connecting to download.amd.com (download.amd.com)|23.33.202.129|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 47058467 (45M) [application/x-gzip]
Saving to: ‘vitis_ai_runtime_r3.0.0_image_video.tar.gz’

vitis_ai_runtime_r3.0.0 100%[===============================>]  44.88M  80.3MB/s    in 0.6s    

2026-08-21 07:31:27 (80.3 MB/s) - ‘vitis_ai_runtime_r3.0.0_image_video.tar.gz’ saved [47058467/47058467]
```

```bash
vitis-ai-user@pc178:/workspace$ tar -xzvf vitis_ai_runtime_r3.0.0_image_video.tar.gz -C examples/vai_runtime
./adas_detection/
./adas_detection/video/
./adas_detection/video/adas.avi
./adas_detection/video/adas.webm
./images/
./images/001.jpg
./pose_detection/
./pose_detection/video/
./pose_detection/video/pose.webm
./pose_detection/video/pose.mp4
./segmentation/
./segmentation/video/
./segmentation/video/traffic.mp4
./segmentation/video/traffic.webm
./video_analysis/
./video_analysis/video/
./video_analysis/video/structure.webm
./video_analysis/video/structure.mp4
```

`vitis-ai-user@pc178:/workspace$ cd examples/vai_runtime/resnet50`

```bash
vitis-ai-user@pc178:/workspace/examples/vai_runtime/resnet50$ bash build.sh 
No LSB modules are available.
No LSB modules are available.
g++ (Ubuntu 10.3.0-1ubuntu1~20.04) 10.3.0
Copyright (C) 2020 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

opencv4                    OpenCV - Open Source Computer Vision Library
```

```bash
vitis-ai-user@pc178:/workspace/examples/vai_runtime/resnet50$ ./resnet50 /usr/share/vitis_ai_library/models/resnet50/resnet50.xmodel
WARNING: Logging before InitGoogleLogging() is written to STDERR
I0821 07:32:30.251623   196 main.cc:292] create running for subgraph: subgraph_conv1

Image : 001.jpg
top[0] prob = 0.982662  name = brain coral
top[1] prob = 0.008502  name = coral reef
top[2] prob = 0.006621  name = jackfruit, jak, jack
top[3] prob = 0.000543  name = puffer, pufferfish, blowfish, globefish
top[4] prob = 0.000330  name = eel
Unable to init server: Could not connect: Connection refused

(Classification of ResNet50:196): Gtk-WARNING **: 07:32:39.423: cannot open display: 
vitis-ai-user@pc178:/workspace/examples/vai_runtime/resnet50$ tar -xzvf resnet50-vck5000-DPUCVDX8H-8pe-r3.0.0.tar.gz
