# Build XY plots with transforms, ticks and drawing models

Focused linear XY plotting with no native dependencies. `Import plotkit` exposes `PlotSeries`,
`PlotBounds`, `FitPlot`, `PlotTicks` and `DrawPlot`. No native bridge or upstream
artwork is bundled. Inspired by [Roger Meier's DataPlot Classes](https://opensource.the-meiers.org/).

`PlotSeries.Add(x,y)` stores a validated point; `Count()`, `X(i)` and `Y(i)` read
points. The series preserves insertion order, supports at most 100,000 points and
accepts finite values within ±1e100. There are no mutable array aliases. Invalid
points reject before mutation.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add plotkit --git https://github.com/BuoyBay/plotkit.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

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

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer plotkit
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
