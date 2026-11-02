# PlotKit 0.1.0

Focused linear XY plotting in pure Buoy. `Import plotkit` exposes `PlotSeries`,
`PlotBounds`, `FitPlot`, `PlotTicks` and `DrawPlot`. No native bridge or upstream
artwork is bundled. Inspired by [Roger Meier's DataPlot Classes](https://opensource.the-meiers.org/).

`PlotSeries.Add(x,y)` stores a validated point; `Count()`, `X(i)` and `Y(i)` read
points. The series preserves insertion order, supports at most 100,000 points and
accepts finite values within ±1e100. There are no mutable array aliases. Invalid
points reject before mutation.

`PlotBounds(xMin,xMax,yMin,yMax)` requires increasing finite bounds, magnitude
at most 1e100 and spans at least 1e-100. Getter methods have the corresponding
names. `UnitX/UnitY` map data into normalized coordinates; `DataX/DataY` invert a
coordinate in 0..1. These helpers leave Y-axis screen inversion to callers.
`FitPlot(series)` computes exact extrema, expands constant axes by the larger of
1 or 5% of the value's magnitude, and uses 0..1 axes for an empty series.

`PlotTicks(minimum,maximum,target=6)` chooses decimal 1/2/5 tick spacing. Target
must be 2..20; output contains at most 100 increasing tick positions inside the
range. Floating point tick labels use Buoy's ordinary `String.From` formatting.

`DrawPlot(g,series,bounds,left,top,width,height,scatter=False)` draws axes, numeric
ticks and a blue trace on a white background. It accepts any `IGraphics`, including
Canvas Paint and Picture.Graphics. Width is 100..100000, height 80..100000. Drawing
state is saved/restored even on failure. Scatter mode draws point markers;
otherwise points are connected in insertion order. Points outside the supplied
bounds are skipped and interrupt the trace: segments crossing the viewport with
outside endpoints are not geometrically clipped into view. Use `FitPlot` to
include all points. Long labels may overlap. Only one series is drawn per call;
callers needing overlays should provide their own composed renderer.
