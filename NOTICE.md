# Licenses & sources

Release images contain software under many licenses (GPL-2.0, Apache-2.0, MIT, BSD and others).

- **Linux kernel (GPL-2.0).** Built from the LineageOS / switchroot kernel repositories at the exact revisions in
  [`patches/kernel-revisions.txt`](patches/kernel-revisions.txt), plus our changes in [`patches/kernel`](patches/kernel).
- **Android / LineageOS (Apache-2.0 and others).** LineageOS 22.2 plus our changes in [`patches`](patches)
  (`frameworks`, `packages`, `device`, `hardware`, `lineage-sdk`, `vendor`).
- **Ubuntu packages** are unmodified binaries from the Ubuntu archive; their sources are available from Ubuntu.

If you need a source for something in the release that is not listed here, open an issue — we will publish it.

TriggerOS contains no Nintendo firmware, keys or other Nintendo content.
