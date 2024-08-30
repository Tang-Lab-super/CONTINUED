# CONTINUED: Cluster, integration and annotation of *In situ* metabonomics data


## Overview
`CONTINUED` is a algorithm to process *In situ* metabonomics data include reconstruction of histological spatial structure based on single sample clustering, integration of multiple samples and annotation with LC-MS data.
![figure1](./docs/Img/Overview.png)


Using `CONTINUED` you can do:
* Processing *In situ* metabonomics data which include tissue detection, remove noise signal and clustering.
* Annotating *In situ* metabonomics data utilize LC-MS data.

## How to install CONTINUED
* Step1: Set up conda environment for `CONTINUED`
  ```
  conda create -n Continued_env python=3.9
  conda activate Continued_env
  ```
* Step2: Install `CONTINUED` from shell
  ```
  pip install git+https://github.com/Tang-Lab-super/CONTINUED.git
  ```
* Step3: Install the requirement packages of `CONTINUED` from shell
  ```
  git clone https://github.com/Tang-Lab-super/CONTINUED.git
  pip install -r ./CONTINUED/requirements.txt
  ```

## How to use CONTINUED
Once you have successfully installed `CONTINUED`, please see our [**Processing_tutorial**](./Tutorial/1.Tutorial.process.ipynb) and [**Annotating_tutorial**](./Tutorial/2.Tutorial.annotation.ipynb) to help you use `CONTINUED`.

Or you can visit our [**Document**](https://continued-doc.readthedocs.io/en/latest/index.html) [![Documentation Status](https://readthedocs.org/projects/continued-doc/badge/?version=latest)](https://continued-doc.readthedocs.io/en/latest/?badge=latest), which contains the installation, usage, and tutorials of `CONTINUED`.


## Improvements
We welcome any comments about `CONTINUED`, and if you find bugs or have any ideas, feel free to leave a comment [FAQ](https://github.com/Tang-Lab-super/PROST/labels/FAQ).


