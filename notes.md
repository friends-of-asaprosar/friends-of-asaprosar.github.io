---
title: Notes & ideas
nav_order: 20
---

This is a page for meeting notes and all the ideas I had while exploring the current version of REIMS.

# Open Questions

1. Domain name? Who buys it?
2. Old source code https://github.com/jboreiko/reims-web ?
3. Stuff: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6431005/

# Ideas

Most of them are just nice-to-have and could be done after the rewrite as a QOL improvement.

- Lens measuring is done with digital devices as well, so it would be nice to automatically import it from there
- QR Code and prescription printing feature?
- Use Grafana for reports!
- Handwrite OCR with mobile phone for entering glasses
- Administration panel for adding new accounts

# Meeting notes 28.04.21

- bifocal = gleichsichtbrille
- progressive = no line bifocal (gleitsicht mit verlauf)

## in america

- empty slots refilled

- sorting by power also required / category: analyze the data/ run reports
- how many slots are empty

- max amount of glasses is limit for shipping

- Rx for right an dleft and additon portion optionally (for bifocal)
- person goes over to dispensing area
- software spits out 3 closest matches
- petient tries it out
- take SKU number and mark it as dispensed

- glasses should be entered with multiple persons
- there is an offline storage unit, where all glasses are stored
  - measeruement is taken before and is noted on the bags. then bags are selected and entered into the unit
- refill just on what's missing
- 0.25 reicht aus,
- readers: shipped seperately, not considered part of the 10k limit. nice-to-have aber nicht wichtig
- power limits within -8 and +8, most -6 and +6

- digital measurement not required
- numeric keypads currently used +1.2 wird zu +1.25
- sequence of fields is important

- we dont need the R-XX prefix

### on site

- pair of empty bags gets dispensed (in free time)
- 4 patients simultanoulsy, a few runner
- algo is in pdf
- also numpad
- fairly stable, with WiFi. offline support nice
- when no matches: track that search

## report

- nothing for PR purporses, nice to have
- mostly diane as well

- read only would be arlight, but write protection

- login with google would be alright

- administrator,
- make it comatpible for others

# Meeting notes 07.05.21

- single or multifocal, no seperation
- sphere + or - required 00.xx (xx are single digits)
- cyl default to minus one number dot one nmber rounding, (1 decimal)
- AXIS require three digits (including padding)
- addition default to +, never negative

- remove material

- sorting is extremely helpful
- type, od/os cly sphere
- Rx correct is much more important
- also have filtering on site

- deleting on site as well because sometimes bags are empty
- editing in table would be great, if you detect wrong entered glasses, most times on site

- no help text in UI required

- tab to swithc fields
- philscore explanation will follow

-

# Meeting notes 26.05.21 (PhilScore)

Either

1. Match Sphere +- Tolerance
2. Match Cyl +- Tolerance
3. Pass AtoLTF() - unclear what it means: Light Transmission Factor? Doesn't make sense

Or

1. Pass SPEQ()

Then

1. Rank using RANK()

## AtoLTF

Variables: zc (Lens cyl), zac (Lens Axis), za (desired axis)

Calculated: zat (calculated from Lens cylinder, it's some kind of mapping from the lens cyl to axis number range)

Test: Depending on (Lens axis +- desired axis)

Todo visualize!

## SPEQ

Variables: desired Sphere, desired Cylinder (_Axis in theory, but unused_)

Returns: An array of lower and upper bounds for cylinder and sphere values, depending on cylinder??

Calc: cn = lower bound for `n`th pair

sn = upper bound for `n`th pair

As soon as cn is greater null, discard that pair. First pair (cylinder+0.5, sphere-0.25), second (cylinder+1, sphere-0.5), third (cylinder+1.5, sphere-0.75)

**That doesn't seem right!** Upper bounds are less than lower bounds as soon as spheres are negative?

## PhilScore RANK()

Variables: desired sphere, cyl and add for OS and OD, measured sphere, cyl and add for OS and OD

Returns an index based on a lot of conditions

For RANK() see also https://github.com/jboreiko/reims-web/blob/58a412ef6185b83e2b5dde96f5bd800d2fb63ecb/app/records/eyeglassRecords.ts#L151-L172
