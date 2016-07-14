isilon-hadoop-tools
===================

Scripts for the creation of Hadoop local user accounts and filesystem trees for Hortonworks, Cloudera, PivotalHD, and IBM Big Insights.
 
**MUST** be run as root on Isilon.
 
This repository contains two scripts:
 
**Isilon-create-users.sh** – The script creates local users and groups in the local provider for the access zone and outputs a files used to transfer onto compute nodes so that users and ID’s match. 

**Usage:**

``bash isilon-create-users.sh --dist --startuid --startgid --zone --append-cluster-name``

**Arguments:**

    * dist – distribution of Hadoop (cdh, hwx, phd3, bi)
    * startuid – the beginning UID range for the creation of users (default is 1000)
    * startgid – the beginning GID range for the creation of users (Default is 1000)
    * zone – the name of the access zone where the users should be created
    * append-cluster-name – the Hadoop cluster name the script should append to the usernames (useful for multi-tenant environments that will use a single KDC)
 
 
**isilon-create-directories.sh** – This script creates a base directory skeleton for the specified hadoop distribution and assigns the correct ownership based on the users created with isilon-create-users.s
 
**Usage:**

``bash Isilon-create-directories.sh –dist --zone --append-cluster-name --fixperm``

**Arguments**

    * dist – distribution of Hadoop for which the script should create an HDFS directory skeleton
    * zone – the name of the access zone where the directory skeleton should be created
    * append-cluster-name – the Hadoop cluster name the script should append to the usernames (useful for multi-tenant environments that will use a single KDC)
    * fixperm – argument to alter the permissions ownership of the directory skeleton according to the users created by isilon-create-users.sh
