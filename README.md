# True ⇄ Magnetic ⇄ Compass (Offline) — v1.1b (BASELINE)

Offline web app that:
- Calculates **magnetic declination** (True ↔ Magnetic) using **WMM-2025** (built-in)
- Applies your boat’s **compass deviation** (Magnetic ↔ Compass) using a 15° deviation table with interpolation
- Works offline as a PWA
- Prints a clean **Deviation Card** (good for laminating)
- EN / FR-CA toggle

© 2026 Glen Carruthers. All rights reserved.

---

## Quick Definitions

### True North (TN) / True Heading (°T)
Direction relative to the geographic North Pole (maps/true bearings).

### Magnetic North (MN) / Magnetic Heading (°M)
Direction relative to the Earth’s magnetic field at your location.

### Compass Heading (°C)
What your ship’s compass actually reads.

### Declination (Variation)
The angle between **True North** and **Magnetic North** at a specific location and date.
- **East declination** is **positive (+)**
- **West declination** is **negative (−)**

This app calculates declination from **WMM-2025** (World Magnetic Model).

### Deviation
The error of your **boat’s compass** caused by onboard magnetic influences (engine, wiring, speakers, metal, electronics).
Deviation depends on heading and is usually measured by “swinging” the compass.

In this app:
- **East deviation = +**
- **West deviation = −**
- You enter values every **15°** (0°–345°)
- Intermediate headings are calculated by **linear interpolation**
- Blank entries are treated as **0.0°** (for printing and calculations)

---

## Sign Convention (Important)

**East = +, West = −** for both declination and deviation.

### True ↔ Magnetic (Declination)
- **Magnetic = True − Declination**
- **True = Magnetic + Declination**

Example: Declination = **+10° (10°E)**  
If True = 120°T  
Magnetic = 120 − 10 = **110°M**

Example: Declination = **−5° (5°W)**  
If True = 120°T  
Magnetic = 120 − (−5) = 120 + 5 = **125°M**

### Magnetic ↔ Compass (Deviation)
- **Compass = Magnetic − Deviation**
- **Magnetic = Compass + Deviation**

Example: Deviation = **+2° (2°E)**  
If Magnetic = 110°M  
Compass = 110 − 2 = **108°C**

Example: Deviation = **−3° (3°W)**  
If Magnetic = 110°M  
Compass = 110 − (−3) = 113 = **113°C**

---

## What the App Does

### 1) Declination
Enter:
- Latitude / Longitude (and optional altitude)
- Date (UTC)

Tap **Calculate Declination**.

### 2) Conversion (True / Magnetic / Compass)
Enter any ONE of:
- True (°T) OR Magnetic (°M) OR Compass (°C)

Tap **Convert** and the app fills in the other two using:
- Declination (from WMM)
- Deviation (from your table)

> Note: If you enter Compass (°C), the app estimates Magnetic (°M) by iterating a few times because deviation depends on heading. This is normal.

### 3) Deviation Table
Fill in deviation values every 15°.
You can:
- Save / Load profiles
- Export / Import JSON
- Print a **Deviation Card**

---

## Offline Model Updates (Optional)
You can import a newer **WMM JSON** model file (when available) so the app stays accurate offline.
- Imported model is stored in your browser (localStorage)
- Use **Reset** to return to built-in WMM-2025

---

## Safety Note
This tool is for convenience and training use.
Always verify navigation calculations against:
- Official sources (charts/publications)
- Your vessel’s current deviation card
- Practical checks underway

---

## Files
- `index.html` — main app (v1.1b baseline)
- `manifest.json` — PWA manifest
- `service-worker.js` — offline caching
- icons — app icons

