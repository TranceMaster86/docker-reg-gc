# docker-reg-gc
The Docker Registry Garbage Collector is a small script which allows you to clean up your registry v2.

# Dependencies
On the machine where the script is running, should be installed the following components (tested with given versions):
 - curl 7.29.0
 - jq-1.5
 - Awk 4.0.2

# Howto use

1. Update registry configuration file (config.yml) and restart registry
`storage: delete: enabled: true` or set the ENV `REGISTRY_STORAGE_DELETE_ENABLED=true`
2. Befor you can run the script, please change the value of the variable `DOCKER_REGISTRY` to your registry url and make the script runable (chmod 775). You can add a `LIVINGDAYS` parameter, but don't need to. The default for this parameter is 150 Days. Than just call the script: `./docker-reg-gc.sh (LIVINGDAYS)`
It is using API calls and soft-removes all older images from your registry 
2. Add a cronjob to your registryserver which calls the docker registry garbagecollector itself `docker exec -it "${REGISTRY_CONTAINER_ID}" bin/registry garbage-collect "${REGISTRY_CONFIG}"` That will clean up your docker registry filesystem.
