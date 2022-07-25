Schematic Transcript of TRS-80 Model 100
----------------------------------------

[![CC BY-SA 4.0][cc-by-sa-shield]][cc-by-sa]

This is a transcript of the original schematic found in the TRS-80 Model 100
manual into a machine-readable and libre license format using KiCAD.

This transcript is based on various scans to minimize read errors

  * https://tim.id.au/trs-80-model-100.pdf
  * https://archive.org/details/tandy_100_schematics/page/n11/mode/2up

The format is in KiCAD eeschema format; for convenience, a generated PDF
has been included in this repository.

<a href="https://github.com/hzeller/trs80-100-schematic/raw/main/trs80-100.pdf">
<img src="https://github.com/hzeller/trs80-100-schematic/raw/main/img/thumbnail.png">
</a>

## Status
The main-board schematic is complete (the LCD one has not started yet).
A fine-combed proof-reading and comparison between original and transcript has
yet to be done.

The schematic passes ERC with zero warnings and errors.

## Minimal layout deviation
This transcript in KiCAD attempts to preserve the original layout as much
as possible to easily navigate and compare between the original and the
transcript. However some parts are slightly rearranged to improve readability.

Some readability improvements have been done in the address demultiplexing
section to more easily see the `AD[0..7]` bus being buffered to the AD-bus and
latched to the lower half of the address bus.

A `RDWR` signal and its buffered counterpart `RDWR*` have been introduced.
In the original schematic, the former was not named but generated to feed
the `ENABLE` for the LCD. The `RDWR*` signal existed but was named `Ⓐ*` in
the original schematic which was not a very useful name.

Now, these signals are generated close to the 'bus buffer signal' section, the
`RDRW` section is used as a named signal in the LCD input (which also makes the
section near the LCD connector less crowded). As a result, the buffer
section is also less crowded by using a block symbol as M20 instead of
multiple separate buffer symbols (note, the `RESET_OUT` signal has been
moved to the right of the 80C85 symbol for that).

The RAM and ROM chips in the original hand-drawn schematic in a 'bulk' format.
The individual chips are made explicit in the transcript.

All component designators have been preserved and all pin-assignments
of components are the same as in the original schematic.
Only exception: the pinouts of the resistor networks have not been arranged
yet (but pin numbers are hidden, so it would not make a difference unless a PCB
is made).

Different busses have been color-coded:

  * Green: unbuffered AD bus from the CPU; named with underscore `_AD[0..7]`
  * Magenta: buffered AD bus `AD[0..7]`
  * Orange: Address bus `A[0..15]` (which includes the demultiplexed `A[0..7]`).
  * Blue: Periphery IO lines from 81C55: `PA[0..7]`, `PB[0..1]`.

For labels with a meaning across the schematic that are not part of
a bus, global labels have been used, mostly because they stand out
more nicely than simple labels.

## Designators

Some designators have been deduced by cross-referencing the schematic
and BOM. These need to be verified on the actual PCB.

The 10nF capacitor in the switching power supply section does not have a
designator in the schematic. The C62 designator was extracted from the BOM,
as this designator was the only missing and also had the correct 10nF value
(to be verified on PCB).

The base transistor to T4 is a 10k value with no designator in the schematic.
This is likely R33. For now using a dummy designator R998.

The resistor discharging C78 via T25 has neither a designator nor value in
the schematic. This could be R162 with 100 Ohm. For now using a dummy
designator R999.

### Missing designators

There are a few missing designator numbers, but these have also been missing
in the original BOM. So for completeness, following designators do *not* exist:

  * D3, D19, D25, D26
  * C51, C68, C93, C95, C96
  * R69, R100, R117, R129, R130, R133, R143, R147, R148, R155, R163..R169

## TODO

  * Compare *values* from KiCAD BOM with original BOM.
  * Thorough comb-through to make sure there are no mistakes and
    confirm R33 (Base-resistor for T4?), R162 (reset circuit?) (look at PCB).
  * Fill in details (voltage, tolerance, original part names (many have original
    Radio Shack part-numbers), datasheets if possible) for each component
    from the original BOM.
  * Add footprints to all components that they reflect exactly the original
    components.
  * Add Makefile to create schematic PDF and BOM from eeschema file.

## BUGS

If you see mistakes, please file them in the issue tracker;
https://github.com/hzeller/trs80-100-schematic

## Transcript License CC-BY-SA

The original schematic is copyright of the respective owner (probably Kyocera).

This editable transcript in KiCAD format is licensed by me, Henner Zeller,
under Creative Commons Attribution-ShareAlike CC-BY-SA 4.0 license.

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg
