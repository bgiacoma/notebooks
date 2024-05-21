
These instructions have been tested on  [Linux Ubuntu 20.04 LTS](https://ubuntu.com/), including an installation within a  [Virtual machine](https://www.virtualbox.org/)  or within the  [WSL of Windows 10 and 11](https://learn.microsoft.com/en-gb/windows/wsl/install).

If you use the WSL in Windows 10 (**you do not need to do this if using Windows 11**), you should also install an Xserver such as  [VcXsrv](https://sourceforge.net/projects/vcxsrv/). You will also need to add the following lines to your  `.bashrc`  file within the WSL:

```
#To add X-server support to WSL2 under Windows 10  
export DISPLAY=$(awk '/nameserver / {print $2; exit}' /etc/resolv.conf 2>/dev/null):0  
export LIBGL_ALWAYS_INDIRECT=1`
```

Within Ubuntu, install the following packages:

```
sudo apt-get install gcc git numactl libgsl-dev libpapi-dev python3 python-is-python3 python3-pip libhwloc-dev libudev-dev make cmake libopenmpi-dev libhdf5-openmpi-dev libfftw3-dev libssl-dev liblapack-dev g++ curl gfortran patch pkg-config libhdf5-dev libjpeg-turbo?-dev
```

```
pip install numpy matplotlib pytest setuptools h5py numba scipy kuibit
```

You can now install the Einstein Toolkit. There are two options. In both cases, if you use conda, I suggest deactivating the conda environment before proceeding with the installation (`conda deactivate`) since it may cause problems when compiling.

**Option A (full installation)**

1.  Create a directory where to install the Einstein Toolkit, e.g.,  `mkdir ET_2023_11`
2.  Go into that directory,  `cd ET_2023_11`
3.  `curl -kLO https://raw.githubusercontent.com/gridaphobe/CRL/ET_2023_11/GetComponents`
4.  `chmod a+x GetComponents`
5.  Download the toolkit,  `./GetComponents --shallow https://bitbucket.org/einsteintoolkit/manifest/raw/ET_2023_11/einsteintoolkit.th`
6.  `cd Cactus`
7.  `./simfactory/bin/sim setup-silent`
8.  Compile the toolkit  `./simfactory/bin/sim build -j2 --thornlist ../einsteintoolkit.th`

**Option B (download and install only the components needed to run the tutorials)**

1.  Create a directory where to install the Einstein Toolkit, e.g.,  `mkdir ET_2023_11`
2.  Go into that directory,  `cd ET_2023_11`
3.  `curl -kLO https://raw.githubusercontent.com/gridaphobe/CRL/ET_2023_11/GetComponents`
4.  `chmod a+x GetComponents`
5.  Download the toolkit,  `./GetComponents --shallow https://raw.githubusercontent.com/bgiacoma/notebooks/main/Einstein_Toolkit_Tutorials/TOV_Sod.th`
6.  `cd Cactus`
7.  `./simfactory/bin/sim setup-silent`
8.  Compile the toolkit  `./simfactory/bin/sim build -j2 --thornlist ../TOV_Sod.th`

Note: especially in the case of option A, the compilation of the Einstein Toolkit (step 8) may be quite long (even more than 1 hour on a laptop). You may also see several warning messages, but if you do not get any error then you should be fine. Check the `exe`  directory within  `Cactus`  and, if compilation was successful, you should see an executable named  `cactus_sim`  (type  `./cactus_sim --help`  to check).  
  
More details on installation, also on non-Linux machines, can be found  [here](http://einsteintoolkit.org/documentation/new-user-tutorial.html).
