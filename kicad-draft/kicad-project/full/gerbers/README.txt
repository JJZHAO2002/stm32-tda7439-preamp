Gerber export instructions and produced files placeholder

After completing routing in KiCad PCBNew use File -> Plot to export Gerber files with these layers:
- F.Cu, B.Cu, F.SilkS, B.SilkS, F.Mask, B.Mask, Edge.Cuts
- Internal planes: GND (L2) and PWR (L3) will be output as copper pour Gerbers

Drill output: use File -> Fabrication Outputs -> Drill Files (Excellon)

This folder will contain generated Gerber files when export is run locally or in CI.
