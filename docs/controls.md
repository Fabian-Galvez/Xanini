# Xanini Controls

Every control in the app. Back to the [README](../README.md).

<br>

## Keys

Shortcut keys defaults that are re-bindable. Change them in the app's Controls panel.

| Key       | Action                           |
| --------- | -------------------------------- |
| `B`       | Bite                             |
| `N`       | Clear bites                      |
| `U`       | Unite                            |
| `D`       | Duplicate                        |
| `[` / `]` | Send back / Bring forward        |
| `C` / `V` | Center horizontally / vertically |
| `A`       | Select tool                      |
| `E`       | Edit points tool                 |
| `P`       | Pen tool                         |

Fixed, not rebindable:

| Key                                                              | Action                                              |
| ---------------------------------------------------------------- | --------------------------------------------------- |
| Arrows                                                           | Nudge 1px                                           |
| Shift + arrows                                                   | Nudge 10px                                          |
| `Del` or `Backspace`                                             | Delete the selection                                |
| `Ctrl+Z` / `Ctrl+Y`                                              | Undo / redo                                         |
| `Ctrl+C` / `Ctrl+V`                                              | Copy the selection / paste into the active capsule  |
| `Ctrl+G` / `Ctrl+Shift+G`                                        | Group the selection / ungroup                       |
| Alt + click                                                      | Cycle down a stack of shapes                        |
| `Esc`                                                            | Cancel a pen path, or return to the Select tool     |
| Ctrl + wheel, Alt + wheel, Space + drag, `+`, `-`, `0`, `1`, `2` | Zoom, resize and pan, listed under Canvas and mouse |

The single-key shortcuts and `Ctrl+C` / `Ctrl+V` are off while the cursor is in a text or number field. Typing an `s` types an `s`, and `Ctrl+C` copies the text.

Unite answered to `G` until 31 August 2026, and `Ctrl+G` was Group. `G` on the canvas with two shapes selected ran Unite. Unite fused the pair into one element that kept only the first shape's fill. Unite also gives that element the type name `group` in the project file, so the merge read as a broken Group. Unite answers to `U` now. A project saved with the old key opens with `U`, unless the user has already given `U` to another command.

<br>

---

<br>

## The four regions, and the strip between two of them

| Region                                     | Holds                                                                                                                     |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| Tool rail, down the left                   | The three tools, then the shape buttons, then Text                                                                        |
| Top bar                                    | The project: Add capsule, Load, Save, Copy active SVG, Preview, Flip layout, and a More menu for the rest                 |
| Canvas strip, above the drawing            | Undo, Redo, Copy, Paste, Duplicate, Delete, and the zoom controls                                                         |
| Arrange and combine strip, right of the canvas | Twelve square icon buttons: Send back, Bring forward, the two centering buttons, then Group, Ungroup, Unite, Intersect, Bite, the Bite help, Clear bites and Outline stroke |
| Right panel                                | Everything else that acts on what is selected: SELECTION, ELEMENT, ANIMATION, and POINTS while the edit points tool is active |

The strip is 44 px wide and its buttons are the 32 px square the zoom
controls draw. Each button carries a glyph and no words. The words are in
the hover label, which reads the button's name, the sentence that says what
it does, and its key.

ARRANGE and COMBINE were two sections of the right panel until 31 August
2026. Five sections in one 260 px column put both of them below the window
at every height this app runs at, so a person could reach Group and Bite
only by scrolling the panel. Offset by, Grow and Shrink went to the ELEMENT
section instead of the strip, because a number box does not fit a 44 px
column. Font size and font family share one row there now, which gives back
the line Offset takes.

At 900 px the top bar's spare buttons move into the More menu. At 600 px the
rail and the arrange and combine strip both become horizontal strips, and
the right panel becomes a drawer under them. No width has a sideways scroll
bar.

<br>

---

<br>

## The Controls panel

