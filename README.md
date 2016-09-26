# docker-reg-gc
The Docker Registry Garbage Collector is a small script which allows you to clean up your registry.

# Dependencies
On the machine where the script is running, should be installed the following components:
- curl
- jq
- awk

# Howto use

1. Befor you can run the script, please change the value of the variable `DOCKER_REGISTRY` to your registry url and make the script runable (chmod 775). You can add a `LIVINGDAYS` parameter, but don't need to. The default for this parameter is 150 Days. Than just call the script: `./docker-reg-gc.sh (LIVINGDAYS)`
It is using API calls and soft-removes all older images from your registry 
2. Add a cronjob to your registryserver which calls the docker registry garbagecollector itself `docker exec -it "${REGISTRY_CONTAINER_ID}" bin/registry garbage-collect "${REGISTRY_CONFIG}"` That will clean up the files from your docker registry filesystem.
