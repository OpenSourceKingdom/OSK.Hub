---
layout: default
section-id: highlights
page-id: storage-service
---

# Storage Service

### References
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Storage_Abstractions-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Storage.Abstractions) | [![GitHub](https://img.shields.io/badge/GitHub-View_Local_Storage-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Storage.Local)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Storage_Abstractions-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Storage.Abstractions) | [![NuGet](https://img.shields.io/badge/NuGet-View_Local_Storage-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Storage.Local)

## Summary

The storage service libraries aims to make a set of APIs that is easily reusable across a wide variety of storage repositories, to include cloud or local options. Storage services provide meta data about the file and the ability to read and parse the data in a file to a desired type, utilizing various serializers (byte, json, yaml, etc.). The main goal is to provide easy access to storage without requiring developers to write custom storage code for every application. Storage services are injected and accessed via dependency injection. 

OSK provides implementation to the following storage services:
- Local

The Local storage service includes extensions for compression and cryptography for the data files being stored and retrieved.