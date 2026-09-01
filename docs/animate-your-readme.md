# Animate your README with Xanini SVGs

Xanini builds SVGs with animations that render on GitHub.

<sub>A GitHub README can't run scripts or CSS animation but it can still show motion thanks to SMIL, SVG's animation language.</sub>

<br>

---

<br>

## Capsules are one SVG file each

A capsule is one canvas that can have many shapes with their own individual animations. 
Each capsule downloads as its own standalone SVG
file.

You can add more capsules to easily fine tune and sync many different SVG animations at the same time. Each capsule keeps its own animation timing. 

The GitHub README stacks them vertically, renders them flush, and plays them together exactly as they did in Xanini.

| Step | Action                                                                                                                                                                                                                                                                                                                                                                                    |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1    | [Open the live GitHub Page app](https://fabian-galvez.github.io/Xanini/) in a browser <br><br>or <br><br>Download [index.html](../index.html) and double-click it. Both are identical. Only difference is being able to run it offline                                                                                                                                                            |
| 2    | Add shapes and text from the top bar.  Drag to place, corner handle to resize, arrows to nudge.<br><br>This is where your skills as an artist come into play. Be creative and try different things. There are many combinations and possibilities to make something unique                                                                                                                |
| 3    | Animate any shape and give it motion from the animation presets. Play around with each shapes individual entrance/exit animations and their individual delay/duration times                                                                                                                                                                                                               |
| 4    | You can add loops to individual shapes/animations and add a loop to individual capsules as well. <br><br>Press Replay to watch the whole sequence from zero is the capsule doesn't have a loop (Loop set to 0)                                                                                                                                                                            |
| 5    | Press Download in the capsule header to save a single SVG, `capsule-1.svg`.<br><br>and/or<br><br>Save the Project to download all capsules as they appear and be able to load them back up to continue where you left off.<br><br>Everything exported by Xanini is built to survive exporting. <br>Imported SVG's you previously exported open in the app exactly as they were downloaded |
<sub>Preview with Anim off before shipping to make sure that everything renders.</sub>

> [!important]- Make sure to save your work by downloading your files to your machine. 

| File                                   | Description                                                                                        |
| -------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Download capsule-N.svg                 | Individual capsule download. Exports one SVG per capsule.                                          |
| Save project to download project .json | Downloads all capsules. Import opens project and all SVG's as they were when you saved the project |

> [!warning]- Any unsaved work will be lost if you exit the page or close the browser. 

<br>

---

<br>

## README SVG layer assembly

| Step | Action                                                                                           |
| ---- | ------------------------------------------------------------------------------------------------ |
| 1    | Copy the capsule files into an  `assets/` folder in the repo                                     |
| 2    | In the app, press Copy README snippet. It writes the centered img block with the right file name |
| 3    | Paste one block per capsule, in order. Capsule order in the app sets the numbering               |
| 4    | Commit and open the README. The stacked SVGs play together as one composition                    |


## Live example

The profile README at `github.com/Fabian-Galvez` opens with a Xanini SVG file:

| File                  | Size       | Carries                                             |
| --------------------- | ---------- | --------------------------------------------------- |
| `Fabian-Galvez-README.svg` | 624 by 200 | The whole banner is 1 SVG with 12 animation records |

The README block:

```html
<p align="left">
  <img src="./assets/Fabian-Galvez-README.svg" alt="Hi, I'm Luis" />
</p>
```



<br>

---

<br>

## Checks before the commit
| Check                                   | Reason                                                                                                                                                                                                                                                          |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Preview to ensure SVG animations render | If SVG's arent animating verify the animation toggle in the Capsule header, Anim on/off, is set to on and redownload the SVG                                                                                                                                    |
| Looping or not looping                  | There are two types of Loop, the Capsule loop and the individual shape loop that is set in the Animation panel on the right. Loop 0 plays once. Any other number wait for the the animation to fully end then counts down the set seconds and loops infinitely. |
| Dark and light both work                | The preview background is transparent, not filled, and will show the README's background. <br><br>Ensure that the animations look good in dark and light settings by toggling the Preview: dark/light setting in Xanini before downloading.                     |
| The motion survives cold open           | Open the downloaded SVG file directly in a browser tab to make sure it renders well                                                                                                                                                                             |




Every control referenced here is listed in [controls.md](controls.md).
