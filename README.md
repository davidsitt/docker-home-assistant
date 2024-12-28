# docker-home-assistant

## Install docker
https://docs.docker.com/engine/install/ubuntu/

## Add the current user to the docker group
usermod -aG docker ${USER}


# Add user to the mqtt container

## login interactively into the mqtt container
docker exec -it mqtt sh

## Add users (it will prompt for password)
mosquitto_passwd -c /mosquitto/config/password USER_NAME

## Update permission for the password file
chmod 0700 /mosquitto/config/password 

## Exit 
exit

## Restart MQTT container
docker restart mqtt



## MQTT
# Add integration
# MQTT
# Enter the information
# Submit



Run the containers   ```docker compose up -d```

Restart the containers ```docker compose restart ```

Show the log of a container ```docker logs zigbee2mqtt```

Run a shell in the container ```docker exec -it mqtt sh```
