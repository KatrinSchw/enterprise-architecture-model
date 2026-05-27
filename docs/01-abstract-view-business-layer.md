# Build guide — Abstract view, Business layer

**For:** ArchiHotel C2F1G4 abstract whole-architecture view.
**Layer scope of this guide:** Business layer only (🟡). Application + Technology layers come in `02-` and `03-` build guides.
**Where this happens:** **All steps below are done inside Archi**, not in the terminal. coArchi syncs the `model/` directory automatically when you commit + push from Archi.

---

## A. Setup (do once, ~5 min)

- [ ] **Open the model in Archi** via coArchi (`File → Open Model from Collaboration Workspace`).
- [ ] **Rename the model** to `ArchiHotel EA` (in the Models tree, double-click the model name or use the Properties panel).
- [ ] **Rename the existing view** from `Default View` to `Abstract — ArchiHotel EA` (in the Views folder, right-click → Rename).
- [ ] **Delete the two placeholder elements** that came with the new model:
  - the `Business Function` named "Business Function"
  - the `Business Object` named "Business Object"
  - Use **right-click → "Delete from model"** (or **Shift+Delete**) — *not* plain Delete, which only removes from the view.
- [ ] Confirm: the view is empty, named correctly, and the Business folder in the tree has no leftover elements.

## B. Conventions to apply throughout

- **Labels are noun phrases for structure** (Actor, Role, Interface, Service, Object) and **verb phrases for processes** (*Handle Reservation*, not *Reservation Handling*).
- Leave the **colour rule alone** — Archi colours by layer automatically.
- Use the **Magic Connector** (top of the palette) when adding relationships — it only offers legal ArchiMate pairings, which catches modelling mistakes.
- Save (`Ctrl/Cmd-S`) after each major step. Archi sometimes crashes.

---

## C. Drop the business-layer elements onto the view

Add elements by dragging from the palette onto the canvas. Layout target: **three vertical columns** for F1 (left), F2 (centre), F3 (right). Within each column, top-to-bottom: actors/roles → collaboration → interfaces → services → processes → objects. Cross-cutting elements (Guest, Guest Profile, Open Costs) go on the far left / bottom.

For each table below: drop one element per row, naming it exactly as written.

### C.1 External actors (cross-cutting)

| Element name | ArchiMate type | F-area | Layout hint |
|---|---|---|---|
| Guest | Business Actor | X | Far left of canvas, top |

### C.2 Internal business roles

| Element name | ArchiMate type | F-area | Layout hint |
|---|---|---|---|
| Receptionist | Business Role | F1 | F1 column, top row |
| Hotel Manager | Business Role | F2 | F2 column, top row, left |
| Housekeeping | Business Role | F2 | F2 column, top row, centre |
| Concierge | Business Role | F3 | F3 column, top row, left |
| Driver | Business Role | F3 | F3 column, top row, right |

### C.3 Business collaboration

| Element name | ArchiMate type | F-area | Layout hint |
|---|---|---|---|
| Daily Briefing Team | Business Collaboration | F2 | F2 column, below the roles |

### C.4 Business interfaces (points of access)

| Element name | ArchiMate type | F-area | Layout hint |
|---|---|---|---|
| Web Booking Interface | Business Interface | F1 | F1 column, interface row, left |
| External Booking Platform Interface | Business Interface | F1 | F1 column, interface row, centre |
| Reception Desk | Business Interface | F1 | F1 column, interface row, right |
| Staff Portal | Business Interface | F2 | F2 column, interface row |
| Concierge Desk | Business Interface | F3 | F3 column, interface row, left |
| In-Room Telephone | Business Interface | F3 | F3 column, interface row, centre |
| WeWash App Interface | Business Interface | F3 | F3 column, interface row, right |

### C.5 Business services

| Element name | ArchiMate type | F-area | Layout hint |
|---|---|---|---|
| Reservation Service | Business Service | F1 | F1 column, service row, left |
| Check-In / Check-Out Service | Business Service | F1 | F1 column, service row, right |
| Daily Briefing Service | Business Service | F2 | F2 column, service row, left |
| Room Access Service | Business Service | F2 | F2 column, service row, centre |
| Energy Saving Service | Business Service | F2 | F2 column, service row, right |
| Concierge Assistance Service | Business Service | F3 | F3 column, service row, left |
| Laundry Service | Business Service | F3 | F3 column, service row, centre |
| Transfer Service | Business Service | F3 | F3 column, service row, right |

> ⚠️ *Daily Briefing Service* and *Energy Saving Service* may need to become **Business Functions** instead of Services once L06 is taught (Functions are internal, Services are externally consumed). Add as Service for now; flag for re-check after L06.

