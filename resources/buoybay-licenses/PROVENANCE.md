# DataPlot source study

Source: https://opensource.the-meiers.org/DataPlotClasses_v1.4.5.zip
Version 1.4.5, retrieved 2026-10-31.
SHA-256: `bb595adf055d7613963ca6cc8c8204659cd9760190a1c58276b0091481df3a24`.
The landing page states its source code is public domain and supplied as-is.
The archive contains binary REALbasic class files Figure, Graph, Trace, Legend
and TextLabel, a PDF user guide and example projects. Binary strings from Graph
and Trace were inspected: Graph.Plot overloads accept XY arrays or generated X
coordinates; Trace clones its arrays and parses style strings. Example filenames
confirm logarithmic scales, custom ticks, zoom/scroll, animated data, point
editing, threaded plotting and waveform display. This is source-structure and
embedded-text inspection, not execution of the original projects. The included
PDF was inventoried but not text-extracted in this environment.

PlotKit is an independent implementation with no copied source or binary assets.
It implements linear XY storage, auto-bounds, normalized forward/inverse mapping,
1/2/5 ticks, and line/scatter rendering through Buoy IGraphics. It deliberately
uses explicit classes and methods rather than claiming drop-in DataPlot APIs.

Remaining parity work: Figure/Graph ownership and multiple traces, legends,
titles, configurable colors/styles/markers, logarithmic axes, custom ticks,
interactive point events/editing, zoom/scroll, selection, export workflows and
thread-safe data snapshots. Buoy already provides Canvas input, offscreen Picture
drawing and IGraphics/PDF composition; these are package tasks, not evidence of a
missing graphics primitive. SmoothTrace and contributed zoom/candlestick demos
are separate studies. High-DPI rendering needs native manual QA; this package
uses caller coordinate units and makes no verified cross-platform visual claim.
