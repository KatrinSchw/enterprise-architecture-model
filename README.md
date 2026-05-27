# Enterprise Architecture Model — ArchiHotel (C2F1G4)

ArchiMate model and project deliverables for the TUM BIE *Enterprise Architecture Management & Reference Models* study project, SoSe 2026.

- **Case:** C2 — [ArchiHotel](https://archihotel-eam.web.app/)
- **Focus Area:** F1 — Reservation Handling & Check-In
- **Group:** G4
- **Submission name:** `C2F1G4`

## Key dates

| Date | Milestone |
|---|---|
| 2026-05-28 | Team registration deadline |
| 2026-06-10 | Optional consultation |
| 2026-06-17 | How-to-present session |
| **2026-07-02 23:59** | **Submission deadline** |
| 2026-07-06 | On-site presentation (C.0.44, 15:20–17:30) |

## Repository layout

```
.
├── model/        ArchiMate model (Archi coArchi collaboration format)
├── exports/      PDF/PNG exports of views from Archi
├── slides/       Presentation deliverables (PPTX + PDF)
├── docs/         Modelling decisions, view notes, references
└── README.md
```

### `model/`
The ArchiMate model itself, serialised by Archi's **coArchi** collaboration plugin. **Do not edit these files by hand** — they are managed by Archi when you commit/push from inside the tool.

The two views required for submission:
1. **Abstract view** — whole-architecture overview of ArchiHotel
2. **Detailed view (F1)** — Reservation Handling & Check-In

### `exports/`
PDF and PNG exports of each view, generated from Archi (`File → Export → Image / PDF…`). Suggested naming:
- `exports/C2F1G4-abstract.pdf`
- `exports/C2F1G4-focus-area-1.pdf`

### `slides/`
Final presentation in both PPTX (working copy) and PDF (submission copy). Suggested naming: `C2F1G4-slides.pptx` / `.pdf`.

### `docs/`
Anything that explains *why* the model looks the way it does — element-mapping decisions, scope assumptions, references to lecture material, meeting notes. Lecture PDFs and the raw case content stay in `~/life-brain/uni/eam/` (out of the repo).

## Working with the ArchiMate model (Archi + coArchi)

This repo is connected to [Archi](https://www.archimatetool.com/) via the **coArchi** plugin. The `model/` folder is Archi's Git-friendly serialisation of a single `.archimate` model.

**One-time setup for a new collaborator:**
1. Install Archi (≥ 5.0).
2. Install the coArchi plugin: `Help → Install New Software → coArchi update site`.
3. In Archi: `File → Open Model from Collaboration Workspace → Clone` and point at this repo URL.

**Daily workflow (all inside Archi, not the terminal):**
- Refresh others' changes: model toolbar → **Refresh**.
- Push your changes: **Commit & Push** with a short message.

Avoid editing `model/*.xml` outside Archi — coArchi rebuilds them and your hand edits will be overwritten.

## Submission packaging

Final hand-in (per the project brief): a single archive named **`C2F1G4.zip`** (or `.rar`) containing:
- `.archimate` file exported from Archi (`File → Export → Archi Model File`)
- PDF of the abstract view
- PDF of the F1 detailed view
- `C2F1G4-slides.pdf`
- `C2F1G4-slides.pptx`

The submission archive itself is **not committed to the repo** (`.gitignore`d) — generate it fresh from `exports/` and `slides/` at submission time.

## Grading

10 exam points total: 5 for the models, 5 for the presentation. Team grade. Registered students drop one modelling task from the final exam.
