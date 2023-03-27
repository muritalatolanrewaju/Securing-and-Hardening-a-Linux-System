# Securing and Hardening a Linux System
## This project covers how to secure and harden a Linux system.
![Untitled](docs/assets/overview.png)
In today's digital age, where Linux powers a significant portion of internet servers, prioritizing the security of Linux systems is crucial in preventing cyber-attacks and data breaches. This Practical Linux, Security, and Hardening project guide individuals seeking to implement security measures and best practices to secure and harden their Linux systems.

This guide is based on OpenSCAP configurations, including the U.S. Government Commercial Cloud Services (C2S) baseline inspired by CIS v2.1.1, C2S for Red Hat Enterprise Linux 7 v0.1.43, and the Red Hat Enterprise Linux 7 Security Technical Implementation Guide (STIG). In addition, these configurations are derived from NIST 800-53 and related documents.

This project provides valuable insights into how attackers can breach Linux systems when they have physical access and various countermeasures to safeguard against such attacks. It also covers the authentication systems utilized in Linux, including creating strong passwords and managing account and password expirations for different account types.

The networking section of the project offers guidance on securing network services running on Linux systems and configuring the local firewall. Furthermore, the project delves into Linux file system security, including permissions, special modes, file attributes, and ACLs, to ensure adequate protection against data breaches.

Lastly, the project emphasizes the importance of staying up-to-date with the latest security concerns for your Linux distribution and continuing your security education.

Overall, this technical project provides a comprehensive guide to securing and hardening a Linux system using various techniques and tools based on OpenSCAP configurations. By implementing these security measures and best practices, users can reduce vulnerability to attacks and ensure better protection against data breaches.

1. [Installation of Docker Engine on Ubuntu](docs/1-installing-docker-engine-on-ubuntu.md): The project starts with the installation of the Docker Engine on Ubuntu. It covers the installation process, checking the installed version, and configuring Docker to start on boot.
2. [Understanding Docker Client](docs/2-the-docker-client.md): Next, the project explains the Docker client and its role in managing Docker containers. It covers various Docker commands, such as docker run, docker stop, docker ps, and docker logs.
3. [Lab: Running Web Servers in a Docker Container](docs/3-lab-running-webservers-in-a-docker-container.md): The project includes a lab on running web servers in a Docker container. It explains how to create a Dockerfile, build a Docker image, and run a Docker container. The lab covers using different web server images, such as Apache and Nginx.
4. [Getting Shell Access to a Container](docs/4-getting-shell-access-to-a-container.md): The project explains how to access shell of a running container. It covers using the Docker exec command and Docker attach command to access shell of a container.
5. [Modifying a Container](docs/5-modifying-a-container.md): The project also covers modifying a running container. It explains how to create a new image from a running container, modify the image, and create a new container from the modified image.

This practical project provides a comprehensive understanding of Securing and Hardening a Linux System on Ubuntu. It covers the installation process, understanding the Docker client, running web servers in a Docker container, accessing the shell of a container, and modifying a container. This project is a must-do for anyone interested in Docker and containerization.

