---
layout: default
section-id: petra
page-id: Provisions
---

# Provisions

### References
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Petra_Provisions-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Provisions) | [![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Provisions-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Provisions)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Petra_Provisions-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Provisions) | [![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Provisions-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Provisions)

## Summary

Every game requires the ability to manage player resources and transfer them between transactions. Provisions is meant to provide shared logic to handle these transactions for game applications, and provide easy ways to manage and validate a transaction. These transactions can encompass gold for items, mana for magic, or any other style of "need x resource to do y thing".

The core component is the `ProvisionCalculator` which is able to perform these calculations and return various Provision expenditure results for a given set of in-game resources. Additionally, it's able to calculate refunds for transactions, while taking into account potential discounts or other desired reductions.

Furthermore, a `ProvisionSet` can be utilized to handle multiple different provisions simultaneously. Essentially acting as a resource bank, provision sets can be used to compare player economies, purchases or transactions spanning multiple provisions at once (e.g. gold, lumber, etc.), and more.

### Godot Integration

The godot provision integration serves primarily as a shared data configuration library for provisions that can be used within a godot game application. The following are key components to the integration library:
- `ProvisionDefinition`: Defines a provision type. For example, Gold. This allows reusing the same definition across multiple game entities when configuring a scene, and configuring a provision type in a single place. Allows configuring icons, descriptions, etc. for definition data that can be referenced in-game
- `ProvisionResource`: Utilized as a resource to specify a provision for a game entity. For example, you can set an array of provisions for a barracks entity that takes 100 gold, 25 lumber, etc. This references a definition for reusing known definitions across multiple provisions of the same type
- `ProvisionDefinitioRepository`: Provides the ability to add a set of provision definitions to an in-game manager so that it can be included as a node in the DI container. This may be desired in some cases during runtime where you want to get the information from a shared provision definition, but don't immediately have access to it.

In order for the definition repository to function, users will need to:
- Add the repository to a game scene (global or not) and configure it with the definition resources needed
- Add the repository to the DI chain. If using the Petra DI setup, you can utilize the extensions to add a node for the interface or the class directly