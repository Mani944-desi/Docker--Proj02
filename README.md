*************************************************************** Showing image

ubuntu@ip-172-31-40-160:~/custom-nginx$ docker images | grep mani702/custom-nginx
WARNING: This output is designed for human readability. For machine-readable output, please use --format.
mani702/custom-nginx:latest   314238199e9c        279MB         72.4MB   U
ubuntu@ip-172-31-40-160:~/custom-nginx$


ubuntu@ip-172-31-40-160:~/custom-nginx$ docker ps
CONTAINER ID   IMAGE                         COMMAND                  CREATED          STATUS          PORTS                                 NAMES
50337306735a   mani702/custom-nginx:latest   "/docker-entrypoint.…"   13 minutes ago   Up 13 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp   custom-nginx-web-1
ubuntu@ip-172-31-40-160:~/custom-nginx$


ubuntu@ip-172-31-40-160:~/custom-nginx$ docker compose down
WARN[0000] /home/ubuntu/custom-nginx/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
[+] Running 2/2
 ✔ Container custom-nginx-web-1  Removed                                                                                                                 0.2s
 ✔ Network custom-nginx_default  Removed                                                                                                                 0.1s
ubuntu@ip-172-31-40-160:~/custom-nginx$


ubuntu@ip-172-31-40-160:~/custom-nginx$ docker compose up -d
WARN[0000] /home/ubuntu/custom-nginx/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
[+] Running 2/2
 ✔ Network custom-nginx_default  Created                                                                                                                 0.1s
 ✔ Container custom-nginx-web-1  Started                                                                                                                 0.4s
ubuntu@ip-172-31-40-160:~/custom-nginx$1


************************************** Pushing the docker image **************

ubuntu@ip-172-31-40-160:~/custom-nginx$ docker login -u mani702

i Info → A Personal Access Token (PAT) can be used instead.
         To create a PAT, visit https://app.docker.com/settings


Password:

WARNING! Your credentials are stored unencrypted in '/home/ubuntu/.docker/config.json'.
Configure a credential helper to remove this warning. See
https://docs.docker.com/go/credential-store/

Login Succeeded
ubuntu@ip-172-31-40-160:~/custom-nginx$ docker push mani702/custom-nginx:latest
The push refers to repository [docker.io/mani702/custom-nginx]
2a471a600e7d: Pushed
ed1170a736a1: Pushed
6f909aa39e40: Pushed
8f8c038c0a7b: Pushed
ee19579bd1e7: Pushed
1adabd6b0d6b: Pushed
68f899c28c34: Pushed
6a651693b1e8: Pushed
ebb34bdc2b38: Pushed
4ecfb5dfa85b: Pushed
ac228a39c3ed: Pushed
latest: digest: sha256:314238199e9cae01fdde5994fd8aa62deb5dfcbc91a6bb46c84b2bacca8cba73 size: 856
ubuntu@ip-172-31-40-160



ubuntu@ip-172-31-40-160:~/custom-nginx$ docker run -d -p 80:80 mani702/custom-nginx:latest
901a23251246550e9e03359714fae505d9d87074b2f03eccc95314325bbadc31
ubuntu@ip-172-31-40-160:~/custom-nginx$

ubuntu@ip-172-31-40-160:~/custom-nginx$ docker run -d -p 8080:80 mani702/custom-nginx:latest
3babaf2b0a79f47485854285eec447ffa8bf42ba733b2f6b4f74e72e428627de
ubuntu@ip-172-31-40-160:~/custom-nginx$


ubuntu@ip-172-31-40-160:~/custom-nginx$ docker ps
CONTAINER ID   IMAGE                         COMMAND                  CREATED         STATUS         PORTS                                     NAMES
3babaf2b0a79   mani702/custom-nginx:latest   "/docker-entrypoint.…"   3 minutes ago   Up 3 minutes   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   practical_shirley
901a23251246   mani702/custom-nginx:latest   "/docker-entrypoint.…"   3 minutes ago   Up 3 minutes   0.0.0.0:80->80/tcp, [::]:80->80/tcp       pensive_bell
ubuntu@ip-172-31-40-160:~/custom-nginx$






