---
title: Requirements
parent: Planning
---

# Requirements for the new system

## User stories

### Process on site

#### Process description

Patient with bad sight visits the clinc in El Salvador and in best case leaves with matching glasses.

1. Check-up by a doctor, who measures eye sight
   - most time-consuming task here
2. If glasses are deemed neccessary, they get a sheet of paper with their Rx/diagnosis written on it
   - Rx means Prescription means which type of glasses are required (more on the exact required types below)
3. Patient proceeds to the next station, where he gives his Rx to the computer person
4. Rx is entered into the program (mostly with a USB numpad only). The program outputs the 3 best fitting glasses and their SKU (serial number).
5. Some other guy fetches the 3 glasses from the storage. The glasses are sorted by SKU in boxes.
   - Meanwhile, the computer person might repeat step 4 for other patients simultanously, so other guys can fetch their best matching glasses as in step 5 simultanously
6. The patient tries out the 3 glasses and pick their favorite. They leave the clinic with the glasses.
7. The empty plastic bag, which the glasses were in, is stored in a seperate "dispensed" container. The computer person records them as "dispensed" in the DB as soon as he has some time inbetween.

### Back in America

#### Process description

A person in America has to refill the glasses inventory.

1. The donated glasses from all over America are collected. Glasses are cleaned and measured. All glasses are stored in a plastic bag with the measured Rx written on them. Those glasses are not yet recorded inside the DB, as it'd be too tedious to enter all of those in a DB.
2. They analyze what glasses are currently in inventory and what glasses should be preferred for refill.
   - This is done by manual analysis of the dispensed and current glasses with excel, combined with their knowledge about the most common Rx's. More on that later.
3. They pick new glasses for entering to inventory and enter them into the program (mostly with a USB numpad only).
   - It should be possible to do this step and the next one with multiple people simultanously all over America.
4. The program outputs the selected SKU and the person writes it also on the plastic bag.
   - The SKU is selected simply by the next free slot, which was open after the dispensing in the last campaign.
5. This process is repeated until all 10k glasses are refilled again.

## Questions

1. Is it required to manually delete glasses from inventory sometimes back in America?
