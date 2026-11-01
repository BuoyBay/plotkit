# DataPlot study

A damped sine-wave Canvas example consuming [PlotKit](../../../libraries/plotkit/README.md).
Source archive inspection and parity gaps are recorded in the package's
[provenance](../../../libraries/plotkit/PROVENANCE.md). This is an independent
linear plotting study, not a full port of the upstream DataPlot classes.

From the repository root, run:

```sh
LD_LIBRARY_PATH=/tmp/buoy-chatui-jpeg8/build python3 tests/meier_dataplot_verify.py
```

This development host needs the existing temporary JPEG8 compatibility library
for programs linked with Buoy drawing support. On a correctly provisioned host,
run without that environment override. The runner performs 18 compiler checks
(package, model/raster test and GUI source on six desktop targets), executes
sealed-package tests, and builds the GUI in a temporary source tree. Tests cover
bounds fitting, 2,002 coordinate roundtrips, decimal ticks, invalid input and
actual offscreen blue pixels. Interactive window appearance and Hi-DPI behavior
have not been visually verified.

For interactive use, install the local `plotkit` dependency from this directory
with bpm, then compile `main.bui -o dataplot` using Buoy and launch the executable.
The example has no mouse editing or zoom controls. Rendering uses IGraphics,
so the same routine can draw onto Picture.Graphics or compatible PDF graphics.
