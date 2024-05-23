# Labo03 - Run a first container

## Pedagogical intent

In this lab, you'll:

* Get to grips with the first Docker commands,
* Run your first Docker
* Familiarize yourself with port publishing

---

Note: the docker engine must be running

## Task 01 - Get to grips with the first Docker commands

* List all images present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
❯ docker images
REPOSITORY      TAG       IMAGE ID       CREATED        SIZE
dgraph/dgraph   latest    f88a502641ff   9 months ago   170MB
dgraph/ratel    latest    98e9777f3b57   3 years ago    26.7MB

```

* Get the official Nginx image using this command

[INPUT]
```bash
docker pull nginx
```

[OUTPUT]
```
❯ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
Digest: sha256:a484819eb60211f5299034ac80f6a681b06f89e65866ce91f356ed7c72af059c
Status: Image is up to date for nginx:latest
docker.io/library/nginx:latest
```
Other commandes for Docker pull
```
docker image pull [OPTIONS] NAME[:TAG|@DIGEST]
Ex : 
docker pull debian:bookworm -> spécifie à l'aide de tag la version choisie
```

Note : do you see the different layer uploaded ?

* List -again- all image present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
❯ docker images
REPOSITORY      TAG       IMAGE ID       CREATED        SIZE
nginx           latest    8dd77ef2d82e   2 weeks ago    193MB
dgraph/dgraph   latest    f88a502641ff   9 months ago   170MB
dgraph/ratel    latest    98e9777f3b57   3 years ago    26.7MB

```

Note : 188 MB is the size of your image... check it.

* List -again- all image present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
//TODO
```

* List all Docker

[INPUT]
```
docker ps -a
```

[OUTPUT]
```
CONTAINER ID   IMAGE                  COMMAND                  CREATED        STATUS                    PORTS     NAMES
50e0fb66ea7d   dgraph/dgraph:latest   "dgraph alpha --my=a…"   2 months ago   Exited (0) 2 months ago             zangular-home-alpha-1
41c8c95c81b2   dgraph/ratel           "dgraph-ratel"           2 months ago   Exited (2) 2 months ago             zangular-home-ratel-1
c3462d23b725   dgraph/dgraph:latest   "dgraph zero --my=ze…"   2 months ago   Exited (0) 2 months ago             zangular-home-zero-1

```

## Task 02 - Run the container

* Run Nginx Docker

[INPUT]
```
docker run nginx
```

[OUTPUT]
```
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/05/23 06:52:18 [notice] 1#1: using the "epoll" event method
2024/05/23 06:52:18 [notice] 1#1: nginx/1.25.5
2024/05/23 06:52:18 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
2024/05/23 06:52:18 [notice] 1#1: OS: Linux 6.6.12-linuxkit
2024/05/23 06:52:18 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2024/05/23 06:52:18 [notice] 1#1: start worker processes
2024/05/23 06:52:18 [notice] 1#1: start worker process 29

```

* Can you reach the default page of nginx
Note : By default, Nginx is listening on port 80
##### Problème(s) rencontré(s) :
* Cette commande n'est pas suffisante pour pouvoir curl la page par défaut de Nginx :
* https://serverfault.com/questions/893430/unable-to-curl-nginx-rhel-docker-container
* Il faut publier le port 80 du container sur un port du host pour pouvoir y accéder : 
````
 docker run -it -p 8080:80  nginx
````
 - -it  : pour ouvrir le terminal interactif dans le docker desktop (meilleur retour des erreurs)
- -p 8080:80 : pour publier le port 80 du container sur le port 8080 du host
- Maintenant le curl va retourner l'HMTL de la page par défaut de Nginx

[INPUT]
```
curl localhost
```

[OUTPUT]
```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

* Stop this first attempt

[INPUT]
```
docker stop <id>
```

[OUTPUT]

Je n'ai eu que l'id en retour du stop, pas de message de confirmation, mais le conteineur a bien été stoppé (vérification dans le docker desktop)
```
<id>
```

## Task 03 - Familiarize yourself with port publishing

* Make it possible to reach nginx with this command

[Publish a port](https://docs.docker.com/network/#published-ports)

Même histoire que plus haut.

Publier le port dans la commande de run pour pouvoir curl la page par défaut de Nginx
- docker run -it -p 8080:80  nginx

[INPUT]
```
curl localhost:8080
```

[OUTPUT]
```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

* Stop and delete the container

[INPUT]
```
docker stop <id>
docker rm <id>
```

[OUTPUT]
```
<id>
```

* Delete the image

[INPUT]
```
docker rmi nginx
```

[OUTPUT]

Utilise part default l'image installée la plus récente
```
Untagged: nginx:latest
Untagged: nginx@sha256:a484819eb60211f5299034ac80f6a681b06f89e65866ce91f356ed7c72af059c
Deleted: sha256:8dd77ef2d82eade8dcf2c08ea032bd9cba04c9d28ace2ccf08ad6804c27bf14f
Deleted: sha256:bb140dd08d08c678705a24498fb77e0a656efc3ed39ec630f50b27667bdc6857
Deleted: sha256:95f15203227213b9497b0a7d4ef0be7fca61753ec3941eb415ac402f36563523
Deleted: sha256:561083788ac4daee009e2d547eb01804405297572133247171981981eb405d8c
Deleted: sha256:cd6e906d3c16a4c7122f1bb430e2e1f35c39846f8418f288ffaae6d32ddce753
Deleted: sha256:e36d70bea51477a7d86ba25685de74b79f8763e71bf3dbe2d124730fcbbe9ef5
Deleted: sha256:c985a11a464fb4e3b98aa8b00f96c2d66ba9e435850001ddf409bcfb81dcf9f5
Deleted: sha256:2bd1a2222589b50b52ff960c3d004829633df61532e7a670a91618cd775f2d47
```