Opened from the More menu, it expands inside the menu. Click anywhere
outside to close. One table per group of buttons

| Column       | Holds                                                                                                                             |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| Shortcut     | The key, in a box you can type a new one into. A fixed key such as Ctrl+Z shows as plain text with no box. Beside it, tap or hold |
| Control      | The button itself and its name, together                                                                                          |
| What it does | The same description its hover label carries                                                                                      |

Every button with a key has the key, with it's name and description, printed in the buttons hover label.

> [!Tip]- Hover the mouse over each button if you forget a key.

<br>

---

<br>

## Tools

One tool is active at a time in the rail. Other buttons are selections, not modes.

| Tool        | Key   | Description                                                                                                                                                                            |
| ----------- | ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Select      | `A`   | Click, drag, resize, rotate, marquee. This is what the app does with no tool chosen.                                                                                                   |
| Edit points | `E`   | Shows the shape's points and lets you drag them. A shape that was a square, a star or a cut outline is converted to points the first time, and the drawing does not change when it is. |
| Pen         | `P`   | Draws a new shape point by point, or freehand.                                                                                                                                         |
| Escape      | fixed | Cancels a half drawn pen path. With no path drawn it returns to Select.                                                                                                                |

<br>

---

<br>

### Edit points

| Action                    | Description                                                                                                                           |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Click a point             | Selects it. Shift-click adds to the selection. Drag on empty canvas rubber-bands several.                                             |
| Drag a point              | Moves it and both its handles.                                                                                                        |
| Drag a handle             | Bends the curve. What the other handle does depends on the point's type below.                                                        |
| Double-click the outline  | Adds a point there. The outline does not move: the segment is split at the place you clicked, which is the same curve written as two. |
| `Del` or `Backspace`      | Removes the selected points and refits the two segments either side into one.                                                         |
| Cusp                      | The two handles are independent. The point is a corner.                                                                               |
| Smooth                    | The two handles stay in line through the point and may differ in length.                                                              |
| Symmetric                 | The two handles stay in line and equal. The curve passes through evenly.                                                              |
| Radius, then Round corner | Replaces a corner with an arc of that radius. The radius is clamped so it can never eat more than half of either edge beside it.      |
| Break apart               | Turns a shape whose outline is several rings into one shape per ring.                                                                 |
| Join                      | Joins the two selected end points of two open runs into one run.                                                                      |

A shape with a hole, and a shape a bite cut into separate pieces, both edit by
their points. 

<br>

---

<br>

### Pen

| Action                      | Description                                                                                                                                                |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Press                       | Places a corner point.                                                                                                                                     |
| Press and drag              | Places a smooth point whose handles follow the drag.                                                                                                       |
| Alt while dragging          | Moves only the outgoing handle. That makes the point a corner.                                                                                             |
| Press on the first point    | Closes the path.                                                                                                                                           |
| `Enter`                     | Finishes an open path.                                                                                                                                     |
| `Backspace`                 | Removes the last point.                                                                                                                                    |
| Shift when the press begins | Draws freehand. The raw movement is simplified and fitted to curves when you let go. A hand drawn S arrives as about four points instead of three hundred. |

A finished path is an ordinary shape. It takes color, animation, bites,
booleans and its own points like anything else.

<br>

---

<br>

## The right panel


| Control      | Description                                                                                                                                                                                              |
| ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Fill, Stroke | The two color rows. The one you touched last is marked. Every swatch below writes to that one. Picking a stroke color on a shape with no stroke width gives it one, or the color would paint nothing |
| Swatches     | Ten to start with, and yours after that. Click one to set the marked row. The + adds the color showing in that row. The small cross drops one. Alt-click replaces one with the color showing             |
| Recent       | The colors you have used, newest first. It fills itself and clicking one works the same way                                                                                                              |
| Keep style   | On means what you set carries to every new shape. Off means it falls back to the default after each one                                                                                                  |
| Make default | The values showing now become your default. Saved with the project                                                                                                                                       |
| Reset        | Throws that saved default away. The app's own default is the default again. Dim when you have saved none                                                                                                 |

