---
description: Setup CentOS for Developers
---

# Setup CentOS for coding

CentOS is a Linux distribution that provides a free, community-supported computing platform functionally compatible with its upstream source, Red Hat Enterprise Linux (RHEL). In January 2014, CentOS announced the official joining with Red Hat while staying independent from RHEL under a new CentOS governing board.

### Install basic development tools

The `Development Tools` package group provides the GNU Compiler Collection (GCC), GNU Debugger (GDB), and other related development tools.

```bash
$ # install Development Tools bundle
$ sudo yum group install "Development Tools"
```

###

### Install [Git](https://git-scm.com/)

[Git](https://git-scm.com/) is the most popular version control system on Linux. It is easy to use, amazingly fast, it’s very efficient with large projects, and it has an incredible branching system for non-linear development.

```bash
$ sudo yum install git
```

###

### Install Python3

By default, CentOS is not installing python3, but we can easily set up the installation.

```bash
$ sudo yum install python3
$
```

> And Python3 libraries for development

```bash
sudo yum install python3-devel
```

## Installing Apache

Apache is available within CentOS’s default software repositories, which means you can install it with the `yum` package manager.

```bash
$ sudo yum install httpd
```

Apache does not automatically start on CentOS once the installation completes. You will need to start the Apache process manually:

```bash
$ # this cmd will start the server
$ sudo systemctl start httpd
$
$ # test server status
$ sudo systemctl status httpd
$
$ # access the default page with `lynx`
$ sudo yum install lynx
$ 
$ lynx http://localhost
```

###

### Installing [Node.js](https://nodejs.org/)

Node.js is an open-source, cross-platform, JavaScript runtime environment that executes JavaScript code outside of a browser.

```bash
$ sudo yum install nodejs
$
$ # check the version
$ node --version
```

###

### Installing [Yarn](https://yarnpkg.com/)

The yarn is an advanced package management software for Node.js applications. It is a fast, secure, and reliable alternative that any other Nodejs package manager.

```bash
$ sudo npm install yarn -g
$
$ # check the version
$ yarn -v
```

###

### Installing Container Tools

RHEL 8 does not officially support Docker; in this section, we will show how to install the new set of container tools as well as the old lady, docker package. The docker package is replaced by the Container Tools module, which consists of tools such as Podman, Buildah, Skope, and several others.

```bash
$ dnf module install -y container-tools
```

###

### Install Docker

Now install docker from the official repositories by running the following commands. Here, the yum-utils package provides the yum-config-manager utility.

```bash
$ dnf install yum-utils
$ yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
$ dnf install containerd.io docker-ce docker-ce-cli
```

###

### Installation of DNF

For packages installation, we can use `dnf` tool instead of the traditional `yum` package manager. DNF is same as Yum that installs, updates and removes packages on RPM bas4ed Linux systems. DNF is introduced for improving the bottlenecks of Yum such as performance, Memory usages, Dependency resolution, speed, and some other factors.

To install DNF on RHEL/CentOS 7 systems, you need to set up and enable `epel` Yum repository before installing DNF

```bash
$ # Initial Setup
$ yum install epel-release
$
$ # Install `DNF` tool
$ yum install dnf
$ 
$ # test the installation
$ dnf –help
```
