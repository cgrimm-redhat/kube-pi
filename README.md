Kube-Pi
=========

The goal of this project is to deploy a small lab cluster of Kubernetes in a repeatable fashion onto a Raspberry Pi Cluster with a couple of x86 VM Nodes  

Current Configuration
------------

 4 Raspberry Pi Modle 4b 8GB
 2 x86 Virtual Machines running on a hypervisor
 Ubuntu 20.04 on all systems
 Internet Access


This will deploy a cluster with one Rapsberry Pi 4 as the Master.  The remaining nodes (3 Raspberry Pi's and 2 x86 VMs) will be deployed as worker nodes.  The SDN is managed via Calico.

Usage
--------------

I do assume that you will have a user to do your SSH configuration, though the default with Ubuntu 20.04 is username ubuntu password ubuntu

    ansible-playbook -i hosts main.yml
    
If you are using the ubuntu username & password then the usage would look like

    ansible-playbook -i hosts main.yml -U ubuntu -k -K

All variables should be managed through group_vars/all 
The Kubernetes toke is the biggest gotcha here as it isn't automatically generated or populated which is a future modification to the code and may give you some headaches when attempting to join the nodes after the master is deployed.  A good portion of the vars are also unused at the moment, so consider those unimplemented for the time being.

Kudos & Thanks
------------------

Jamie Duncan for his own variant of this code base and contributions to that as it saved me from having to reinvent the wheel.
