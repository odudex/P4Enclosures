# p4_pico

A 3D-printable back shell for the Kern `p4_pico` device, built from an **ESP32-P4-Pico** board and a
**5" DSI touch display** (050-DSI-TOUCH-A), modelled in [SolidCraft](https://github.com/bherbruck/solidcraft).
It is one of the enclosures in [P4Enclosures](../README.md).

The display keeps its own case; the shell closes its back. It screws to the display's four
corner standoffs and holds the board, which sits in a keel below the main floor. The camera
looks out through a window in the back, and the USB-C port and the microSD slot are reached
through one opening in the side wall.

The back shell has been printed and tested.

## Files

| File | What it is |
|---|---|
| `back_shell.sc` | The printed part, fully parametric |
| `display_5in_dsi.sc` | Simplified display model (panel, back plate, standoffs) |
| `exports/` | `BackShell.stl` and `BackShell.3mf` for printing, `display_5in_dsi.step` |
| `pico_enclosure.sc` | Local only. Assembly: display, board, camera and back shell in place |
| `esp32_p4_pico.sc` | Local only. Board model, imported from the vendor's STEP file |

The two local-only files contain the vendor's board model, so they are not in the repository. To
rebuild `esp32_p4_pico.sc`, import the vendor's `ESP32-P4-PICO.stp` and remove its small components.
In that file the PCB is centred, its top face at Z 0, with the USB-C toward -X. The assembly turns the
board 180° about Z and places it at (32.16, 0, -14.7), and links its parts by relative path, so keep
the `.sc` files together. The vendor drawings, DXF and STEP for the board and the display go in
`references/`, which is not in the repository either.

## Parts

| Qty | Part | Use |
|---|---|---|
| 1 | Back shell, printed (`exports/BackShell.stl` or `BackShell.3mf`) | |
| 4 | M2.5 × 6 mm flat-head hex socket (Allen) screws | Shell to the display's corner standoffs |
| 4 | Small self-tapping screws for plastic | Board to the shell's posts: Ø1.3 mm pilot holes, 3.5 mm deep, through the 1.6 mm PCB |

## Opening the designs

Open `back_shell.sc` to edit the shell. With the local assembly, open `pico_enclosure.sc` for the
whole device, and run **Update Links** in it after saving a part.

## Back shell

- Outside 129 × 72.8 mm with R4 corners, matching the display; 9.6 mm deep, 22.2 mm at the keel.
- Walls and floor 2 mm.
- Display mounting: four M2.5 flat-head screws through counterbored holes into the display's
  standoffs.
- Board mounting: four tapered posts with Ø1.3 mm pilot holes for small self-tapping screws.
- Printing: stand the shell on its USB-C side wall (the +X face on the bed). The 45° ramp at the
  -X end of the keel and the 45° gussets on the corner mount blocks let it print without supports
  in that orientation.

The shell is driven by named user parameters (Parameters table, each with a comment), among them
`shell_w`, `shell_h`, `wall`, `floor_t`, `cavity_depth`, `pocket_depth`, `mount_x`, `mount_y`,
`mount_reach`, `mount_reach_y`, `pcb_depth`, `post_x1`, `post_x2`, `post_y`, `lens_x`, `ramp_r`
and `ramp_x`.

Coordinate frame for every part: origin at the centre of the display's back face (the mounting
plane), +Z toward the viewer, USB-C end at +X.

## License

MIT, see [LICENSE](../LICENSE). It covers this project's own files. The vendor's board model is not
in the repository.
