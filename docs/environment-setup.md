## Environment Setup

### Prerequisites:

- [Node.js (npm)](https://nodejs.org/en/download/)
- [Redis](https://redis.io/) (2 methods)
  - Use [Docker and docker-compose](https://docs.docker.com/install/)
  - Install as a [native application](https://redis.io/topics/quickstart)

### Install Redis as a native application

#### Linux:

Install Redis using your distribution's package manager, for example:

- Ubuntu based: `sudo apt install redis`
- Red Hat, Fedora: `sudo dnf install redis`

_Once Redis is installed, you can start it in a terminal by running:_

```
redis-server
```

#### Windows:

We are using [Chocolatey package manager](https://chocolatey.org/) to install Redis on Windows. To get Chocolatey, simply follow this [guide](https://chocolatey.org/install) and run the following commands:

1. To install Redis: `choco install redis-64 -v`
1. To set Redis as a windows service: `redis-server --service-install`
1. To start Redis: `redis-server --service-start`
1. To check if running and display server information: `redis-cli info`

### Docker and Docker-Compose Set Up

#### Linux-Ubuntu

This guide is sourced from the official [Docker-CE](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and [Docker-Compose](https://docs.docker.com/compose/install/) Installation Documentation.

**Install Docker Engine - Community Edition**

1. Update the apt package index: `sudo apt-get update`
2. Install packages to allow apt to use a repository over HTTPS:

```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

3. Add Docker’s official GPG key: `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`
4. Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, by searching for the last 8 characters of the fingerprint: `sudo apt-key fingerprint 0EBFCD88`
5. Use the following command to set up the stable repository:

```
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

6. Update the apt package index again: `sudo apt-get update`
7. Install the latest version of Docker Engine community: `sudo apt-get install docker-ce docker-ce-cli containerd.io`
8. Add yourself to the Docker group ([source](https://docs.docker.com/install/linux/linux-postinstall/)):
   1. Create the Docker group: `groupadd docker`
   1. Add your user to the group: `sudo usermod -aG docker $USER`
   1. Log out and log back in (you may have to restart if you are running through a virtual machine)
9. Verify your installation by running `docker run hello-world`. This should print a hello world paragraph that includes a confirmation that Docker is working on your system.
   _NOTE: This may cause errors if you have already tried to run docker before. If you get errors then run the following commands to reset it:_

```
sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
sudo chmod g+rwx "$HOME/.docker" -R
```

10. Now run docker as a service on your machine, on startup:
    1. Enable docker on startup: `sudo systemctl enable docker`
    1. Disable docker on startup: `sudo systemctl disable docker`

**Install Docker-Compose**

11. Run to download the current stable version of Docker-Compose:

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

12. Apply executable permissions to the downloaded file: `sudo chmod +x /usr/local/bin/docker-compose`
13. Check installation using: `docker-compose --version`

_NOTE: This will not work on WSL (Windows Subsystem for Linux). Use the approach listed above under WSL._

#### MacOS (Sierra 10.12 or above)

1. Get [Docker for Desktop For Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
1. Docker for Desktop comes with docker-compose installed.

#### Windows 10 Pro, Enterprise, or Education

1. Get [Docker for Desktop For Windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
1. Docker for Desktop comes with docker-compose installed.

#### Windows 10 Home Edition and Windows Subsystem for Linux (WSL)

Docker Desktop for Windows is not available on Home Edition, and you cannot run docker in WSL (Windows Subsystem for Linux). You can get the environment set up using **one** of these three methods:

- Get [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/) instead of Docker Desktop for Windows. Make sure that your system can do virtualization and enable virtualization.
- Set up a virtual machine to run Linux Ubuntu
  1. Make sure your system can do virtualization and enable it.
  1. [Download VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  1. [Follow this helpful youtube tutorial to create a virtual machine with Ubuntu](https://www.youtube.com/watch?v=ThsxqznrgCw&t=401s)
  1. Use the Linux installation instructions [below](#linux-Ubuntu).
- Update your home edition to Windows 10 Education Edition
  1. Download Windows 10 Education Edition from the [Seneca Software Center](https://senecacollege.onthehub.com/WebStore/OfferingDetails.aspx?o=c0bd2c36-a530-e511-940e-b8ca3a5db7a1)
  1. Update your OS using the installation instructions.
  1. Use [Windows 10 Education Edition](#Windows-10-Pro,-Enterprise,-or-Education) set up instructions.
