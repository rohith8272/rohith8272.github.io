# mavQT

**mavQT** is a lightweight tool to connect **MAVLink-enabled drones** to **IoT systems** via MQTT. It allows you to receive, display, and forward MAVLink messages in real time to an MQTT broker.

---

## Features

- Connect to **UDP/TCP MAVLink streams** from drones.
- Subscribe and publish MQTT topics with **custom QoS levels**.
---

## Installation and setup
1. Clone the repository to the project here: https://github.com/rohith8272/mavQT
2. In your favorite code editor, setup a virtual env and install the required packages from requirements.txt
3. Run the mavQT tool:
```
python -m mavQT
```


## Setting up the broker
1. We first need to start a MQTT broker to send out converted MAVLink packets. There are several online brokers available but in this tutorial we will use mosquitto.(https://mosquitto.org/download/)
2. Once the broker is installed on your system, navigate to the root directory. Here you will find the executable "mosquitto.exe".
3. We need to setup a few parameters for the broker by making a configuration file. Here's an example that you can try (save it as sample.conf).
```
# Default listener (local + remote)
listener 1883 0.0.0.0

# Allow anonymous connections 
allow_anonymous true

# (Optional) persistence
persistence true
persistence_location mosquitto/
```
4.To start the broker, you can run the following cmd:
```
mosquitto.exe -c "sample.conf" -v
```
The broker should now be listening on port 1883.

## Forwarding MAVLink stream
1. On mission planner, set UDP, outbound on port 14550.
   
2. Alternatively you can use mavproxy:
```
mavproxy --master=tcp:127.0.0.1:5760 --out 127.0.0.1:14550
```
You can find more information about MAVLink routing here:https://dronesim.gitbook.io/dronesim-docs/development-tutorials/forwarding-mavlink-packets

## Testing mavQT
- connect to your MQTT broker IP/port
- Subscribe and publish MQTT topics with **custom QoS levels**.




