
# Projects Name – Bringing Installing Docker with Homarr The Conatinment Manager

# Date -- 08 December 2025

## Purpose For This

With file sharing being successfully added to the server, now we can add on services to bring the server to its true capabilities. Which we will use docker for most of these services since it will be easier to manage such services

Of course, that would be a tedious task if it wasnt for the fact that we can bring in a container manager that will help in that task. Such as Homarr that is the most recognized manager to use.

## What I Did

### Installing Docker

* First things first, I access my server with ssh for remote use.

* Make sure that all the repositories and packages are updated to the latest version.

* We need to install docker onto the server to begin added these services, so run the command: "sudo apt install docker.io" and confirm installation.

* Type next "sudo systemctl enable docker" so docker will always start automatically when the system boots so we dont need to constantly start it ourselves (If you wanna run it mannualy then type "sudo systemctl start docker".)

* To test if it works, we must use this command "sudo docker hello-world". If you got a hello message from it, then it works fine.

* Finally, we need docker compose so we can bring in the docker images with a file. That's done with this command: "sudo apt install docker-compose-v2"

### Bringing Homarr for Docker Containers

* Ok before we bring Homarr, we need to create some directories for the docker-compose files, first we create a file named for "Docker Files", use "cd docker-files" to enable as a current directory. That will be where all the services files will be added, each one containing a docker compose file with the name "docker-compose.yml".
   
* So in the docker-file file, create a file by the name of "Homarr" then make that the current directory

* Now create the docker file with "nano docker-compose.yml"
  
* Copy and paste this to the file:
```
#---------------------------------------------------------------------#

#  Homarr - A simple, yet powerful dashboard for your server.#

#---------------------------------------------------------------------#

services:

homarr:

container_name: homarr

image: ghcr.io/homarr-labs/homarr:latest

restart: unless-stopped

volumes:

- /var/run/docker.sock:/var/run/docker.sock # Optional, only if you want docker integration

- ./homarr/appdata:/appdata

environment:

- SECRET_ENCRYPTION_KEY=b6b4e337ad72206a7ef82f6a3ce365b8d980c1add2b2584dffd82e3de21be77b

ports:

- 7575:7575`
```

* Press Ctrl + O to write out and enter to confirm, then Ctrl + X to exit.
* Finally, run "docker compose up -d" in the same directory so it will start Homarr in the background.

## Managing Homarr

* Now we can access the dashboard in your local browser with this address:  **<Your_Server_IP>:7575.**
* It will prompt you to make an account to access it so save the info through a password manager or personal notes so you dont forget.
* It will take you to a screen that will let you configure the settings, but the default settings are fine enough so just press continue.
* Now reate boards that will hold the services you can look over.

## Devices Used

- Lenovo Ideapad 110 15-ISK
- ASUS TUF A15

## Problems & Fixes

- No Issues :D

## Commands Used

- sudo apt install docker.io
- sudo systemctrl enable docker
- sudo docker hello-world
- sudo apt install docker-compose-v2
- mkdir docker-files
- cd docker-files
- mkdir Homarr
- cd Homarr
- nano docker-compose.yml
- sudo docker compose up -d

## Screenshots

## Leasons Learned

Thanks to this we can run many services and manage all the containers with ease. This will be useful for the next service we will add next time that will benefit further with these services.

## Sources Used:

- https://homarr.dev/docs/getting-started/installation/docker
- https://www.youtube.com/watch?v=cqbh-RneBlk
- https://homarr.dev/docs/getting-started/installation/docker/
