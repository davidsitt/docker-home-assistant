# docker-home-assistant

* Tried on an Ubuntu 24.04.1 LTS and a Raspberry Pi Bookworm.
* For ZigBee, I used the [SONOFF TI CC265P](https://sonoff.tech/product/gateway-and-sensors/sonoff-zigbee-3-0-usb-dongle-plus-e/), worked out of the box on both. 


## Install docker

* Follow : https://docs.docker.com/engine/install/ubuntu/

* On the Pi, I had to add the current user to the docker group
```usermod -aG docker ${USER}```

## Start the containers
* ```docker compose up -d```


## Add user to the mqtt container

* Login interactively into the mqtt container
```docker exec -it mqtt sh```

* Add users (it will prompt for password)
```mosquitto_passwd -c /mosquitto/config/password USER_NAME```

* Update permission for the password file
```chmod 0700 /mosquitto/config/password```

* Exit 
```exit```

* Restart MQTT container
```docker restart mqtt```

## Add user to Zigbee2MQTT
* ```nano zigbee2mqtt/configuration.yaml```
* Update user and password for MQTT
* Restart the containers ```docker compose restart```


## Add MQTT in Home Assistant
* Go to http://raspberry.local:8123 or http://XXX.XXX.XXX.XXX:8123
* Create your home
* Add integration -> MQTT
* Enter the connection information
* Submit


## Access Zigbee2MQTT frontend
http://raspberry.local:8080 or http://XXX.XXX.XXX.XXX:8080


## Useful commands
* Show the log of a container ```docker logs zigbee2mqtt```
* Run a shell in the container ```docker exec -it mqtt sh```
