---
title: Requirements
parent: Planning
---

# Requirements

## General / other

- System might be reused from other initiatives in the world, so it's preferred to make the branding customizable and the code easy to setup & modular

## Backend

- Data has to be write-protected

  - Read is not that important, since there is no personal data
  - Login via Google Account or other 3rd parties would be okay

### Data format

_See PDF "Working with REIMS to find glasses" for a detailled explanation_

Shorthand explanation:

- Rx = Prescription = A pair of glasses descriped by its parameters like strength and others
- OD = right eye
- OS = left eye
- Readers = glasses with near vision only (i.e. only two parameters for strengths of both eyes)

Data for every Rx:

- _Type_, can be single (standard glasses), bifocal (single, but with a different lens power at the bottom) or progressive (bifocal, but with a smooth transition. German: "Gleitsichtbrille"). In the future, reader (simple reading glasses with _Sphere_ only should be possible as well).
- _Size_, can be small, medium, large, child
- _Appearance_, can be "neutral", "feminine" or "masculine"
- _Material_, optional, can be metal or plastic

The following data is stored for **each** eye:

- _Sphere_/lens power in diopters. Negative numbers means near sighted, positive is far sighted. Range from -20 to +20 in 0.25 increments.
- _Cylinder_: Lens power to correct astigmatism (German: "Hornhautverkrümmung"). Range from 0 to -6 in 0.25 increments.
- _Axis_: Also some value to correct astigmatism. Range from 1 to 180 in 1 increments.
- _Add_: **only for bifocal or progressive lenses**, this described the lens power of the additional bottom lens. Range from 0.25 to 4 in 0.25 increments.

_Program should round to the increments automatically._

## Frontend

- Everything should be usable via keyboard/numpad only as it's the current workflow.
- The current sequence (of tabbing) fields should be kept.
- Mobile usage is not required, since numpad is much faster.
