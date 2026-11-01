---
title: "Linear XY plots API"
summary: "Public plotkit symbols and numerical contracts."
category: "Reference"
order: 20
keywords: ["plotkit", "API", "reference"]
symbols: ["PlotSeries", "PlotSeries.Add", "PlotSeries.Count", "PlotSeries.X", "PlotSeries.Y", "PlotBounds", "PlotBounds.XMin", "PlotBounds.XMax", "PlotBounds.YMin", "PlotBounds.YMax", "PlotBounds.UnitX", "PlotBounds.UnitY", "PlotBounds.DataX", "PlotBounds.DataY", "FitPlot", "PlotTicks", "DrawPlot"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# API reference

`Import plotkit` exposes these public types and operations.

| Symbol | Behavior |
| --- | --- |
| `PlotSeries.Add(x As Double, y As Double)` | Append a validated point in insertion order. |
| `PlotSeries.Count() As Integer` | Read the number of points. |
| `PlotSeries.X(index) / Y(index) As Double` | Read a zero-based point coordinate without exposing backing arrays. |
| `PlotBounds(xMin, xMax, yMin, yMax)` | Construct immutable validated increasing linear bounds from Doubles. |
| `PlotBounds.XMin() / XMax() / YMin() / YMax() As Double` | Read axis bounds. |
| `PlotBounds.UnitX(x) / UnitY(y) As Double` | Map finite bounded data values to normalized coordinates; outside data can produce coordinates outside 0..1. |
| `PlotBounds.DataX(unit) / DataY(unit) As Double` | Map a normalized Double in 0..1 back into data coordinates. |
| `FitPlot(series As PlotSeries) As PlotBounds` | Fit extrema, expand constant axes, or return 0..1 axes for an empty series. |
| `PlotTicks(minimum, maximum, target As Integer = 6) As Array Of Double` | Produce bounded increasing decimal 1/2/5 tick positions. |
| `DrawPlot(g As IGraphics, series, bounds, left, top, width, height, scatter As Boolean = False)` | Render line segments or point markers while preserving caller graphics state. |

## Numerical behavior

FitPlot uses exact extrema, expanding constant or extremely narrow axes by the larger of 1 or 5 percent of their magnitude; an empty series uses 0..1 axes. UnitX/UnitY normalize data without inverting Y; DataX/DataY accept coordinates in 0..1. PlotTicks uses decimal 1/2/5 spacing, targets 2..20 ticks, and returns at most 100 increasing positions. DrawPlot saves and restores graphics state, draws one blue trace on a white background, and requires width 100..100000 and height 80..100000. Out-of-bounds points are skipped and break the trace; segments with outside endpoints are not clipped geometrically into view. Long ordinary numeric labels may overlap.

## Errors and ownership

Series hold at most 100,000 points, each finite and within +/-1e100. Invalid additions reject before mutation. Bounds must increase, stay within that magnitude, and span at least 1e-100. Invalid numerical inputs, Nil models, and invalid rendering dimensions throw `InvalidArgumentException`; invalid point indices use ordinary array bounds behavior. Mutable backing arrays are not exposed.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)


[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
