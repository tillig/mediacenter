===================
HP EX475 MediaSmart
===================

I bought an HP EX475 MediaSmart server with :doc:`Windows Home Server v1 <../../software/system/whs>` on it as my first foray into serving media and general media storage.

- 2GB RAM (upgraded)
- AMD Sempron Processor 3400+

Storage
=======

Current drive mappings (model / serial) - helpful in debugging issues:

- WD10EADS-00L5B1 / WCAU45460755 1TB WD Green Drive
- WD10EADS-00L5B1 / WCAU46152093 1TB WD Green Drive
- WD10EADS-00L5B1 / WCAU48489215 1TB WD Green Drive
- 500GB Samsung system drive

There is a defect in WHS where the serial number of the drives inside the EX475 gets misreported. Number pairs get transposed. For example:

- Real serial number: 12345678
- Reported serial number: 21436587

