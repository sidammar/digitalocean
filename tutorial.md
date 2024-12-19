<!-- Title -->
# How To Install Docker on Ubuntu 22.04: A Beginner-Friendly Guide

<!-- Meta Description
Learn how to install Docker on Ubuntu 22.04 step-by-step and start managing containers today with this easy guide
 -->

<!-- Image (Bluish containing Topic Logo + DigitalOcean Mascot)  -->
<img alt="How To Install and Start Using Docker on Ubuntu 22.04" title="How To Install and Start Using Docker on Ubuntu 22.04" loading="lazy" width="752" height="358" decoding="async" data-nimg="1" class="TutorialTemplateStyles__StyledRecordHeaderImage-sc-337a0527-1 eoHutf" srcset="https://i.ibb.co/BZbg08f/sharkie-digitalocean.jpg&amp;width=828 1x, https://i.ibb.co/BZbg08f/sharkie-digitalocean.jpg&amp;width=1920 2x" src="https://i.ibb.co/BZbg08f/sharkie-digitalocean.jpg&amp;width=1920" style="color: transparent;">


<!-- Introduction-->
### Introduction
[Docker](https://www.docker.com/) is a platform that makes it easier and faster to build, share and run applications. Developers have been using it since 2013 since it enables an application to run on any computer on any operating system. Docker employs OS Level Virtualization in which the kernel enables the existence of multiple isolated instances. For more information, check out this blog on [OS Based Virtualization](https://www.geeksforgeeks.org/operating-system-based-virtualization/).

Docker does this by packaging all code files, configurations, dependencies and the runtime environment into one container. This process is called **Containerization** and if you're curious about Docker components, check out [The Docker Ecosystem: An Introduction to Common Components](https://www.digitalocean.com/community/tutorials/the-docker-ecosystem-an-introduction-to-common-components).

In this tutorial, you will set up and work with **Docker Community Edition (CE)** on Ubuntu 22.04. Docker has 2 editions namely Community Edition (CE) and Enterprise Edition (EE). The Community Edition is suitable for small scale projects whereas for larger scale deployments, it is recommended to use the latter. 

When you're finished, you will have learnt how to install Docker, manage containers and images, and upload an image to a Docker repository.

You can also try our [1-Click Docker Installation](https://marketplace.digitalocean.com/apps/docker) to get up and running with a pre-installed Docker Droplet.


## Prerequisites

Before starting, ensure you have:

- One Ubuntu 22.04 x64 server with at least 1GB of RAM which includes a non-root user with `sudo` privileges following the [Ubuntu 22.04 inital server setup guide](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04) which also includes an active firewall. 
- An account on [Docker Hub](https://hub.docker.com/) if you wish to create your own images and push them to Docker Hub, as shown in Steps 7 and 8.


## Step 1 — Installing Docker

The official Ubuntu repository may not always have the latest Docker package, which is why we'll be installing it directly from the source which is the [Official Docker Repository for Ubuntu](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository). 

To do that, we’ll add the **GPG** Key from Docker and then proceed to add the repository to the apt source.



What is a **GPG** Key?
Basically, A GPG key is like a digital seal that proves the files you download are authentic and not tampered with.

 - First, update your existing list of packages:
```command
sudo apt update
```

 - Next, install the CA certifcates package to authenticate Docker's official repository:
```command
sudo apt-get install ca-certificates curl
```

 - Create the /etc/apt/keyrings directory and allow full access to manage and store configuration files:
```command
sudo install -m 0755 -d /etc/apt/keyrings
```
This ensures secure storage for Docker's configuration keys.


 - Then add the GPG key for the official Docker repository to your system:
```command
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```

 - Grant all permissions to the main `docker.asc` config file in order to ensure no errors:
```command
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

 - Add the Docker repository to APT sources:
```command
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

 - Update your existing list of packages again for the addition to be recognized:
```command
sudo apt-get update
```

 - Then proceed to install the latest Docker version:
```command
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

 - Verify that the installation is successful by checking the docker version:
```command
sudo docker run hello-world
```
Output:-

![Docker hello-world output](https://i.ibb.co/0nQtgm8/docker-final-output.png "a title")


<!--Conclusion -->
## Conclusion

Congratulations! You’ve successfully installed Docker on Ubuntu 22.04. With Docker installed, you can now create and manage containers for consistent app deployment across different environments. To explore more, check out our guide on [Working with Docker Containers](https://www.digitalocean.com/community/tutorials/working-with-docker-containers).

DigitalOcean makes it simple to build, deploy, and scale your apps. With easy tools and reliable cloud infrastructure, it’s built for developers at any stage. Start building smarter with [DigitalOcean](https://www.digitalocean.com)!

Also, we're coming to Austin, Texas on January 22nd, 2025 and are excited to invite you to attend **Deploy: Scaling with Simplicity**. Find more information [here](https://www.digitalocean.com/blog/deploy-2025-scale-with-simplicity).

