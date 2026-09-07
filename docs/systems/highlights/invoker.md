---
layout: default
section-id: highlights
page-id: Invoker
---

# Invoker

### References
<div style="display:table"><em>*Source*:</em> [![GitHub](https://img.shields.io/badge/GitHub-View_Invoker-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Expressions.Invoker)</div>

<div style="display:table"><em>*Packages*:</em> [![NuGet](https://img.shields.io/badge/NuGet-View_Invoker-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Expressions.Invoker)</div>

## Summary

This library aims to make execution of functions on objects highly performant and easy as possible. In certain scenarios this is highly beneficial, for example, in a case where dependency injection is used to create a generic service at runtime and pass in required parameter information, execution can be slow. See an example from an inputs library use case:
```
                var invoker = InvokerFactory.CreateInvoker(definitionType, method);

                definitionBuilder.WithAction(new InputAction(inputActionName,
                    inputActionAttribute?.TriggerPhases.ToHashSet() ?? [InputPhase.Start],
                    inputEventContext => invoker.FastInvoke(inputEventContext.Services.GetRequiredService(definitionType), [inputEventContext]),
                    inputActionAttribute?.Description, inputActionAttribute?.InternalActionGroup));
```

The invoker is able to achieve performance near to that of executing a method directly on a known type, due to the usage of compiled expressions.