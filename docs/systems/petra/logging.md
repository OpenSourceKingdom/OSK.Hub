w---
layout: default
section-id: petra
page-id: Logging
---

# Logging

### Links
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Petra_Logging-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Logging) [![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Logging-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Logging)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Petra_Logging-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Logging) [![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Logging-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Logging)

## Summary

Logging is a useful tool to provide diagnostic and other information for an application and game engines are no different. In order to utilize standard .NET logging, Petra injects a logger provider that allows for consumers to add in separate `ILogSink` to record a log message. It also provides access to a log collector that can be configured for retaining logs to a certain limit, which can be accessed through dependency injection - `ILogCollector`. This can be useful in scenarios where a game might want event or similar logs to be displayable during runtime.

### Godot Integration

A Godot logging library exists to provide some extra configuration for a Godot logger, but also to add the Godot log sink that the base library will use. The Godot logger can be configured to set custom text color or custom log formats, if defaults are not preferred. Users will only need to add the services through one of the `AddGodotLogging` DI extensions