---
layout: default
section-id: highlights
page-id: Outputs
---

# Outputs

### References
<div style="display:table"><em>*Source*:</em> [![GitHub](https://img.shields.io/badge/GitHub-View_Outputs-black?style=flat&logo=github)](https://github.com/OpenSourceKingdom/OSK.Operations.Outputs)</div>

<div style="display:table"><em>*Packages*:</em> [![NuGet](https://img.shields.io/badge/NuGet-View_Outputs-blue?style=flat&logo=nuget)](https://www.nuget.org/packages/OSK.Operations.Outputs)</div>

## Summary

This library provides an implementation to the [result pattern](https://medium.com/@aseem2372005/the-result-pattern-in-c-a-smarter-way-to-handle-errors-c6dee28a0ef0), using a semantic known as `Output`. The terminology in the library is aimed at responses from functions/methods in a project, but there are helpers and conversions for HTTP status codes over a network. The main goal is to provide easy access to a way to give more details about the output of a given function than merely true/false (out style parameters) or exception based error handling. Utilizing the result pattern, developers can provide richer data to applications when receiving error or success outputs.

Outputs come in few different ways:
`Output`: a simple, single output for a function
`MultiOutput`: a container of multiple outputs for a function
`PaginatedOutput`: an output that represents a page of data for a list style response

Outputs are capable of masking as other types of outputs, to make bubbling error responses easier, and there are generic overloads to each.

The main accessor for generating outputs is the `Out` factory that provides quick access to generate various outputs of a known status code, or custom codes if required.

Outputs also can include diagnostic related data for runtime performance checking or similar validation.
