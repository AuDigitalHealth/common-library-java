# Security

## Reporting issues

Report security-sensitive findings through your organisation's usual channel for **ADHA / AuDigitalHealth** repositories (do not open a public issue with exploit details before it is triaged).

## This repository

- **Do not commit secrets to git.** That includes passwords, API tokens, private keys, real mutual-TLS keystores, production or staging endpoint URLs with embedded credentials, and Services Australia / vendor registration material - even inside comments, test fixtures, or tracked documentation.
- **`local.properties`** is gitignored. Never commit real credentials or keystores.
- **`settings.xml`** at the repository root is gitignored when it contains release credentials; do not commit populated copies. Use **`settings.xml.example`** as the template (server id **`central`**).
- In property files, prefer **forward slashes** in filesystem paths so the same values work on **Windows**, **macOS**, and **Linux**.
