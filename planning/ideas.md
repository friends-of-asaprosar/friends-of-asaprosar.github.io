---
title: Idea collection
parent: Planning
---

# Ideas and notes for the new system

This is a page for all the ideas I had while exploring the current version of REIMS. Most of them are just nice-to-have and could be done after the rewrite as a QOL improvement.

- Split the application into features:

  - Entering new Rx (online connection required),
  - Searching & dispensing (must work without full connection)
  - Generating reports after a campaign (maybe Grafana or sth like that)

- Two kinds of prescriptions (Rx): readers & glasses

- QR Code and prescription printing feature?

# Meeting notes

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

- see excel
- export to excel for analysis
- inbetween on site and entering
- nothing for PR purporses, nice to have
- mostly diane as well

- backups

- read only would be arlight, but write protection

- login with google would be alright

- administrator,
- make it comatpible for others
