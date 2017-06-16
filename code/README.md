Docker Registry
===============

### ADD TO LOCAL /etc/hosts FILE THE REGISTRY IP
```sh
$ docker-machine ip docker-registry   # COPY OUTPUT, EXAMPLE --> 192.168.99.100
$ sudo vim /etc/hosts # ADD NEW LINE WITH MACHINE IP AND DOMAIN

Example --> "192.168.99.100  hub.private.dev"
```
--> OPEN A BROWSER AND CHECK REPOSITORIES: http://hub.private.dev:5000/v2/_catalog


### TAG SOME IMAGE
```sh
$ docker tag <image_name> <registry_ip>:<registry_port>/<tag_name>:<tag_version>

Example: docker tag some_image hub.private.dev:5000/my_repo/my_image:prodv1
Example: docker tag some_image hub.private.dev/my_repo/my_image:prodv1 # If proxy is enabled
```


### TAG SOME CONTAINER
```sh
$ docker commit <options> <container_id> <registry_ip>:<registry_port>/<tag_name>:<tag_version>

Example: docker commit c3f279d17e0a  hub.private.dev:5000/my_repo/my_image:prodv1
Example: docker commit c3f279d17e0a  hub.private.dev/my_repo/my_image:prodv1 # If proxy is enabled
```

### LOGIN TO REGISTRY
```sh
$ docker login <registry_ip>:<registry_port>

Example: docker login hub.private.dev:5000
Example: docker login hub.private.dev # If proxy is enabled
```


### AUTHENTICATION
```sh
$ username: admin
$ password: 123456
```


### PUSH CREATED IMAGE
```sh
$ docker push <registry_ip>:<registry_port>/<tag_name>:<tag_version>

Example: docker push hub.private.dev:5000/my_repo/my_image:prodv1
Example: docker push hub.private.dev/my_repo/my_image:prodv1 # If proxy is enabled
```


### LOGOUT FROM REGISTRY
```sh
$ docker logout <registry_ip>:<registry_port>

Example: docker logout hub.private.dev:5000
Example: docker logout hub.private.dev # If proxy is enabled
```


### GENERATE AUTH PROFILES
```sh
$ mkdir auth
$ docker run --entrypoint htpasswd registry:2 -Bbn testuser testpassword > auth/htpasswd
```

