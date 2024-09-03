# Mqtt
Message Query Telementary Transport (MQTT) is a lightweight publication/subscription model type (pub/sub) messaging model
Work on top of TCP/IP model
- Publisher
    Collect data and send info to subscriber via broker
- Broker
    Ensure security by cross checking authorization of publisher and subscriber
- Subsciber
    The device to with the data is send
- Quality of Service
    - QOS0: (At most one) Least reliable but the fastest. publicstion is sent but verification is not received
    - QOS1: (At least one) Ensures that the meassage is sent at least once, but duplicated may be received
    - QOS2: (Exactaly one) Most reliable mode but consumes the most bandwidth. 
        Duplicate are controlled to ensure that the message is delivered only once
- advantage
    - minimum bandwidth use 
    - opeartion over wireless networks
    - low energy consumption 
    - good reliability if neccesary 
    - little process and memory resources 
# Concepts
- Publish - Subscribe
----
A device can publish a message on a topic or it can be subscribed to a particular topic to receive meassage

- Message: these are information that you want to exchange between the devices.
- Topics: are the way you register interest for incoming message or how you specify where to display the message.
    example : /home/topic/load
- Broker
---
It is responsible for recieving, transfering, filtering message and who is interested in them and publish the meassafe to all subscriber.
  
