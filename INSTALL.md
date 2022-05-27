# Installing the necessary software 

## Option 1: Using MyBinder

1. Create a `.binder/environment.yml` file with the necessary software, using conda instead of mamba. 
2. Create a `.binder/postBuild` file to pip install the drs client. 
3. Visit mybinder.org to create a binder. 


## Option 2: Using AWS and JupyterHub 

[![hackmd-github-sync-badge](https://hackmd.io/rrjnYcZ3QemfuDpt82oomw/badge)](https://hackmd.io/rrjnYcZ3QemfuDpt82oomw)

Permanent link: [github.com/ctb/2022-may-cfde-demo/INSTALL.md](https://github.com/ctb/2022-may-cfde-demo/blob/main/INSTALL.md)

Contact: C. Titus Brown, ctbrown@ucdavis.edu

May 10, 2022

Contents:
[toc]

### Spin up an AWS instance.

Boot an Ubuntu 22.04 AMD64 server - I used `ubuntu/images/hvm-ssd/ubuntu-jammy-22.04-amd64-server-20220420`.

Use a `t2.large` instance (with 8 GB of RAM).

Set the root volume to have 20 GB. (You may want 100 GB if you are going to be working with multiple files.)

Make sure to enable incoming SSH, HTTP, and HTTPS.

### Install The Littlest JupyterHub

Log in, and then install JupyterHub per [the Littlest JupyterHub](https://tljh.jupyter.org/en/latest/):

```
curl -L https://tljh.jupyter.org/bootstrap.py | sudo python3 - --admin admin
```

This will take less than 5 min, usually.

## Create two JupyterHub accounts

Go to the default web port on the instance (`http://` + instance IP address). You should see a JupyterHub login.

Log in as `admin`, using a password of your choosing; the first time you enter the username/password will set the password for that user.

Log out.

Log in as `cfde`, using a password of your choosing.

## Install miniforge

Start a terminal in JupyterHub (New... Terminal) and run:

```
curl -LO https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
bash Miniforge3*.sh
```
answer yes to all the questions.

Then remove the .sh file:
```
rm Miniforge3*.sh
```

### Install software.

Restart the terminal; you should now be the base conda environment.

Install a pile of software into the base environment:
```
mamba install -y -c bioconda sourmash snakemake-minimal ipykernel r-dplyr r-metacoder r-readr
```

Also install the [updated version of the DRS client](https://github.com/ga4gh/ga4gh-drs-client/pull/7):

```
pip install https://github.com/nih-cfde/ga4gh-drs-client/archive/refs/heads/fix/access_json.zip
```

Last but not least, you'll need to establish the conda environment as a new Python environment for Jupyter:
```
ipython kernel install --name=cfde --user
```

and you should now be done!

### Check out git repo

Check out the latest version of [the demo repo](https://github.com/ctb/2022-may-cfde-demo):

```
git clone https://github.com/ctb/2022-may-cfde-demo ~/demo
```

### Create an AMI

At this point you can shut down the instance (NOT terminate!) and create an AMI for others to use.

