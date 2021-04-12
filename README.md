# Get started with Pebble Tracker (for developers)

Pebble Tracker is a multi-sensor **IoT data oracle** that uses a tamper-proof secure element to convert real world phenomena into **verifiable, blockchain-ready data**.

This repository is intended for developers who want to get started with pebble tracker and take advantage of the verifiable IoT data into their decentralized applications. The image below shows the components required for the simplest verifiable data flow, from Pebble Tracker to a smart contract: 

![image](https://user-images.githubusercontent.com/11096047/114436672-e81cdb80-9bc5-11eb-9de4-32551aa22ef2.png)


Let's examine these components one by one:

## Pebble Tracker
Pebble Tracker is the source of verifiable data: it provides a stream of data points over MQTT, where each data point includes all the readings from the integrated sensors, plus an ECC signature of the data message itself that is securely computed inside a secure element integrated in the device. By checking this signature at any time, anyone can verify both the source and the integrity of the data point. [Read more about Pebble Tracker in the documentation](https://docs.iotex.io/developer/hardware/pebble.html).

While you can get a real Pebble on [crowdsupply.com](https://www.crowdsupply.com/iotex/pebble-tracker), you can get just *simulate* any number of devices by using the _Pebble Tracker Simulator_ script provided in the [pebble-simulator repository](https://github.com/iotexproject/pebble-simulator) **TODO: Make this public asap**.

## Backend
As Pebble Tracker produces and transmits data messages over the MQTT protocol, you will need an MQTT broker to receive these messages and possibly an objects storage system for data storage. While this component can be [configured using one of the available IoT cloud services](https://docs.iotex.io/developer/hardware/pebble-aws-configuration.html) on the market, we also provide a [dockerized service made out of open source tools](https://github.com/iotexproject/pebble-backend) like [hmq](https://github.com/fhmq/hmq) and [min.io](min.io) that you can easily configure and run as a backend for receiving your devices data messages.

## Data Relayer
The data relayer is a small piece of software in charge of fetching the data points received by the backend and forward them to the smart contracts that will actually make use of the data by first verifying integrity and device authorizations, then triggering required actions depending on the dApp logic. In this context, the Relayer will use the [min.io API](https://docs.min.io/docs/javascript-client-api-reference.html) on one side to access the data stored in the backend, and the [IoTeX SDK](https://docs.iotex.io/developer/sdk/overview.html) on the other side to forward the data points to the smart relevant contracts.

## Smart Contracts
