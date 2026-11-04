# Harpsichord Stringing Calculator

A browser-based tool for designing and analyzing **harpsichord string scales**. It brings together string lengths, pitch, commercial wire diameters, breaking-strength data, safety factors, and estimated tensions in an interactive worksheet.

The application is intended for harpsichord builders, restorers, and researchers who want to compare possible stringing arrangements and document their work.

## Features

- **Pitch and transposition:** set the `a¹` reference pitch (415.3 Hz by default) and shift the calculated pitches in semitone steps. Frequencies are calculated using **equal temperament**.
- **String-scale worksheet:** enter or edit speaking lengths in millimeters for individual notes, and view frequency (Hz), *fL-scale* (m/s), wire diameter (mm), and estimated tension (kgf).
- **Wire database:** compare diameter-dependent wire data included in the application for Malcolm Rose, Instrument Workshop, Zuckermann, Vogel, Birkett, Voss, Microfil FADD, Ormiston, and Mount Joy (modern steel). Availability varies by manufacturer and material.
- **Material comparisons:** display wire-related *fL* values and calculated safety factors for red brass, brass, and iron/steel where data are available.
- **Diameter selection:** calculate a suggested commercial wire diameter, adjust the choice for individual notes using `−` / `+`, and reset the adjustments. A separate control sets the smallest wire size at `f²`.
- **Safety-factor highlighting:** set a safety-factor limit and see color-coded warnings when calculated values fall below that limit.
- **Length interpolation:** fill in known string lengths, then estimate missing intermediate lengths using a **natural cubic spline** or a **not-a-knot spline**.
- **Charts:** generate plots of *fL-scale*, string tension, and string lengths on a logarithmic scale.
- **Project files:** save and reopen work as local `.json` files, including project comments, settings, entered lengths, and diameter adjustments.

## Getting started

No installation or build process is required.

1. Download `calculadora_cordas07.html` from this repository.
2. Open it in a modern web browser.
3. Set the reference pitch, transposition, wire manufacturer, and safety-factor limit.
4. Enter or adjust the **Length (mm)** values in the note table. The file contains example values that you can replace.
5. Set the `f²` wire-size control. Review the suggested diameters, material data, safety factors, and tensions; use the per-note `−` / `+` buttons when needed.
6. Optionally interpolate missing lengths, generate charts, and use **Save Project** to download a `.json` file. Use **Open Project** to restore it later.

**Interpolation requirements:** the natural spline needs at least **three** entered lengths; the not-a-knot spline needs at least **four**. Only empty entries between the first and last entered points are filled.

## Main calculations

The worksheet uses the reference pitch and equal-tempered semitone relationships to calculate note frequencies. For each note with a known speaking length, it calculates:

- **fL-scale (m/s):** frequency in hertz multiplied by speaking length in meters.
- **Safety factor:** a logarithmic comparison between the calculated *fL-scale* and the *fL-wire* value stored for the selected wire diameter and material.
- **Commercial wire diameter:** a calculated diameter mapped to available wire sizes, with optional manual steps up or down.
- **String tension (kgf):** an estimate based on frequency, speaking length, selected diameter, and material density.

The application also includes a `c²` reference-diameter section for estimating a maximum possible string length and working-length ranges at two safety-factor settings. Its automatic instrument-type classification is based on the entered length of the sounding `c²`.

## Technology

- HTML, CSS, and vanilla JavaScript
- Chart.js for plotting, loaded from a CDN
- Browser-based JSON import and export using the File API

The calculator itself runs in the browser and does not require a backend. **An internet connection may be needed to load Chart.js** for the graphs unless the library is already cached or provided locally.

## Notes and limitations

- The wire database is embedded in the HTML; **not every manufacturer has data for every material or diameter**. Empty cells may indicate unavailable data.
- Note frequencies use equal temperament. The app is a **stringing and scaling calculator**, not a historical-temperament tuning simulator.
- Safety factors, diameter choices, and tensions are **engineering estimates**, not guarantees against wire breakage. Check physical properties, the chosen wire, and the instrument's construction before applying the results to an actual instrument.
- The initial **Nicolas Dufour – 1683** project is example content included in the supplied HTML, not a validated reference design.

## Publishing on GitHub Pages

The project is a static web page. To publish it with GitHub Pages, you can rename `calculadora_cordas07.html` to `index.html`, commit it alongside this `README.md`, and enable GitHub Pages for the repository.

## License

No license is specified in the current HTML file. Add a `LICENSE` file if you want to define how others may use, modify, and redistribute the code.
