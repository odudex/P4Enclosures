# crowpanel_7

A 3D-printable enclosure for the Kern `crowpanel` device in its 7" version, built on the Elecrow
**CrowPanel Advanced 7" ESP32-P4** (1024×600 touch display, glass, LCD and PCB in one module),
modelled in [SolidCraft](https://github.com/bherbruck/solidcraft). It is one of the enclosures in
[P4Enclosures](../README.md). Kern's `crowpanel` target also covers the 10.1" panel, whose enclosure is in
[crowpanel_101](../crowpanel_101/README.md); both are built the same way.

The construction follows the FreeCAD case for the 10.1" CrowPanel that
[@3rdIteration](https://github.com/3rdIteration) made for Kern. A back case and a front frame clamp
the panel's PCB between them: four M3 screws go through the frame's corner posts and the PCB's corner
holes into standoffs in the case. As in Kern's case, the connectors on the back of the PCB are reached
through openings in the back. The two USB-C ports and the microSD slot open through the side walls,
and the camera looks out the back from a holder.

Work in progress: the case and frame are modelled and exported, and the assembly shows no
interference with the board, but nothing has been print-tested yet. The camera's position is an
estimate: its flex has to fold back to its connector, which the vendor model does not show.

## Files

| File | What it is |
|---|---|
| `crowpanel_7_case.sc` | The printed parts, fully parametric: bodies `Case` and `Frame` |
| `exports/` | `crowpanel_7_case.3mf` (case and frame), `Case.stl`, `Frame.stl` |
| `images/` | `assembly.png`, a render of the assembly from behind |
| `crowpanel_7_enclosure.sc` | Local only. Assembly: board, case and frame in place |
| `crowpanel_7_board.sc` | Local only. Board model, the vendor's STEP file placed in the case's frame |

The two local-only files contain the vendor's board model, so they are not in the repository. The
assembly links both `crowpanel_7_case.sc` and `crowpanel_7_board.sc` by relative path, so keep the
`.sc` files together. The board model has two changes from the vendor STEP: the touch and display flex
tails, which the STEP shows unfolded, are cut off at the panel edge, and the camera module is moved
into its holder (its flex is left out). The vendor STEP goes in `references/`, which is not in the
repository either.

## Parts

| Qty | Part | Use |
|---|---|---|
| 1 | Case, printed (`exports/Case.stl`, or `crowpanel_7_case.3mf` with the frame) | |
| 1 | Front frame, printed (`exports/Frame.stl`) | |
| 4 | M3 × 16 mm flat-head self-tapping screws | Frame and PCB to the case's standoffs, from the front |

## Opening the designs

Open `crowpanel_7_case.sc` to edit the case and frame. With the local assembly, open
`crowpanel_7_enclosure.sc` for the whole device, and run **Update Links** in it after saving the case.

## Case and frame

- Case outside 181.1 × 108.2 mm, 20.9 mm deep; the frame stands 1.35 mm above the glass front, for a
  total thickness of 21.85 mm.
- Case walls 1.6 mm, back wall 1.7 mm, 0.5 mm gap round the PCB. The frame fits inside the case's rim
  with 0.25 mm per side.
- PCB mounting: four Ø6 standoffs at the PCB's corner holes, from the back wall up to the PCB back, with
  Ø2.5 pilot holes for the self-tapping screws. The frame's corner posts come down onto the PCB front,
  trimmed clear of the glass, with M3 clearance holes and 90° countersinks.
- Frame: a 1 mm plate 0.35 mm above the glass that covers 1 mm of the glass border all round.
- Back openings, sized from the parts with a margin: the 2×20 header, the two 4-pin connectors, the
  4-pin 2.5 mm connector, the slide switch, the two LEDs, access holes for the two buttons, two
  microphone holes, and a notch through the side wall for the two 1×7 pin headers (as in Kern's case).
- Two speaker grilles in the back, over the PCB's two 14 × 25 mm cutouts, as in Kern's 10.1" case.
- Side openings: two USB-C ports (12.5 × 6.5 mm, rounded) in the +X wall; the microSD slot (13 × 3 mm,
  with a 0.8 mm chamfer) in the +Y wall.
- Camera holder: the camera module that ships with the board faces backwards. Its square lens holder
  rests on a Ø16 holder and its Ø9 barrel goes through a Ø9.3 bore, leaving the lens front 0.5 mm inside
  the back face.
- Printing: the case prints on its back, which has a 1 mm chamfer round its outer edge; the frame
  prints face down, so turn it over in the slicer.

The parts are driven by 48 named user parameters (Parameters table, each with a comment), among them
`fit`, `wall`, `floor_t`, `depth`, `rim_lift`, `standoff_d`, `pilot_d`, `frame_gap`, `plate_gap`,
`plate_t`, `lip`, `post_d`, `usb_w`, `usb_h`, `sd_w`, `cam_y`, `cam_seat`, `grille_n` and
`grille_pitch`. The board-derived values (PCB, glass, holes, connector positions) were measured on the
vendor STEP.

Coordinate frame for every part: origin at the centre of the glass front face, +Z toward the viewer,
USB-C end at +X, the 2×20 header and microSD at +Y, the 4-pin connectors and the camera at -Y.

## License

MIT, see [LICENSE](../LICENSE). It covers this project's own files. The vendor's board model is not
in the repository.