### C.6 Business processes

| Element name | ArchiMate type | F-area | Layout hint |
|---|---|---|---|
| Handle Reservation | Business Process | F1 | Below Reservation Service |
| Conduct Check-In/Check-Out | Business Process | F1 | Below Check-In/Out Service |
| Conduct Daily Briefing | Business Process | F2 | Below Daily Briefing Service |
| Grant Room Access | Business Process | F2 | Below Room Access Service |
| Manage Room Energy | Business Process | F2 | Below Energy Saving Service |
| Provide Concierge Assistance | Business Process | F3 | Below Concierge Assistance Service |
| Provide Laundry | Business Process | F3 | Below Laundry Service |
| Provide Transfer | Business Process | F3 | Below Transfer Service |

### C.7 Business objects (passive)

| Element name | ArchiMate type | F-area | Layout hint |
|---|---|---|---|
| Reservation | Business Object | F1 | F1 column, bottom row, left |
| Pricing Information | Business Object | F1 | F1 column, bottom row, centre |
| Room Availability | Business Object | F1 | F1 column, bottom row, right |
| Arrival Schedule | Business Object | F2 | F2 column, bottom row, left |
| VIP List | Business Object | F2 | F2 column, bottom row, centre |
| Briefing Report | Business Object | F2 | F2 column, bottom row, right |
| Special Request | Business Object | F3 | F3 column, bottom row, left |
| Transfer Booking | Business Object | F3 | F3 column, bottom row, centre |
| Laundry Booking | Business Object | F3 | F3 column, bottom row, right |
| Guest Profile | Business Object | X | Below F1/F2 columns, cross-cutting band |
| Open Costs | Business Object | X | Below F2/F3 columns, cross-cutting band |

**Element count check:** 1 + 5 + 1 + 7 + 8 + 8 + 11 = **41 business-layer elements**. Verify the count in the Business folder before moving on.

- [ ] All 41 elements created in the Business folder.
- [ ] All 41 placed on the *Abstract — ArchiHotel EA* view.
- [ ] Save model (`Ctrl/Cmd-S`).

---

## D. Add the internal business-layer relationships

Use the **Magic Connector** in the palette. Click the source element first, then the target. Archi will offer only relationships valid for that pairing.

### D.1 Role-to-process assignment (●———▶)

The role *performs* the process.

| Source (Role/Collab) | Relationship | Target (Process) |
|---|---|---|
| Receptionist | Assignment | Handle Reservation |
| Receptionist | Assignment | Conduct Check-In/Check-Out |
| Daily Briefing Team | Assignment | Conduct Daily Briefing |
| Housekeeping | Assignment | Grant Room Access |
| Concierge | Assignment | Provide Concierge Assistance |
| Concierge | Assignment | Provide Transfer |
| Driver | Assignment | Provide Transfer |

Notes:
- *Manage Room Energy* has no assigned role — it's automated by the key-card switch; OK to leave unassigned in the abstract view.
- *Provide Laundry* has no assigned role — guests use the WeWash app themselves; OK to leave unassigned.

### D.2 Role aggregation into Daily Briefing Team (◇———)

The Daily Briefing Team is **composed of** the Hotel Manager + Housekeeping + Concierge leads (per the case text).

| Source (Collaboration) | Relationship | Target (Role) |
|---|---|---|
| Daily Briefing Team | Aggregation | Hotel Manager |
| Daily Briefing Team | Aggregation | Housekeeping |
| Daily Briefing Team | Aggregation | Concierge |

### D.3 Process realises Service (· · ·▷)

Each process *realises* the service it provides.

| Source (Process) | Relationship | Target (Service) |
|---|---|---|
| Handle Reservation | Realisation | Reservation Service |
| Conduct Check-In/Check-Out | Realisation | Check-In / Check-Out Service |
| Conduct Daily Briefing | Realisation | Daily Briefing Service |
| Grant Room Access | Realisation | Room Access Service |
| Manage Room Energy | Realisation | Energy Saving Service |
| Provide Concierge Assistance | Realisation | Concierge Assistance Service |
| Provide Laundry | Realisation | Laundry Service |
| Provide Transfer | Realisation | Transfer Service |

### D.4 Service is exposed via Interface — composition (◆———)

The interface is *part of* the service offering.

| Source (Service) | Relationship | Target (Interface) |
|---|---|---|
| Reservation Service | Composition | Web Booking Interface |
| Reservation Service | Composition | External Booking Platform Interface |
| Check-In / Check-Out Service | Composition | Reception Desk |
| Daily Briefing Service | Composition | Staff Portal |
| Concierge Assistance Service | Composition | Concierge Desk |
| Concierge Assistance Service | Composition | In-Room Telephone |
| Laundry Service | Composition | WeWash App Interface |
| Transfer Service | Composition | Concierge Desk |

