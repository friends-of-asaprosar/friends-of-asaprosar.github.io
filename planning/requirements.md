---
title: Requirements
parent: Planning
nav_order: 2
---

# Requirements

## Backend

### Endpoints

- Adding new glasses. This should return a unique SKU that was not in use (i.e. the previous glasses in that slot were dispensed).
- Recording glasses as dispensed (and optionally an undo function for that)
- Deleting entries from DB so that it's possible to remove wrongly-entered entries completely (and not just mark them as dispensed).
- Optional: Modifying existing data so that it's possible to correct wrongly entered data. This is rarily needed and could also be done via delete+add for now.
- Returning all active (i.e. non dispensed) glasses so that it's possible to work w/o internet connection on site. Optionally make that endpoint searchable/sortable but we'll probably do that on client-side.
- Optional: Saving failed matches so that it's possible to analyze what type of glasses were often required but not available. For this the frontend will report to the backend what was missing and it's simply stored.

### General considerations

- Data has to be write-protected

  - Read is not that important, since there is no personal data
  - Login via Google Account or other 3rd parties would be okay

- It should never be possible to have the same SKU for two active (i.e. non dispensed) glasses.

## Data format

_See PDF "Working with REIMS to find glasses" for a detailled explanation_

Data for every entry:

- `Type` can be single (standard glasses), bifocal (single, but with a different lens power at the bottom) or progressive (bifocal, but with a smooth transition. German: "Gleitsichtbrille"). In the future, reader (simple reading glasses with `Sphere` only should be possible as well).
- `Size` can be small, medium, large, child
- `Appearance` can be neutral, feminine or masculine
- `Material` optional, can be metal or plastic

The following data is stored for **each** eye (OD=right eye, OS=left):

- `Sphere`/lens power in diopters. Negative numbers means near sighted, positive is far sighted. Range from -20 to +20 in 0.25 increments.
- `Cylinder` Lens power to correct astigmatism (German: "Hornhautverkrümmung"). Range from 0 to -6 in 0.25 increments.
- `Axis` Also some value to correct astigmatism. Range from 1 to 180 in 1 increments.
- `Add` **only for bifocal or progressive lenses**, this described the lens power of the additional bottom lens. Range from 0.25 to 4 in 0.25 increments.

## Frontend

General:

- Everything should be usable via keyboard/numpad only as it's the current workflow.
- The current sequence (of tabbing) fields should be kept.
- Mobile usage is not required, since numpad is much faster.

Entering data:

- Return SKU after data entry so that it's easier to implement the backend no duplicates logic.
- Round to the data increments automatically.

## General / other

- System might be reused from other initiatives in the world, so it's preferred to make the branding customizable and the code easy to setup & modular
