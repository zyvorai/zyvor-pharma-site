# Zyvora Pharmacy Workspace

A pharmacy counter and stock system for India: sell with GST, keep stock by batch and expiry, and keep the
controlled-drug register. One codebase runs as a desktop app (macOS, Windows, Linux) and as a web app on Kubernetes.

**Try it: <https://zyvorai.github.io/zyvor-pharma-site/demo/>**
The demo runs entirely in your browser with made-up data. Nothing is sent anywhere and it resets when you reload.
Never type real patient or business data into it. The source code is private; this repository holds the demo and
this page.

## What it does

- **Sales counter.** Search or scan, build a basket, check out. MRP is GST-inclusive; the bill splits CGST and SGST per rate.
- **Barcode scanning.** Any USB or Bluetooth scanner that types like a keyboard. Product numbers are check-digit verified,
  GS1 DataMatrix packs name their batch and expiry, and an expired pack is never added.
- **Batches and expiry.** Stock is sold earliest-expiry-first; expiring and expired batches are flagged; reorder suggestions
  and draft purchase orders.
- **Schedule H, H1 and X.** Schedule H needs a pharmacist's prescription check. H1 and X need a recorded, approved prescription
  with the patient's address and the prescriber's registration number, and each sale is written to the controlled-drug register.
- **Controlled-drug register.** Append-only and hash-chained, so a changed or removed entry is detected and pinpointed;
  exportable as CSV for an inspector.
- **Bills.** Print or reprint a tax invoice or cash memo with batch and expiry on every line, through any printer with a driver.
- **Catalogue.** Add and edit products (barcode, schedule, GST rate, MRP) and receive stock by batch, with every change checked.
- **People.** Sign-in per person with cashier, pharmacist and admin roles, an audit log, and encrypted backups.

## Where it runs

| | |
|---|---|
| Desktop | Tauri app with a local SQLite database; works offline. |
| Web | Fastify API on PostgreSQL behind an nginx web tier; Docker images and a Helm chart for Kubernetes. |

## Honest limits

- This is software, not a compliance certificate. Check the register format, record retention and bill content against
  your state's rules and your licence conditions before relying on it.
- Barcode scanning and bill printing are tested with simulated input. They have not yet been verified on real scanner
  or thermal printer hardware.
- Not built yet: receiving stock by scanning, camera scanning, stock write-offs and corrections, discontinuing a product,
  raw thermal-printer commands, two-factor sign-in.

## Contact

Open an issue on this repository.

© Zyrona Labs. The demo is provided for evaluation only.