These work with a shape selected or with nothing selected. With none they
set what the next shape starts with.

A button that cannot act in the state you are in is dim, and its hover label
says what is missing. Bite, Unite and Intersect need exactly one shape
selected. That one is the shape doing the cutting or merging. Outline
stroke needs a line. Clear bites needs something already cut. Ungroup needs a
group. Group needs two or more shapes.

<br>

---

<br>

## Capsule header


| Control          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| W / H            | Capsule size in px. Default 600x200. Changing them changes the frame; the shapes stay where they are.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Anim: on / off   | Off shows the still image a renderer sees when it ignores animation. That picture is always the finished one.                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Loop             | 0 plays the sequence once. Any other number restarts the whole sequence that many seconds after it finishes.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Up / down arrows | The two arrow buttons on the right of the header. They reorder capsules on the page. The order sets the numbering in the README snippet. The up arrow is grayed out on the first capsule and the down arrow on the last.                                                                                                                                                                                                                                                                                                           |
| Download         | Saves the capsule as a standalone SVG, named capsule-N.svg.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Import           | Reads one .svg into a new capsule inserted at the top, the way Add capsule works; every existing capsule keeps what it holds and moves down one. The new capsule has the default size, grown only where the file is larger, and the file's drawing is centered in it. A small icon file does not arrive as a tiny frame. Typing text made here comes back as typing. On text, font-family and font-weight together pick the matching Font family stack, and letter-spacing and font size come back as the same numbers the file carried, so a capsule this app exported reads back with nothing lost. Export size: shapes brings the drawing's own box back at download time. One undo removes the new capsule. Load in the menu replaces the whole project instead. An imported element takes its animation from the file it arrived in. It takes none when the file carries none. Every new shape takes what the Animation panel holds. An import took the same until 31 August 2026. A file with no animation in it arrived carrying the last entrance and exit the user set. |
| Delete           | Removes the capsule, after a warning box that names it. Deleting the last one empties it instead. Ctrl+Z brings a deleted capsule back. The warning says so. Tick "Do not ask again this session" to skip the box until the page is reloaded.                                                                                                                                                                                                                                                                                      |

<br>

---

<br>

## Canvas and mouse

| Action                                    | Description                                                                                                                                                                                                                                                                                    |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Click                                     | Selects a shape. The click has to land on the shape itself: inside a triangle, on a circle, on the line, not in the empty corner of its box. A click through a bite falls to the shape underneath. Shift-click adds to the selection. Alt-click cycles down a stack of overlapping shapes. |
| Drag on empty canvas                      | Marquee select. Anything it touches is selected.                                                                                                                                                                                                                                               |
| Drag a shape                              | Moves it, or the whole selection as one.                                                                                                                                                                                                                                                       |
| Corner handle                             | Resize. Shift keeps the proportions the shape had when the drag began. Alt grows it from its center. Shift and Alt together grow it in place with the proportions kept. On text, drag down to grow the font. Lines stay straight. Shift locks them to 45 degree steps.                     |
| Arrows                                    | Nudge 1 px. Shift-arrows nudge 10 px.                                                                                                                                                                                                                                                          |
| Wheel                                     | Scrolls the page, the way a wheel does everywhere else.                                                                                                                                                                                                                                        |
| Ctrl and wheel                            | Zooms the canvas, holding the point under the cursor still. Inkscape, Figma and the browser itself all use Ctrl for this.                                                                                                                                                                      |
| Alt and wheel                             | Grows and shrinks everything selected, about the middle of the selection. One burst of notches is one undo step.                                                                                                                                                                               |
| Space and drag, or middle button and drag | Pans.                                                                                                                                                                                                                                                                                          |
| `+` / `-`                                 | Zoom in or out one step.                                                                                                                                                                                                                                                                       |
| `0` / `1` / `2`                           | Back to 100 per cent / fit the capsule / fit the selection.                                                                                                                                                                                                                                    |

