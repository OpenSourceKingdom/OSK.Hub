---
layout: default
section-id: petra
page-id: Modules
---

# Modules

### References
<div class="refs">*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Petra_Modules-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Modules) [![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Modules-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Modules)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Petra_Modules-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Modules) [![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Modules-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Modules)</div>

## Summary

Within Petra, a module is considered an isolated scene, game object, or entity. It is essentially a level, or similar asset, that can be created, updated, and deleted independent of other modules. There are two types of modules: `IModule` and an `IServiceModule`. IModule is a basic game entity that mostly serves as a marker and reference for other game entities that might need it. The real enhancement comes from the inclusion of the dependency injection library which is used to help generate a mostly isolated `IServiceProvider` for the module. This allows the module to share game services within itself for any game entities that ask for it.

### Godot Integration

The godot integration offers a `GameModuleBootstrapper` tool to help initialize `IServiceModule` instances within Godot's runtime.

A consumer wanting to utilize Petra's built-in capabilities will want to use the `GameModule` or `GameServiceModule` scripts alongside the bootstrapper.