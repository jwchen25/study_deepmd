# IPE北京服务器安装deepmd套件、deepchem、rdkit等软件包的python环境
## *2021-03-18 By Junwu Chen*

# 方法1 (Method 1)

### 1. 安装anaconda或miniconda (install anaconda/miniconda)

### 2. 用conda创建python3.6的虚拟环境 (create a python3.6 virtual environment by conda):
```
conda create -n deepc python=3.6  libprotobuf==3.8.0
```
激活刚创建的python虚拟环境 (activate the created virtual environment):
```
conda activate deepc
```
### 3. 安装deepmd-kit (install deepmd-kit):
```
conda install deepmd-kit=*=*cpu lammps-dp=*=*cpu -c deepmodeling
```
### 4. 安装dpgen0.8.1 (install dpgen 0.8.1):
```
pip install pymatgen==2019.6.5 \
            monty==2.0.4 \
            ase==3.17.0 \
            paramiko==2.6.0 \
            custodian==2019.2.10 \
            dpgen==0.8.1
```
### 5. 安装deepchem (install deepchem):
```
pip install deepchem==2.5.0
```
### 6. 安装rdkit (install rdkit):
```
conda install -y -c conda-forge rdkit
```
### 安装结束

# 方法2 (Method 2)
## 使用yml快速配置conda虚拟环境 (Use .yml file to quickly configure the conda virtual environment)
### 1. 安装anaconda或miniconda (install anaconda/miniconda)

### 2. 从.yml文件创建python虚拟环境 (Use .yml file to create desired conda virtual environment):
```
conda env create -f deepc_environment.yml
```