Zoom and its buttons are in the strip above the canvas.

<br>

---

<br>

## Element panel

Shows the controls that apply to the selected shape.

| Control        | Description                                                                                                                                                 |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Text           | The string. Editing refits the box.                                                                                                                         |
| Fill / Stroke  | Color pick, or type a hex. Type `none` for no paint.                                                                                                        |
| Outline        | Stroke width. Draw entrances need a stroke to draw.                                                                                                         |
| Corner radius  | Rectangles only. Pills are the radius maxed.                                                                                                                |
| Font size      | Text only, in px. Floor is 8, so a shape never shrinks past the point it stops reading as text. Shares one row with Font family, on the label `Font`.       |
| Font family    | Text only. Five web-safe stacks: Monospace, Sans, Serif, Heavy sans, System heavy. Each one ends in a generic family (monospace, sans-serif or serif), so the exported SVG never depends on a font the reader's machine lacks. Each stack carries its own weight too: 600 for the first four, 800 for System heavy, which is `ui-sans-serif, system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif` at that weight, for matching a real page heading rather than faking the weight with a display font. Importing an SVG this app wrote, or any SVG whose text carries font-family and font-weight, reads both back to the matching stack. |
| Letter spacing | Text only, in the same units as the canvas. Negative pulls letters together; 0 is the old, unspaced run. Refits the box the same way Text and Font size do.  |
| Rotation (deg) | Rotates around the shape's center. Bites rotate with it. The round handle above a selected shape does the same by mouse; Shift snaps it to 15 degree steps. |
| Hide           | Keeps the shape in the stack but out of the canvas and the export.                                                                                          |
| Opacity        | 0 to 1. This is the resting value, before any animation.                                                                                                    |
| Offset by, then Grow or Shrink | Grows the shape outward or shrinks it inward by that distance, rounding every corner. Inkscape calls the two Outset and Inset. This row came in from COMBINE on 31 August 2026, because its number box does not fit the 44 px icon strip. |

<br>

---

<br>

## Animation panel

| Control                                 | Description                                                                                                                                             |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Entrance                                | First thing the shape does: fade, zoom, bounce, four slides, draw, typing, or any of the seven loops. Draw needs a stroke. Typing needs a text element. |
| Delay (s)                               | Wait before the entrance starts. Stagger delays across shapes to make a capsule read as a sequence.                                                     |
| Duration (s)                            | How long the entrance takes.                                                                                                                            |
| Iterations                              | For a loop entrance: 0 repeats forever, any other number runs that many passes.                                                                         |
| Exit + exit delay, duration, iterations | Same options, played on the way out. Exit delay is absolute, counted from zero.                                                                         |
| Second color                            | The color the color pulse swings to.                                                                                                                    |
| Blinking caret                          | Typing only. On by default. Hidden until the Delay, then on and off every half second to the end of the loop.                                           |

<br>

---

<br>

## Arrange and combine


