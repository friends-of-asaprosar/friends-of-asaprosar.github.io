# DB files from fox pro

## Important

- Glsku.dbf -- eyeglass inventory db
- Dispense.dbf -- containing a record of dispensed glasses
- Rdinv.dbf -- reader inventory db
- Rdtrak.dbf -- containing a record of dispensed readers

## Unsure

- Deleted.dbf -- a file of available numbers to be reused. _Created by the "Utilities" -> "Make file of available numbers" or by Export/Import -> "Import re-used numbers"_
- Glnxtno.dbf -- a file containing the next serial number to be used (glasses next number)
- Rdadd.dbf -- a file for recording additions to reader inventory
- Readd.dbf -- a file with data entered to replace used numbers

## Other not important stuff

- Bulog.dbf -- a log of backups – also contains the location of the clinic to appear in the window title if desired
- Notfound.dbf -- a file containing the Rx’s of unsuccessful searches
- Reimshlp.dbf -- the help file

## CDX (probably not important)

- Glsku.cdx -- the accompanying index file that allows the data to be displayed in the correct order
- Rdinv.cdx -- the accompanying index
- Readd.cdx -- the accompanying index

on cdx files: https://stackoverflow.com/q/3618633/4026792

## Helpful stuff

> SA and SM are the 2 sites

> There is no correlation between the SKU and the power of the glasses that is assigned to it (so the SKU can be generated automatically)

SKU= Stock keeping unit i.e. serial number
