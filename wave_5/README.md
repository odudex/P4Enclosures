# wave_5

A 3D-printable case for the Kern `wave_5` device, built on the Waveshare
**ESP32-P4-WIFI6-Touch-LCD-5** board (glass, 5" LCD and PCB in one module), modelled in
[SolidCraft](https://github.com/bherbruck/solidcraft). It is one of the enclosures in
[P4Enclosures](../README.md).

The case is a single printed part. The glass drops into a pocket in the rim. The board screws to four
bosses on the back wall through its own M2.5 standoffs, and a 503450 LiPo sits in a bay under it. The
camera looks out the back from a holder on the back wall. The two USB-C ports, the microSD slot and
the three side buttons are reached through the side walls, the buttons through separate printed
plungers.

Work in progress: the case and buttons are modelled and exported, but the fit and plunger clearance
have not been print-tested, the battery is not in the assembly yet, and the camera holder still
needs checking against the real camera module.

## Files

| File | What it is |
|---|---|
| `wave5_case.sc` | The printed parts, fully parametric: body `Case` and plungers `Button1`–`Button3` |
| `exports/` | `wave5_case.3mf` (case and three buttons), `Case.stl`, `Button.stl` (one button; print three) |
| `images/` | `assembly.png`, a render of the assembly from behind |
| `wave5_enclosure.sc` | Local only. Assembly: board and case in place |
| `wave5_board.sc` | Local only. Board model, the vendor's STEP file imported as is |

The two local-only files contain the vendor's board model, so they are not in the repository. The
assembly links `wave5_case.sc` by relative path, so keep the `.sc` files together. The board in the
assembly is its own copy of the vendor STEP, placed as described under the coordinate frame below,
not a link to `wave5_board.sc` (linking the full board design is too slow in SolidCraft). Changes to
`wave5_board.sc` must therefore be repeated in the assembly by hand. The vendor drawing and STEP go in
`references/`, which is not in the repository either.

## Parts

| Qty | Part | Use |
|---|---|---|
| 1 | Case, printed (`exports/Case.stl`, or `wave5_case.3mf` with the buttons) | |
| 3 | Button plunger, printed (`exports/Button.stl`) | Side buttons |
| 4 | M2.5 × 6 mm flat-head hex socket (Allen) screws | Case to the board's standoffs, from the back |
| 1 | 503450 LiPo battery with an MX1.25 plug | In the bay under the board, taped to the floor |

## Opening the designs

Open `wave5_case.sc` to edit the case. With the local assembly, open `wave5_enclosure.sc` for the
whole device, and run **Update Links** in it after saving the case.

## Case

- Outside 130.6 × 74.4 mm, 17.7 mm deep; the rim stands 0.2 mm proud of the glass front.
- Rim wall 1.6 mm, back wall 1.7 mm; 0.25 mm gap per side around the 126.9 × 70.7 mm R3 glass.
- Board mounting: four tapered bosses (Ø6 at the top, widening at 25° down to the back wall) under the
  board's M2.5 standoffs. M2.5 flat-head screws go in from the back, their heads sunk 3 mm in
  recesses with a 90° countersink seat.
- Battery bay: the inner floor is 15.8 mm below the glass front, room for a 503450 LiPo taped to the
  floor under the board.
- Camera holder (from Kern's 4.3" case): Ø17 base with a 3 mm 45° chamfer to Ø11, joined to the -X
  wall with R3 rounds, Ø7.5 lens bore with an R1 round, and a 45° view cone 4.5 mm deep in the back
  face. Its top is 3 mm below the PCB, for the camera module that ships with the board.
- Openings: two USB-C ports (12.5 × 6.5 mm, rounded edges) in the +X wall; the microSD slot (14 × 3 mm)
  and three Ø5 button holes in the +Y wall.
- Side recesses: a 2 mm deep scallop, about 105 mm long with rounded ends, runs along the +Y wall
  from the glass shelf to 2 mm above the back face, so the microSD card and the buttons are easier
  to reach. The same scallop on the -Y wall is a grip.
- Buttons: three plungers with a Ø4.6 shaft and a Ø6.4 × 0.5 mm flange that keeps them in from the
  inside. They stand 0.8 mm out of the wall.
- The case prints on its back; the back outer edge has a 1 mm chamfer.

The case is driven by 53 named user parameters (Parameters table, each with a comment), among them
`glass_w`, `glass_h`, `fit`, `wall`, `rim_lift`, `floor_d`, `floor_t`, `boss_d`, `boss_taper`,
`hole_x1`, `hole_x2`, `hole_y`, `screw_recess`, `cam_x`, `cam_gap`, `usb_w`, `usb_h`, `sd_w`, `sd_h`,
`btn_x1`, `btn_pitch`, `btn_d`, `btn_proud`, `side_recess_depth`, `side_recess_x` and
`side_recess_bottom`. The board-derived values (standoff, connector and
switch positions) were measured on the vendor STEP.

Coordinate frame for every part: origin at the centre of the glass front face, +Z toward the viewer,
USB-C end at +X, buttons and microSD at +Y, the 2×20 header at -Y. The board model is the vendor STEP
turned 90° about Z and lowered 3 mm.

## License

MIT, see [LICENSE](../LICENSE). It covers this project's own files. The vendor's board model is not
in the repository.
