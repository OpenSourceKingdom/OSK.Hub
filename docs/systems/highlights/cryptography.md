---
layout: default
section-id: highlights
page-id: Cryptography
---

# Cryptography

### References
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Cryptography-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Security.Cryptography) [![GitHub](https://img.shields.io/badge/GitHub-View_Aes-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Security.Cryptography.Aes) [![GitHub](https://img.shields.io/badge/GitHub-View_Rsa-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Security.Cryptography.Rsa)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-Cryptography-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Security.Cryptography) [![NuGet](https://img.shields.io/badge/NuGet-Aes-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Security.Cryptography.Aes) [![NuGet](https://img.shields.io/badge/NuGet-Rsa-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Security.Cryptography.Rsa)

## Summary

The cryptography libraries aim to make using encryption and decryption as seamless as possible within dependency containers. Security keys are generated using required key information and then provides access to getting what is the public, shareable information for decryption to process across a network. Utilizing the `ICryptographicKeyServiceProvider` from the core library, consumers only need to provide the required key information for their security method of choice and will then get access to APIs, to encrypt, decrypt, sign, and verify data.

Rsa and Aes security keys are implemented, and future plans to support Lattice cryptography are being considered. Custom security implementations can be registered utilizing the core libraries dependency extensions for security keys.