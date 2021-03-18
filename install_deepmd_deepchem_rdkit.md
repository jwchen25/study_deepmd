# IPE北京服务器安装deepmd套件、deepchem、rdkit等软件包的python环境
## *2021-03-18 By Junwu Chen*

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
### 安装deepchem (install deepchem):
```
pip install deepchem==2.5.0
```
### 安装rdkit (install rdkit):
```
conda install -y -c conda-forge rdkit
```
