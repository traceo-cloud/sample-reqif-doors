# sample-reqif-doors

Public ReqIF samples in the shape of IBM DOORS (Classic) exports, with the
**fidelity receipt** [Traceo](https://traceo.cloud) writes when it reads them.

> **Read this first.** At least one file here is *shaped*: hand-written to resemble an export from IBM DOORS (Classic), not produced by it. A clean read of a shaped file shows that Traceo reads that shape. It does not show that Traceo reads what the tool really emits.

## Files

| File | Kind | Source | Licence | sha256 (prefix) |
|---|---|---|---|---|
| `doors_classic_user_export.reqif` | **export**: produced by the tool | [`strictdoc-project/reqif`](https://github.com/strictdoc-project/reqif/blob/b44fc51/tests/integration/reqif_software/Doors/02_example_from_a_user/sample.reqif) @ `b44fc51` | Apache-2.0 | `56179c470d10f94f` |
| `doors_classic_shaped_tidewater.reqif` | **shaped**: hand-written to look like the tool's export, *not* produced by it | [`jclements3/agile`](https://github.com/jclements3/agile/blob/fe93943/ps/practice/templates/tw-model/c2/imports/v1.0/tidewater.reqif) @ `fe93943` | MIT | `d22edcbffe71f554` |

- `doors_classic_user_export.reqif`: A user-contributed export from IBM Rational DOORS, anonymised. It has **no links**.
- `doors_classic_shaped_tidewater.reqif`: Hand-written in the shape of a DOORS 9.7 export. Its own header says: *"written by sim/tidewater-v1.pl in the shape of a DOORS 9.7 ReqIF 1.2 export. Fictional."*

Each file is copied byte-for-byte from the repository named and is unedited. Check it against the sha256.

## What Traceo kept

Traceo writes a receipt before it imports anything. The receipt counts every class of item **in**
the file and **kept**. It names every item it did not keep, with a reason code. A file with nothing
in it gets the verdict `vacuous`, never `clean`.

### `doors_classic_user_export.reqif`

Verdict: **lossy**, some items were not kept, and every one of them is named below.

| Class | In the file | Kept |
|---|---:|---:|
| objects | 3 | 3 |
| headings | 3 | 3 |
| attributes | 25 | 18 |
| hierarchy nodes | 3 | 3 |

Not kept, grouped by reason:

| Class | Reason | Count | Example detail |
|---|---|---:|---|
| attributes | `unmapped_attribute` | 7 | attribute on a SPECIFICATION |

Full receipt: [`receipts/doors_classic_user_export.reqif.receipt.json`](receipts/doors_classic_user_export.reqif.receipt.json)

### `doors_classic_shaped_tidewater.reqif`

Verdict: **clean**, every item in the file was kept.

| Class | In the file | Kept |
|---|---:|---:|
| objects | 35 | 35 |
| headings | 5 | 5 |
| attributes | 189 | 189 |
| enumeration values | 24 | 24 |
| link types | 1 | 1 |
| links | 24 | 24 |
| hierarchy nodes | 35 | 35 |

Full receipt: [`receipts/doors_classic_shaped_tidewater.reqif.receipt.json`](receipts/doors_classic_shaped_tidewater.reqif.receipt.json)

These receipts were written by Traceo's ReqIF importer at commit `90cfc15` on 2026-11-03.

## Try it

Traceo's import screen is not released yet. When it is, importing one of these files will show
this receipt before anything is written.

## Names

IBM DOORS (Classic) is a trademark of its owner. It is named here only to describe the file. Traceo is not
affiliated with or endorsed by its owner.

## Licence

The `.reqif` files are third-party and keep their upstream licence. The texts are in
[`LICENSES/`](LICENSES/). The README and the `receipts/` are © Traceo, released under the MIT
licence in [`LICENSE`](LICENSE).
