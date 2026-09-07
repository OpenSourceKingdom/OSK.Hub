---
layout: default
section-id: petra
page-id: dependency-injection
---

# Dependency Injection

### References
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Dependency_Injection-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.DependencyInjection) [![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Extensions-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Extensions.Petra.Godot/tree/main/src/OSK.Extensions.Petra.Godot.DependencyInjection)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Framework-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.DependencyInjection) [![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Extensions-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Extensions.Petra.Godot.DependencyInjection)

## Summary

Dependency injection is an extremely useful tool that helps to manage not only the lifetime of services that are being requested by the application, but also to construct and create the service instances that are used throughout a system. For these reasons and the desire to have the ability to use standard .NET dependency containers in a game engine, Petra DI was created.

Petra provides access to a specially designed `IGameServiceProvider`, which is an `IServiceProvider`. A game service provider differs from a standard service provider in that it allows inheriting a parent service provider's services in cases where the child doesn't have services registered. This helps in certain scenarios where the expectation of game configuration might be globally setup and then reused throughout multiple levels. So, a parent global scene can generate a child scene and reuse its services within the child. In this way, a game module can generate a new game entity and expect that the game entity is able to reference the same services it has. This allows multiple objects to reuse the same service logic from the module.

The library also provides an `Inject` attribute, which can be used on properties to inform the Petra framework that the property expects to have its value injected at the start of the game runtime or when the game entity is created.

There is an extensions library that allows adding node dependencies to a DI container.