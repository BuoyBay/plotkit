# DataPlot study

A damped sine-wave Canvas example consuming [PlotKit](../../../README.md).
Source archive inspection and parity gaps are recorded in the package's
[provenance](../../../PROVENANCE.md). This is an independent
linear plotting study, not a full port of the upstream DataPlot classes.

Install PlotKit in a Buoy consumer project and compile `main.bui` to run the Canvas example. Interactive display sizing depends on the host font and DPI configuration.

For interactive use, install the local `plotkit` dependency from this directory
with bpm, then compile `main.bui -o dataplot` using Buoy and launch the executable.
The example has no mouse editing or zoom controls. Rendering uses IGraphics,
so the same routine can draw onto Picture.Graphics or compatible PDF graphics.
