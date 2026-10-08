# Third-party notices

Mifare Windows Tool (MWT) is proprietary freeware (see [LICENSE](LICENSE)).
It bundles or runs the open-source components listed below. Each component
remains under its own license, and the full license texts are shipped in the
[`licenses`](licenses) folder of every release ZIP.

## Components and source code

| Component | Used as | License | Source code |
|---|---|---|---|
| **libnfc** (modified fork) | DLL loaded by MWT and the NFC tools | LGPL v3 | <https://github.com/xavave/libnfc_with_extra_tools> (upstream: <https://github.com/nfc-tools/libnfc>) |
| **libnfc utilities** (`nfc-mfclassic` with `-s` / `-t` options, `nfc-list`, ...) | Separate command-line programs | BSD 2-Clause | <https://github.com/xavave/libnfc_with_extra_tools> (`utils/`) |
| **mfoc-hardnested** (modified fork, static-nonce diagnostic) | Separate command-line program | GPL v2 or later | <https://github.com/xavave/mfoc-hardnested-and-static-nonce> (upstream: <https://github.com/nfc-tools/mfoc-hardnested>) |
| **libusb-1.0** | DLL (`libusb-1.0.dll`) loaded by libnfc and mfoc-hardnested | LGPL v2.1 | <https://github.com/libusb/libusb> |

License texts: [`licenses/`](licenses)

## How these components are used

- **LGPL libraries (libnfc, libusb)** are distributed as separate, dynamically
  loaded DLLs. You may replace them with your own modified builds. They are
  never compiled into the MWT executable.
- **GPL program (mfoc-hardnested)** is a standalone executable started by MWT
  as a separate process. Its code is not linked into MWT, and the complete
  corresponding source code is available at the link above.
- The modifications made to libnfc and mfoc-hardnested are published in the
  forks listed above, under the same licenses as the original projects.

## Maintainer checklist (for each release)

- [ ] The ZIP contains the `licenses` folder, up to date with the bundled components.
- [ ] Every bundled third-party binary is listed in the table above, with a link to its source.
- [ ] The source repositories linked above contain the exact code the shipped binaries were built from (push or tag it before publishing the release).
- [ ] libnfc and libusb are shipped as DLLs, never statically linked into the MWT executable.
- [ ] MWT calls mfoc-hardnested only as a separate process, and no GPL code is linked into MWT.
- [ ] Any new third-party component is added to this file and to `licenses/` before release.
