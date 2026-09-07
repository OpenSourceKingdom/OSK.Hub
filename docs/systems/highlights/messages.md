---
layout: default
section-id: highlights
page-id: Messages
---

# Messages

### References
<div style="display:table"><em>*Source*:</em> [![GitHub](https://img.shields.io/badge/GitHub-View_Messages-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Messages)</div>

<div style="display:table"><em>*Packages*:</em> [![NuGet](https://img.shields.io/badge/NuGet-View_Message_Abstractions-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Messages.Abstractions) | [![NuGet](https://img.shields.io/badge/NuGet-View_Messaging-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Messages.Messaging) | [![NuGet](https://img.shields.io/badge/NuGet-View_Messenger_Pigeons-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Messages.Couriers.Pigeons)</div>

## Summary

This set of libraries aims to make the process of transmitting, publishing, receiving, and distributing messages (or events) in an application as easy as possible. The system is divided into the following parts:
- Dispatcher
- Courier
- Message Center/Message Box

Each part acts as a part of a pipeline and handles an individual responsibility in the message transmission process. 
- Dispatchers are responsible for queueing the message to be sent from a courier, and provide a mechanism to send the message across a single or multiple couriers. 
- Couriers handle the publishing and travel care of a message, ensuring a message is delivered to a message center. That is, the courier is expected to ensure the message is delivered to a respective service that is listening to a message center
- Message Centers collect and then distribute the received messages to the expected recipient message boxes. A message center can send a received message to a single box or fan it out to multiple. Once a message box receives a message, it is on the recipient to process the message and handle whatever the expected instruction demands.

OSK provides implementation for the following couriers:
- EasyNetQ: A RabbitMQ courier that uses EasyNetQ as the main API for connecting with the RabbitMQ server
- Pigeons: A courier that is specialized to running on local machines, that is the message is intended to act within the local system only
