# DIY Container
These scripts are designed to highlight the basic anatomy of a container. They provide basic network, IPC, PID, UTS, cgroup, and mount namespacing, as well as filesystem isolation.

## Pre-requisites
* A bash shell
* 12Mi disk space

## Usage
*The following commands require root privileges. The container filesystem behaves like a "real" container, thus any changes made within `runtime-exec` will not be persisted. You can run either script with `VERBOSE=1 ./<script> <args>` to see what commands are being executed.*
1. `cd` to the repo directory
2. Execute `./setup-image` to setup the container image (uses alpine)
3. Execute `./runtime-exec <cmd>`, where `<cmd>` is the command to execute within the container image (i.e. `sh`)
   1. The container image contains `httpd`, which can be run by passing `httpd -D FOREGROUND` as the command and connecting to <http://10.178.61.2>
   2. You can examine the network and PID containment with `ip`, `ping`, and `ps`

## TL;DR
```
git clone https://github.com/Nuvalence/diy-container.git
cd diy-container
sudo ./setup-image
sudo ./runtime-exec httpd -D FOREGROUND
```
Assuming all went well, the containerized `httpd` instance should now be accessible at <http://10.178.61.2>.
