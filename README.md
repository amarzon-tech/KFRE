# Kidney Care Plan (NSPC)

A single‑page web app for computing the **Kidney Failure Risk Equation (KFRE)** and exporting a clean, patient‑ready PDF — branded with the **NSPC** logo.

This repo includes a **two‑button workflow**:
- **Compute KFRE** — validates inputs and calculates 2‑year / 5‑year risk (North America calibration; UACR in mg/g).
- **Export PDF** — fills a minimal patient summary (logo, date, Age/Sex/eGFR/UACR, risks, short interpretation, disclaimer) and opens **Print → Save as PDF**.

---

## Files

- `nspc-kfre-two-buttons.html` — Main single‑file app (no external build step).
- `nspc-logo.png` — NSPC logo shown on page and on the PDF.
- `README.md` — This document.

> If you are using the fuller Kidney Care Plan page with charts and KDIGO heat map, your main file may be named `index-33.html`. The KFRE module and two‑button workflow are compatible with that layout as well.

---

## Quick Start

1. Put `nspc-kfre-two-buttons.html` and `nspc-logo.png` in the **same folder**.
2. Open the HTML file in Chrome/Edge/Safari.
3. Enter **Age, Sex, eGFR, UACR** (or paste a note and click **Parse from text**).
4. Click **Compute KFRE** to view 2‑yr / 5‑yr risks on screen.
5. Click **Export PDF** to generate the patient summary and save as PDF.

---

## Assumptions & Model

- **Calibration**: North America.
- **Units**: UACR in **mg/g**; creatinine in mg/dL; eGFR in mL/min/1.73m².
- **Intended population**: CKD **G3–G5** (eGFR < 60).
- **Equation**: 4‑variable KFRE (age, sex, eGFR, ln‑UACR).  
  Risk = 1 − S₀(t)^(exp(LP)), where LP combines centered terms for age, sex, eGFR, and ln‑UACR.

If eGFR is missing but the note contains **creatinine**, the app can estimate eGFR using **CKD‑EPI 2021 (race‑free)** once **Age** and **Sex** are set.

---

## Deploy to GitHub Pages

1. Create a new repo and add:
   - `nspc-kfre-two-buttons.html`
   - `nspc-logo.png`
   - `README.md`
2. Commit & push.
3. In the repo settings → **Pages** → set **Source** to `main` (or `master`) and **/ (root)**.  
4. Your page will be available at `https://<your-username>.github.io/<repo-name>/nspc-kfre-two-buttons.html`.

To use as a homepage, simply rename the file to **`index.html`**.

---

## Editing on macOS (TextEdit tip)

- Use **Format → Make Plain Text** before pasting code.  
- Save as `index.html` (ensure it’s not `index.html.txt`).

---

## Troubleshooting

- **Logo doesn’t show**: Ensure `nspc-logo.png` is in the **same folder** and the filename matches exactly.
- **No numbers after Compute**: Confirm all four inputs are numeric; KFRE only reports for eGFR < 60.
- **“Parse from text” didn’t fill fields**: Parsing is optional; enter values manually and compute.
- **Nothing prints on PDF**: In some browsers, pop‑up/print dialogs may be blocked; allow the print dialog for this page.
- **Safari/local file security**: If inline JS is blocked locally, host the file (e.g., GitHub Pages) and it will run normally over HTTPS.

---

## Disclaimer

This tool supports **education and shared decision‑making** and is **not** a diagnostic device. It does not replace clinical judgment. For emergencies, call **911**.

© 2025 Nephrology Specialists, P.C.
