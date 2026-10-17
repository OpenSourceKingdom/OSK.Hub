---
layout: default
section-id: petra
page-id: Acquisition
---

# Acquisition

### Links
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Petra_Acquisition-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Acquisition) [![GitHub](https://img.shields.io/badge/GitHub-View_Godot_Acquisition-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Godot.Acquisition)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Petra_Acquisition-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Acquisition) [![NuGet](https://img.shields.io/badge/NuGet-View_Godot_Acquisition-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Godot.Acquisition)

## Summary

Acquisitions encompasses anything that can be acquired, or obtained. This can include a variety of uses, from purchasing an item in a shop, to queuing multiple infantry units, to tracking upgrade unlocks (level 1, 2, ..), and even including tech trees of hundreds of choices.

The core concept is that of an `AcquisitionHub` returning requests for an acquisition list to an `IAcquirer`. A hub is simply a focal point for acquisitions to be processed and retrieved. Each hub presents a list of `IAcquisitionDefinition` to the core system, which then will determine if the acquisition is a single choice or a multi-choice path. Whatever the case, acquisitions are returned to an acquirer whom is requesting an `IAcquisitionView`. The view is a tailored catalog of acquisitions available to a given acquirer at the time the view is returned. This view is generated from an acquisition mechanism that allows validating choices and path against the acquirer for various requirements and costs. Acquirers are flexible to be either the entire player or an individual character. This allows for supporting scenarios where a character has certain items or abilities and can adjust the cost or availability of an item based on the specific acquirer requesting the page of acquisition choices. Each hub and choice has a configuration that can impact how long it takes to acquire, pricing information, queue limits, and more.

The core `IAcquisitionSystem` needs to be updated per frame but it manages acquisitions of all the hubs that have been used with it.


### Godot 

A Godot integration exists and helps to configure the choices that a hub possesses, along with how it functions in the application. 