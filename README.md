# Get started with Pebble Tracker (for developers)

Pebble Tracker is a multi-sensor **IoT data oracle** that uses a tamper-proof secure element to convert real world phenomena into **verifiable, blockchain-ready data**.

This repository is intended for developers who want to get started with pebble tracker and take advantage of the verifiable IoT data into their decentralized applications. The image below shows the components required for the simplest verifiable data flow, from Pebble Tracker to a smart contract: 

![image](https://user-images.githubusercontent.com/11096047/114433787-85761080-9bc2-11eb-9fb6-d1a2540ab58e.png)

Let's examine these components one by one:

## Pebble Tracker
Pebble Tracker is the source of verifiable data: it provides a stream of data points over MQTT, where each data point includes all the readings from the integrated sensors, plus an ECC signature of the data message itself that is securely computed inside a secure element integrated in the device. By checking this signature at any time, anyone can verify both the source and the integrity of the data point. [Read more about Pebble Tracker in the documentation](https://docs.iotex.io/developer/hardware/pebble.html).

While you can get a real Pebble on [crowdsupply.com](https://www.crowdsupply.com/iotex/pebble-tracker), you can get just *simulate* any number of devices by using the _Pebble Tracker Simulator_ script provided in the [pebble-simulator repository](https://github.com/iotexproject/pebble-simulator) **TODO: Make this public asap**.
