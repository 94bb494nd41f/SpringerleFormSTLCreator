# Springerle Mold Generator

A small browser tool that designs a **Springerle baking mold** from an image or sketch. The result is a mirrored depth map (PNG) or a print-ready **STL file** for 3D printing, with a choice of **six borders**.

The tool is a single file (`index.html`) and runs entirely in your browser. No installation, no server, no internet connection needed. Your image is never uploaded.

It is tuned for printers with a **0.2 mm nozzle**: borders and the minimum feature width are around 0.5 mm.

## Usage

1. Open `index.html` in a browser (a double-click is enough).
   Alternatively publish it with **GitHub Pages**: *Settings → Pages → Branch `main` → `/ (root)`*.
2. Choose your own image or load the **example fox**.
3. Adjust size, depth, threshold, depth levels, minimum feature width, draft angle and smoothing.
4. Pick one of the six borders.
5. Check the result: the **mirrored mold** on the left (dark = deep) and a **preview of the baked cookie** on the right.
6. Export:
   - **Depth map (PNG)**, 25 pixels per mm, for CNC milling, carving templates or heightmap import
   - **STL mold (negative)** to print directly
   - **STL positive (casting master)** to cast a silicone mold from

## The six borders

| Border | Description |
|---|---|
| **A · Double line** | two continuous lines (0.8 and 0.5 mm), inspired by historical molds |
| **B · Pearl border** | chain of round dimples (Ø 1.6 mm, 3.2 mm pitch) with larger corner pearls |
| **C · Zigzag band** | notched band of triangles between two frame lines |
| **D · Wave band** | flowing wave line (vine) between two frame lines |
| **E · Diamond band** | chain of small diamonds made of crossing zigzag lines |
| **F · Arch frieze** | row of small arches with a dot (garland) below the outer line |

The outer border also serves as a guide for cutting the cookie out.

## Settings

| Control | Effect |
|---|---|
| Width / Height | mold size in mm |
| Max. depth | depth of the deepest point (2–8 mm); about 4–5 mm is common |
| Threshold | darkness at which a line or area goes into depth |
| Depth levels | 3 to 32 (32 = continuous) |
| Min. feature width | thinner lines are thickened to this width (default 0.5 mm, suited to a 0.2 mm nozzle). 0 = off |
| Draft angle | tilts all walls (angle from vertical, default 12°) so the dough releases. Thin lines become V-shaped and shallower, wide areas keep full depth. 0 = off |
| Smoothing | rounds edges; keep it small for detailed motifs |
| Light motif on dark background | inverts the image brightness |
| Mesh resolution | STL detail (6, 8 or 10 px/mm) |
| Base | thickness under the deepest point (STL), default 1.2 mm. Total thickness = base + depth. Thinner saves filament |

## What makes a good Springerle mold

The defaults of the tool follow these criteria:

- **Negative mold, mirrored:** whatever is recessed in the mold becomes raised on the cookie. Text and motif must be mirrored.
- **Deeper than molds for flat cookies:** the relief must be clearly pronounced. The deepest spot is where the motif is fullest.
- **No undercuts, smooth and rounded hollows:** otherwise the dough sticks. The tool tilts all walls by an adjustable angle.
- **Clear silhouette:** historical molds are delicate, but thin lines are not reliably printable. With a 0.2 mm nozzle, keep features at about 0.5 mm or more.
- **Border or frame:** double lines and ornament bands give the motif a frame.
- **Wood with short fibers**, such as pear wood, if the mold is carved.
- **Typical size:** roughly 4–10 cm edge length.

## 3D printing

- Print the STL **flat, relief facing up**.
- **Save material:** keep the base thin (default 1.2 mm); 10–15 % infill and 2–3 walls are enough.
- For fine detail, a **resin printer** or a **0.2 mm nozzle** works better than a 0.4 mm nozzle. Layer height about 0.1–0.15 mm.
- **Food safety:** 3D-printed surfaces are porous and residue can collect in fine details. Resin is usually not food safe.
  A safer route: print the **positive**, cast a mold from **food-grade silicone**, and use that.
- Dust the mold with flour or starch before each use, hand-wash lukewarm, and do not put it in the dishwasher.
- Make a **test impression in modeling clay** before baking.

## Limitations

- The tool converts brightness into depth. It does not recognize subjects or add details. Line drawings with dark lines on a light background work best; photos only to a limited extent.
- Border dimensions and depth values are guidelines; verify them with a test impression.
- The example fox is a simple, hand-drawn graphic and is only a demo.

## Technical notes

Plain HTML, CSS and JavaScript with no dependencies. The depth map is built with the Canvas API. The STL is generated in the browser as a binary STL (closed mesh with a base). Runs in current versions of Chrome, Firefox, Edge and Safari. Large STL files (mesh resolution 10 px/mm) need some memory.

## License

MIT, see [LICENSE](LICENSE).

---

## Note on Claude

This project, including the code and this README, was created with the assistance of **Claude** (an AI assistant by Anthropic). The content is AI-generated and has not been thoroughly reviewed. Please check results yourself before use, especially dimensions, depths and exported STL files. The project gives no warranty for food safety, material choice or print results; responsibility lies with the users.
