---
layout: default
section-id: highlights
page-id: Workflows
---

# Outputs

### Links
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Workflows-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Operations.Workflows)[![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Workflows-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Operations.Workflows)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Workflows-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Operations.Workflows)[![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Workflows-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Operations.Workflows)

## Summary

Workflows is a project that allows running one or more long-running operations together and provides a mechanism to manage it. Think of it similar to managing multiple images in docker being downloaded at the same time, or similar. The main goal is to be able to handle asynchronous style tasks in a system that does not inherently supported it (e.g. game engines). In some scenarios, it is better to handle the operations across multiple frames, using synchronous style step updates. This is where Workflows positions itself to help.

The library provides a task manager, workflow runner, and more to manage handling multiple long running tasks across multiple frames in a game engine. It also is setup to be configurable so that some tasks must wait for others to complete (queue systems).