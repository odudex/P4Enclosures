# wave_43

A 3D-printable case for the Kern `wave_43` device, built on the Waveshare
**ESP32-P4-WIFI6-Touch-LCD-4.3** board (glass, 4.3" LCD and PCB in one module), modelled in
[SolidCraft](https://github.com/bherbruck/solidcraft). It is one of the enclosures in
[P4Enclosures](../README.md).

The case is [wave_5](../wave_5/README.md)'s design, resized to this board: the same parametric model
with every board-derived value measured again on the 4.3" vendor STEP. The FreeCAD case for this board
that [@Filputt](https://github.com/Filputt) made for Kern served as a cross-check, and the camera
position comes from it.

The case is a single printed part. The glass drops into a pocket in the rim. The board screws to four
bosses on the back wall through its own M2.5 standoffs, and a 503450 LiPo sits in a bay under it. The
camera looks out the back from a holder on the back wall. The two USB-C ports, the microSD slot and
the three side buttons are reached through the side walls, the buttons through separate printed
plungers.

Work in progress: the case and buttons are modelled and exported, and the assembly shows no
interference with the board, but nothing has been print-tested yet.

## Files

| File | What it is |
|---|---|
| `wave43_case.sc` | The printed parts, fully parametric: body `Case` and plungers `Button1`–`Button3` |
| `exports/` | `wave43_case.3mf` (case and three buttons), `Case.stl`, `Button.stl` (one button; print three) |
| `images/` | `assembly.png`, a render of the assembly from behind |
| `wave43_enclosure.sc` | Local only. Assembly: board and case in place |
| `wave43_board.sc` | Local only. Board model, the vendor's STEP file placed in the case's frame |

The two local-only files contain the vendor's board model, so they are not in the repository. The
assembly links `wave43_case.sc` by relative path, so keep the `.sc` files together. As in wave_5, the
board in the assembly is its own copy of the vendor STEP, not a link to `wave43_board.sc`. The vendor
drawing, DXF and STEP go in `references/`, which is not in the repository either.

## Parts

| Qty | Part | Use |
|---|---|---|
| 1 | Case, printed (`exports/Case.stl`, or `wave43_case.3mf` with the buttons) | |
| 3 | Button plunger, printed (`exports/Button.stl`) | Side buttons |
| 4 | M2.5 × 6 mm flat-head hex socket (Allen) screws | Case to the board's standoffs, from the back |
| 1 | 503450 LiPo battery with an MX1.25 plug | In the bay under the board, taped to the floor |

## Opening the designs

Open `wave43_case.sc` to edit the case. With the local assembly, open `wave43_enclosure.sc` for the
whole device, and run **Update Links** in it after saving the case.

## Case

- Outside 118.1 × 70.5 mm, 17.9 mm deep; the rim stands 0.2 mm proud of the glass front.
- Rim wall 1.6 mm, back wall 1.7 mm; 0.25 mm gap per side around the 114.4 × 66.8 mm R2.5 glass.
- Glass shelf: the glass is only 0.55 mm thick along its border, so the shelf sits under that border.
  The thicker touch layer behind the middle of the glass sits inside the cavity.
- Board mounting: four tapered bosses (Ø6 at the top, widening at 25° down to the back wall) under the
  board's M2.5 standoffs, on a 92 × 50 mm grid. M2.5 flat-head screws go in from the back, their heads
  sunk 3.6 mm in recesses with a 90° countersink seat, so 6 mm screws reach 3 mm into the standoffs.
- Battery bay: the inner floor is 16 mm below the glass front, room for a 503450 LiPo taped to the
  floor under the board.
- Camera holder (from Kern's 4.3" case): Ø17 base with a 45° cone to Ø9, Ø7.5 lens bore, and a 45° view
  cone 4.5 mm deep in the back face, 44.1 mm from the centre at the end away from the USB-C ports. Its
  top is 3 mm below the PCB, for the camera module that ships with the board.
- Openings: two USB-C ports (12.5 × 6.5 mm, rounded edges) in the +X wall, which is 4 mm thick there
  because the ports sit 2.25 mm inside the glass edge; the microSD slot (13 × 3 mm) and three Ø5
  button holes in the +Y wall.
- Side recesses, as on wave_5: a 2 mm deep scallop, about 93 mm long with rounded ends, runs along
  the +Y wall from the glass shelf to 2 mm above the back face, so the microSD card and the buttons
  are easier to reach. The same scallop on the -Y wall is a grip.
- Buttons: three plungers with a Ø4.6 shaft and a Ø6.4 × 0.7 mm flange that keeps them in from the
  inside. They stand 0.8 mm out of the wall.
- The case prints on its back; the back outer edge has a 1 mm chamfer.

The case is driven by the same 53 named user parameters as wave_5 (Parameters table, each with a
comment). The board-derived values (glass, cavity, standoff, connector and switch positions) were
measured on the vendor STEP.

Coordinate frame for every part: origin at the centre of the glass front face, +Z toward the viewer,
USB-C end at +X, buttons and microSD at +Y, the 2×20 header at -Y. The board model is the vendor STEP
turned 90° clockwise about Z, seen from the front; its glass front is already at Z 0.

## License

MIT, see [LICENSE](../LICENSE). It covers this project's own files. The vendor's board model is not
in the repository.
