---
title: "plotkit typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["PlotBounds", "PlotSeries"]
dependencies: []
symbols: ["PlotBounds", "PlotSeries"]
related: ["api.md", "getting-started.md", "index.md"]
---

# plotkit typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## PlotSeries

`Public Class PlotSeries`

One bounded, ordered XY series. Does not expose mutable storage.

### Add

`Public Sub Add(x As Double, y As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |

Returns: no value.

### Count

`Public Function Count() As Integer`

No parameters.

#### Returns

| Type |
| --- |
| `Integer` |

### X

`Public Function X(index As Integer) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `index` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### Y

`Public Function Y(index As Integer) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `index` | `Integer` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

## PlotBounds

`Public Class PlotBounds`

Immutable linear axis bounds with invertible normalized coordinates.

### Constructor

`Public Sub Constructor(xMin As Double, xMax As Double, yMin As Double, yMax As Double)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `xMin` | `Double` | `ByVal` | Required |
| `xMax` | `Double` | `ByVal` | Required |
| `yMin` | `Double` | `ByVal` | Required |
| `yMax` | `Double` | `ByVal` | Required |

Returns: no value.

### XMin

`Public Function XMin() As Double`

No parameters.

#### Returns

| Type |
| --- |
| `Double` |

### XMax

`Public Function XMax() As Double`

No parameters.

#### Returns

| Type |
| --- |
| `Double` |

### YMin

`Public Function YMin() As Double`

No parameters.

#### Returns

| Type |
| --- |
| `Double` |

### YMax

`Public Function YMax() As Double`

No parameters.

#### Returns

| Type |
| --- |
| `Double` |

### UnitX

`Public Function UnitX(x As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `x` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### UnitY

`Public Function UnitY(y As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `y` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### DataX

`Public Function DataX(unit As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `unit` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

### DataY

`Public Function DataY(unit As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `unit` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |

## PlotKit functions

### FitPlot

`Public Function FitPlot(series As PlotSeries) As PlotBounds`

Empty series uses 0..1; constant data expands by max(1, abs(value)*0.05).

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `series` | `PlotSeries` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `PlotBounds` |

### PlotTicks

`Public Function PlotTicks(minimum As Double, maximum As Double, target As Integer = 6) As Array Of Double`

Bounded 1/2/5 decimal tick spacing, maximum 100 ticks.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `minimum` | `Double` | `ByVal` | Required |
| `maximum` | `Double` | `ByVal` | Required |
| `target` | `Integer` | `ByVal` | `6` |

#### Returns

| Type |
| --- |
| `Array Of Double` |

### DrawPlot

`Public Sub DrawPlot(g As IGraphics, series As PlotSeries, bounds As PlotBounds, left As Double, top As Double, width As Double, height As Double, scatter As Boolean = False)`

Draw a linear plot into a caller-owned drawing surface; preserves state.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `series` | `PlotSeries` | `ByVal` | Required |
| `bounds` | `PlotBounds` | `ByVal` | Required |
| `left` | `Double` | `ByVal` | Required |
| `top` | `Double` | `ByVal` | Required |
| `width` | `Double` | `ByVal` | Required |
| `height` | `Double` | `ByVal` | Required |
| `scatter` | `Boolean` | `ByVal` | `False` |

Returns: no value.
