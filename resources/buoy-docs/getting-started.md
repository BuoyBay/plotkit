---
title: "Linear XY plots getting started"
summary: "Use plotkit with a complete example and explicit numerical conventions."
category: "Guides"
order: 10
keywords: ["plotkit", "example", "import"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

## Prepare the package

Place the sealed `plotkit-0.1.0.buipkg` archive in your project's `packages/` directory. The example imports the package by its manifest name and uses explicit methods.

## First use

Append points to `PlotSeries` in their desired line order. Obtain bounds with `FitPlot`, or construct explicit increasing bounds. Pass an existing Canvas paint surface or an offscreen Picture graphics surface to `DrawPlot`; retain the series and bounds in your own application model.

```buoy
Import plotkit

Sub Main()
    Dim series As New PlotSeries()
    series.Add(0.0, 1.0)
    series.Add(1.0, 3.0)
    series.Add(2.0, 2.0)
    Dim bounds As PlotBounds = FitPlot(series)
    Dim image As New Picture(320, 200)
    DrawPlot(image.Graphics, series, bounds, 0.0, 0.0, 320.0, 200.0)
    Print series.Count()
    Print bounds.UnitX(1.0)
End Sub
```

## Conventions

FitPlot uses exact extrema, expanding constant or extremely narrow axes by the larger of 1 or 5 percent of their magnitude; an empty series uses 0..1 axes. UnitX/UnitY normalize data without inverting Y; DataX/DataY accept coordinates in 0..1. PlotTicks uses decimal 1/2/5 spacing, targets 2..20 ticks, and returns at most 100 increasing positions. DrawPlot saves and restores graphics state, draws one blue trace on a white background, and requires width 100..100000 and height 80..100000. Out-of-bounds points are skipped and break the trace; segments with outside endpoints are not clipped geometrically into view. Long ordinary numeric labels may overlap.

## Handle invalid inputs

Series hold at most 100,000 points, each finite and within +/-1e100. Invalid additions reject before mutation. Bounds must increase, stay within that magnitude, and span at least 1e-100. Invalid numerical inputs, Nil models, and invalid rendering dimensions throw `InvalidArgumentException`; invalid point indices use ordinary array bounds behavior. Mutable backing arrays are not exposed.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
