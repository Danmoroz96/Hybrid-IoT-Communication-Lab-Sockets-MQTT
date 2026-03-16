# Hybrid-IoT-Communication-Lab-Sockets-MQTT
In this lab series I built a small IoT communication pipeline using two laptops.  The system simulates:  a sensor node, an edge device, a cloud/server application. The communication technologies used are:  Socket Programming, MQTT Messaging

# IoT Communication Pipeline: Sockets to MQTT

This project demonstrates a three-tier IoT architecture simulating a sensor node, an edge device, and a cloud application.

## 🏗 System Architecture

The following diagram illustrates how data moves from the local sensor to the cloud:

```mermaid.js
graph LR
    subgraph "Laptop 1 (Sensor Node)"
    A[socket_sensor.py]
    end

    subgraph "Laptop 2 (Edge Device)"
    B[edge_device.py]
    end

    subgraph "Cloud / Broker"
    C((broker.emqx.io))
    end

    subgraph "Laptop 1 (Cloud App)"
    D[mqtt_subscriber.py]
    end

    A -- "Socket (Port 5005)" --> B
    B -- "MQTT (Port 1883)" --> C
    C -- "Subscribe" --> D
```


Lab Configuration



Laptop 1 IP is 192.168.89.x (Client) or I used 0.0.0.0  or you can use Mobile Hotspot (Galaxy)


Laptop 2 IP (Edge) 192.168.89.175 (or 192.168.123.175) 


Socket Port 5000 

MQTT Brokerbroker.emqx.io

MQTT Topic   savonia/iot/temperature

![Screenshot 2026-03-16 212835](https://github.com/user-attachments/assets/89f98be5-135e-46ae-928f-7f9c0e893490)

![Screenshot 2026-03-16 212851](https://github.com/user-attachments/assets/3f0ee1f2-faa1-4317-885c-d8ea345bbc86)

![Screenshot 2026-03-16 213040](https://github.com/user-attachments/assets/a3472b37-0a26-4a17-b5e5-55e2722b14e0)

![Screenshot 2026-03-16 213119](https://github.com/user-attachments/assets/2b56d882-7c99-4af8-b1c7-37ee9ce0bcf9)

![Screenshot 2026-03-16 213134](https://github.com/user-attachments/assets/1af1664a-83f0-4008-af60-ab9ec165a74d)

![Screenshot 2026-03-16 213207](https://github.com/user-attachments/assets/aee1d649-eadc-4a02-bc66-c374cc3b4348)

![Screenshot 2026-03-16 214509](https://github.com/user-attachments/assets/5290ad44-1ff0-4de9-8954-48eb919b37ae)

![Screenshot 2026-03-16 214525](https://github.com/user-attachments/assets/08ca1bfa-4764-423a-97ed-96036dfe4026)



Execution Order
Laptop 1: Run subscriber.py

Laptop 2: Run edge_device.py

Laptop 1: Run socket_sensor.py



Lab 1: Sensor to Edge (Socket Programming)
Objective: Direct communication between two devices.

Run: socket_server.py on Laptop 2, then socket_sensor.py on Laptop 1.

Lab 2: Edge to Cloud (MQTT)
Objective: Implement MQTT messaging to forward data to a global broker.

Run: subscriber.py on Laptop 1, then publisher.py on Laptop 2.

Lab 3: Full IoT Pipeline (Integration)
Objective: Combine both systems into a complete bridge.

Run: edge_device.py on Laptop 2 to catch socket data and push it to the cloud.

Before that Install the Paho MQTT library on both devices:

pip install paho-mqtt




