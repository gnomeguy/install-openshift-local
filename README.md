# install-openshift-local
How to install Red Hat OpenShift Local on your laptop (Ubuntu)

**Get started with OpenShift Local**
For Linux, OpenShift Local deployments are supported in the 2 latest releases of Fedora and Red Hat Enterprise Linux. You can also install it on other Linux distributions if you have the following requirements:

Network manager
Libvirt
Qemu (qemu-kvm)
To get started with OpenShift Local, download the crc tool from the Red Hat Console. If you don't have a Red Hat account, you can create one for free with the Red Hat Developer program.

After you log in, download both the installation package and the pull secret from the Red Hat OpenShift Local screen:
![image](https://github.com/user-attachments/assets/4bd8815b-0c0c-444d-9377-fe6a339f07e2)

When the download finishes, decompress the crc tool and move it to a location within your PATH. If you prefer to keep everything local to your user account, then create a directory and add it to your PATH like this:
$ cd ~/Downloads/

$ tar xvf crc-linux-amd64.tar.xz 

crc-linux-2.16.0-amd64/

crc-linux-2.16.0-amd64/LICENSE

crc-linux-2.16.0-amd64/crc

$ mkdir -p ~/local/bin

$ mv crc-linux-*-amd64/crc ~/local/bin/

$ export PATH=$HOME/local/bin:$PATH

$ crc version

CRC version: 2.16.0+05b62a75

OpenShift version: 4.12.9

Podman version: 4.4.1

$ echo 'export PATH=$HOME/local/bin:$PATH' >> ~/.bashrc
**Set up your machine**

$ crc config set consent-telemetry no

$ crc config view
 consent-telemetry                     : no
 
 Now you can run the setup to configure your machine:

$ crc setup

**Start OpenShift Local**
crc start -p ~/Downloads/pull-secret.txt

If you receive an error "Error starting machine: Error in driver during machine start: virError(Code=9, Domain=10, Message='operation failed: Unable to find a satisfying virtiofsd')" then run below commands ;

sudo apt install virtiofsd

sudo apt install virt-manager

After a few minutes, the cluster is up and running and crc prints the connection information:

Started the OpenShift cluster.

The server is accessible via web console at:
  https://console-openshift-console.apps-crc.testing

Log in as administrator:
  Username: kubeadmin
  Password: *****-****-****-47t22

Log in as user:
  Username: developer
  Password: developer

Use the 'oc' command line interface:
  $ eval $(crc oc-env)
  $ oc login -u developer https://api.crc.testing:6443
  
For detailed info : https://www.redhat.com/en/blog/install-openshift-local
