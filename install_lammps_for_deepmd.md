# IPE北京服务器安装lammps(intel_mpi_deepmd版)过程
## *2021-03-15 By Junwu Chen*
### 参考教程：http://t.cn/A6tmS3Aw
### 随着时间的变更，lammps版本提升、编译器更新等原因，本教程可能不会完全适用
# 
# 
### 1. 下载lammps最新稳定版源码包（可自行下载需要的版本的源码包:[官方](https://lammps.sandia.gov/tars/);[github](https://github.com/lammps/lammps/releases)）
wget方式下载：
```
wget https://lammps.sandia.gov/tars/lammps-stable.tar.gz --no-check-certificate
```
解压：
```
tar -xzf lammps-stable.tar.gz
```
### 2. 安装编译lammps
编译环境加载:
1. Intel开发套件(parallel_studio_xe_2018)加载，一般北京服务器登陆时自动加载
```
source /opt/intel/parallel_studio_xe_2018/psxevars.sh
```
2. 高版本GCC加载(如v_7.5.0，可采用module方式加载)，因为makefile是由GNU make编写
```
module load GCC/7.5.0
```
## 

进入lammps安装目录:
```
cd lammps-29Oct20/src/
```
将DeePMD-kit中的lammps的模块文件拷贝至`src/`下，如果采用conda安装deepmd-kit，则运行：
```
cp -r $CONDA_PATH/envs/$ENV_NAME/share/USER-DEEPMD .
```
其中`$CONDA_PATH`为安装的anaconda或miniconda的路径，其中`$ENV_NAME`为用conda安装deepmd-kit的虚拟环境的名称。conda安装deepmd-kit的步骤见[教程](http://t.cn/A6tmS3Aw)
## 
选择需要安装的package：
1. 只安装deepmd-kit包 (此步目的是在lammps运行中可以调用deepmd类型的势函数文件)
```
make yes-kspace
make yes-user-deepmd
```
2. 选择安装其它的包(如不需要，跳过此步)

如：`make yes-kspace yes-manybody yes-molecule`

或：`make yes-std && make no-lib`

相关命令，详情见[官方手册](https://lammps.sandia.gov/doc/Build_package.html)：
```
make package-status     # show which packages are currently installed
make ps                 # show which packages are currently installed
make yes-all            # install all packages
make no-all             # uninstall all packages
make yes-std            # install standard packages
make no-std             # uninstall standard packages
make yes-user           # install user packages
make no-user            # uninstall user packages
make yes-lib            # install packages that require extra libraries
make no-lib             # uninstall packages that require extra libraries
make yes-ext            # install packages that require external libraries
make no-ext             # uninstall packages that require external libraries
```
注意：有些软件包需要其它库依赖，无法安装，详情见[官方手册](https://lammps.sandia.gov/doc/Build_extras.html)
## 
开始编译：
```
make -j 12 intel_cpu_intelmpi
```
其中的`12`代表用12核cpu并行编译，若之前编译过或编译失败过，请在正式编译前运行`make clean-all`
