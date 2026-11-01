---
title: "Linear XY plots"
summary: "Store bounded XY series and draw linear line or scatter plots through IGraphics."
category: "Overview"
order: 0
keywords: ["plotkit", "mathematics", "numerical"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# Linear XY plots

`plotkit` supplies a compact linear plotting model, automatic bounds, coordinate transforms, decimal ticks, and a renderer for any Buoy `IGraphics`. The pure Buoy package bundles no native bridge or upstream artwork.

## Install

Copy `plotkit-0.1.0.buipkg` into the consuming application's `packages/` directory and use `Import plotkit`. The package is independently usable on macOS, Windows, and Linux. It requires no native bridge; rendering in PlotKit still requires a working host graphics surface.

## Scope and provenance

This independent implementation is inspired by Roger Meier's DataPlot Classes. It supplies linear models and drawing rather than drop-in Figure/Graph/Trace classes. Multiple traces, legends, configurable styles, logarithmic axes, custom ticks, interactive editing, zoom, scrolling, and export workflows are not supplied. Graphics runtime availability and display scaling belong to the host application.

## Validation and limits

Series hold at most 100,000 points, each finite and within +/-1e100. Invalid additions reject before mutation. Bounds must increase, stay within that magnitude, and span at least 1e-100. Invalid numerical inputs, Nil models, and invalid rendering dimensions throw `InvalidArgumentException`; invalid point indices use ordinary array bounds behavior. Mutable backing arrays are not exposed.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