> *Concierge Desk* is the access point for both Concierge Assistance and Transfer — model it once and let two services compose it.

### D.5 Actor serves through Interface (———▶)

The interface *serves* the consumer.

| Source (Interface) | Relationship | Target (Actor / Role) |
|---|---|---|
| Web Booking Interface | Serving | Guest |
| External Booking Platform Interface | Serving | Guest |
| Reception Desk | Serving | Guest |
| Concierge Desk | Serving | Guest |
| In-Room Telephone | Serving | Guest |
| WeWash App Interface | Serving | Guest |
| Staff Portal | Serving | Receptionist |
| Staff Portal | Serving | Concierge |
| Staff Portal | Serving | Housekeeping |
| Staff Portal | Serving | Driver |
| Staff Portal | Serving | Hotel Manager |

> The Staff Portal serves multiple internal roles — that's intentional, it's the single shared dashboard.

### D.6 Process accesses Business Object (· · ·▶)

Set the **access type** explicitly via the Properties panel after creating each access (Read / Write / Read-Write).

| Source (Process) | Access type | Target (Object) |
|---|---|---|
| Handle Reservation | R/W | Reservation |
| Handle Reservation | Read | Pricing Information |
| Handle Reservation | Read | Room Availability |
| Handle Reservation | R/W | Guest Profile |
| Handle Reservation | Write | Open Costs |
| Conduct Check-In/Check-Out | R/W | Reservation |
| Conduct Check-In/Check-Out | R/W | Open Costs |
| Conduct Daily Briefing | Read | Arrival Schedule |
| Conduct Daily Briefing | Read | VIP List |
| Conduct Daily Briefing | R/W | Briefing Report |
| Conduct Daily Briefing | Read | Special Request |
| Provide Concierge Assistance | R/W | Special Request |
| Provide Transfer | R/W | Transfer Booking |
| Provide Transfer | Write | Open Costs |
| Provide Laundry | R/W | Laundry Booking |
| Provide Laundry | Write | Open Costs |

**Relationship count check:** 7 + 3 + 8 + 8 + 11 + 16 = **53 business-layer relationships**. Some are also visible on adjacent areas (e.g. Staff Portal serving 5 roles spreads across the diagram).

- [ ] All 53 relationships drawn.
- [ ] All access relationships have the access type set in Properties.
- [ ] No "ghost" relationships left from accidental clicks (check the Relations folder for anything with an empty name).
- [ ] Save model.

---

## E. Commit + push from Archi via coArchi

- [ ] In Archi: switch to the **Collaboration view** (or click the coArchi icon in the toolbar).
- [ ] **Commit & Push** with message: `feat(abstract): business layer — 41 elements, 53 relationships`.
- [ ] Confirm on GitHub that `master` has a new commit and `model/business/` contains 41 new files.

---

## F. What's intentionally not in this guide (yet)

- **No Application or Technology layer elements** — they live in build guides `02-` and `03-`.
- **No layout polish** (alignment, spacing, line bending) — do a final cosmetic pass after all three layers are in.
- **No internal application structure** (sub-components, application interfaces) — those belong only in the detailed F1 view, not the abstract.
- **No payment routing** through External Payment Service yet — that's an application-layer relationship between HMS and the external payment component, added in guide `02-`.
- **No External Cleaning Service** — out of scope per draft open-question 6.
- **Behaviour-element type (Service vs. Function)** for *Daily Briefing* and *Energy Saving* — re-check after L06 lecture.

## G. Open questions still parked for the team

Pulled from `notes/abstract-model-draft.md` — these are decisions the team should make before the model goes to consultation on 2026-06-10. Until decided, the choices in this guide are provisional defaults.

1. External Booking Platform & External Payment Service — treat as Business Actors (orgs) or Application Components only? *(Guide treats them as Application Components, added in guide 02-.)*
2. Keep Energy Management System separate from Door System Software at application layer, or merge?
3. Daily Briefing Team — Business Collaboration (current default) vs. Business Interaction only?
4. In-Room Equipment as one Node vs. split (door reader / phone / energy switch)?
5. Open Costs — cross-cutting vs. F1-owned?
6. External Cleaning Service — drop entirely (current default) vs. keep as an F3 fallback actor?
7. Service vs. Function for *Daily Briefing* and *Energy Saving* — re-check after L06.
8. One Online Booking Service realised by two Application Components vs. two parallel services?
