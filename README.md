# Ino Hub: connector store catalog

This repository holds the catalog of connectors that Tryino has reviewed and approved for [Ino Loyalty](https://inoloyalty.com).

- `catalog.envelope.json` is the signed catalog that Ino Loyalty engines and the `ino` command line read. Only Tryino's signing key (ECDSA P-256, kept in a hardware-backed key vault) can produce an accepted signature; an edited or unsigned file is ignored.
- `catalog/<id>.json` holds one approved connector each; `catalog/withdrawn.json` lists withdrawn ones.

## Submitting a connector
Write it with `ino connector new`, run the compatibility check (`ino connector check`), push it to a public repository with an open-source licence, then run:

```
ino hub submit --company "<company>" --contact-name "<name>" --contact-email "<address>" --dry-run
ino hub submit --company "<company>" --contact-name "<name>" --contact-email "<address>" --yes
```

The submission goes to Tryino privately. Tryino reviews and tests the exact commit you submit; nothing appears in the store until Tryino approves it. Please do not open issues or pull requests here to submit.

## Using an approved connector
`ino hub list`, `ino hub show <id>` and `ino hub get <id>` (prints the commands that fetch the exact approved commit from Tryino's mirror). In Power Apps: Settings → Integrations → Connectors → Add connector → From the store.
