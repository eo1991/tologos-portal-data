# tologos-portal-data

Live data for the T.O. Logos customer order-tracking portal (https://track.tologos.com/).

- `portal-data-manifest.json` — current version: SHA-256 + chunk list for `portal-data.json`.
- `portal-data.partN.json` — chunks of `portal-data.json` (each <=3MB; pushed separately because the GitHub MCP request limit is ~4-5MB).
- `portal-data.json` itself is one JSON object `{version, scheme, blobs[]}`: one AES-256-GCM encrypted blob per job, keyed by that job's portal token. A customer with only their token can decrypt only their own blob; the file is public but unreadable without a token.

Updated automatically every 2 minutes by the portal live-sync job when content changes. Do not edit by hand.
