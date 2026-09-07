---
layout: default
section-id: petra
page-id: probability
---

# Probabilities

### Links
*Source*: [![GitHub](https://img.shields.io/badge/GitHub-View_Probabilities-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Petra.Probabilities)

*Packages*: [![NuGet](https://img.shields.io/badge/NuGet-View_Probabilities-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Petra.Probabilities)

## Summary

Provides the ability to handle RNG in a game through various random number generation methods. The central point is the `IProbabilityRoller` to handle probability and random checks. To setup and configure a roller with the dependency container, use `AddProbabilities`. Additionally, a static factory class is available through `Probability` to create rollers independent of any DI containers or where such use cases are not viable for an application.

Proabilities allows for seeded or non-seeded style RNGs, depending on needs; i.e. you can restore the RNG state easily and continue generating where you left off (saving/loading RNG state from a file perhaps)