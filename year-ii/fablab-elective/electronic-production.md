# Electronic Production

### We learned how to export file from KiCad and mill it through SRM-20 mill

### 1. Export from KiCad

* [ ] Open The PCB in **Pcbnew**.
* [ ] Only choose layer of **(F.Cu)** for traces in '_Include Layers_'and **Edges.Cuts** for outline in '_Plot on all layers_'
* [ ] Go to **File → Plot/Print**:
  * Format: **SVG** (or Gerber if you prefer converting)
* [ ] If needed, convert SVG → PNG (black = copper, white = removed)

### 2. Use Inkscape to organize the layers of the traces in group

Select the outline and go the _Path_ in the menu and choose '_Fill between path_'. Make this into a layer for outline.

Group the black background as Background.

Group the rest as traces.

<figure><img src="../../.gitbook/assets/Screenshot 2026-03-20 181208.png" alt=""><figcaption></figcaption></figure>

<div><figure><img src="../../.gitbook/assets/Screenshot 2026-03-20 181043.png" alt=""><figcaption><p>Exported outline file</p></figcaption></figure> <figure><img src="../../.gitbook/assets/Screenshot 2026-03-20 181325.png" alt=""><figcaption><p>Exported trace file</p></figcaption></figure></div>

Export the file in DPI 1000, and save as .png file.

### 3. Prepare in MODS

Open **modsproject.org** → select:

click _Programs → Open server program → SRM-20 Mill→ mill 2D PCB_

Load the**PNG** file.

#### Set parameters:

**Tool diameter**: e.g. 0.2 mm _(1/64")_ for traces

**Cut depth**: \~0.1 mm

**Max depth**: same as cut depth (for traces)

**Offset number**: 3–5 (more = more isolation)

For outline: Use _1/32"_ tool

### 4. Generate toolpath

Click **Calculate,** we can review paths. And click **Save file** → generates `.rml` file

### 5. Setup Roland Mill

Tape the PCB (FR1 board) on bed (double-sided tape)

Install correct **end mill**:

* 1/64" → traces
* 1/32" → cutout
* Set **origin (X, Y, Z)**:
  * Lower tool gently to touch surface (Z = 0)

### 5. Mill the PCB

Send `.rml` file to machine (via mods or Roland software)

Mill **traces first** with 1/64 drill, then **outline** with 1/32 drill

We need to check if there is dust so that the board is successfully milled, if not, we need to re-adjust the Z=0

After milling:

Clean board (brush + alcohol)

Check for shorts

<figure><img src="../../.gitbook/assets/WhatsApp Image 2026-03-20 at 18.29.02.jpeg" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/WhatsApp Image 2026-03-20 at 18.40.47.jpeg" alt=""><figcaption><p>The results >&#x3C;</p></figcaption></figure>

### 6. Soldering

Solder components and test circuit

<div><figure><img src="../../.gitbook/assets/WhatsApp Image 2026-03-20 at 19.40.22.jpeg" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/WhatsApp Image 2026-03-20 at 19.jpeg" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/WhatsApp Image 2026-03-20 at .jpeg" alt=""><figcaption></figcaption></figure></div>