| Control                        | Panel        | Description                                                                                                                                                                                                                                                                                                 |
| ------------------------------ | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bite                           | Strip        | Punches the selected shape's outline out of every shape it overlaps. The cut is real geometry: the shape is rewritten as its own outline. The next bite, the click test and the exported file all read what is on the canvas. Bite intersects the two real outlines first. Two shapes whose boxes overlap need not touch. Two diamonds meeting corner to corner passed the old box test. That bite took no area, and the shape recorded it anyway until 31 August 2026. A line on either side is outlined first. A line can be cut and can cut. |
| ? beside Bite                  | Strip        | Opens a small animated drawing of what Bite does. Hovering Bite for about 400 ms opens the same panel. It closes when the pointer leaves, on Escape, or on a click outside. It sits under Bite in the strip, and it stays live with nothing selected.                                                        |
| Clear bites                    | Strip        | Clears the cuts the selected shape received and gives back the frame the shape had before its first bite. The refit after a cut shrinks the box to what is left, so a 160 px rect that lost its right end came back drawn into a 155.6 px box until 31 August 2026.                                         |
| Unite                          | Strip        | Merges the selected shape into every shape it overlaps. Two outlines become one.                                                                                                                                                                                                                         |
| Intersect                      | Strip        | Keeps only the part where the selected shape and the shape under it overlap.                                                                                                                                                                                                                                |
| Outline stroke                 | Strip        | Turns a line's stroke into a filled outline. A line has no area. Nothing can be subtracted from it until this runs. Bite, Unite and Intersect run it for you; the button is there for when you want the outline itself, to edit its points. Inkscape calls this Stroke to Path.                          |
| Group / Ungroup                | Strip        | Group links the selection: clicking one member selects them all. Drag, nudge, delete, copy and duplicate act on the whole group. Ungroup breaks the link and leaves every shape where it is. The link is saved in the project file.                                                                     |
| Undo / Redo                    | Canvas strip | 60 steps. Drags and nudges collapse into one step.                                                                                                                                                                                                                                                          |
| Center shape horizontally / vertically | Strip | Centers the whole selection in the capsule. The two buttons measure the box around everything selected and move every member by the same distance, so a pair keeps its spacing and a group stays a group. They read one shape until 31 August 2026, which meant they did nothing at all to a pair and pulled one member out of a group. Their icons are a dotted line with a shape sitting on it. |
| Send back / Bring forward      | Strip        | Moves the shape one step through the stack. Send back draws `[` and Bring forward draws `]`, the two keys they answer to, and the pair reads as one bracket.                                                                                                                                                |
| Copy / Paste                   | Canvas strip | Copy takes the selection into the app's own clipboard. Paste puts it in the active capsule with new ids, selected: 12 px down and right in the same capsule, on the same coordinates in another one.                                                                                                        |
| Duplicate                      | Canvas strip | Copies the selection 20 px down and to the right.                                                                                                                                                                                                                                                           |
| Delete                         | Canvas strip | Deletes the selection.                                                                                                                                                                                                                                                                                      |
| Section arrows                 | all three    | Reorders the panel sections. ELEMENT, ANIMATION and POINTS all carry them. The project file holds the order. A file saved while ARRANGE and COMBINE were sections still names them, and the app ignores a name it finds no section for.                                                                     |
| Section scrolling              | all three    | The panel scrolls as one column with one scroll bar. Each heading stays put while its own section passes under it. Three sections fit a 800 px tall window without scrolling.                                                                                                                               |
| Color target                   | Fill, Stroke | The color row touched last is marked. Every swatch and Recent color writes to that one. Shift forces the other one.                                                                                                                                                                                     |

<br>

---

<br>

## Multi-select panel

Visible when two or more shapes are selected.

With more than one shape selected, `+ delay`, `+ duration`, and `+ exit duration` add the typed value to each shape from the existing settings as the base. Subtract time by adding negative values. 

| Control                                               | Description                                                                                         |
| ----------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| + delay / + duration / + exit delay / + exit duration | Adds the value to each shape's own value.                                                           |
| Group / Ungroup                                       | Same as the buttons in COMBINE.                                                                     |
| Unite                                                 | Fuses the selection into one compound shape and cannot be reversed. Text cannot join a union.       |
| Hide                                                  | Hides everything selected.                                                                          |
| Copy / Paste                                          | Same as the buttons in the canvas strip, on the whole selection.                                    |
| Duplicate                                             | Copies the whole selection 20 px down and to the right. A group is duplicated as its own new group. |
| Delete                                                | Deletes everything selected.                                                                        |

Center, forward, back, bite, and clear bites need one shape selected. Multi-selection does nothing.

<br>
