# Drift och verifiering

## Före varje push

Det finns inga bygg- eller testkontroller i CI. Testerna nedan är den enda testgrinden, så de körs lokalt före varje push:

Installera byggberoenden (Debian och Ubuntu):

```bash
sudo apt install --no-install-recommends build-essential pkg-config libgtk-4-dev libadwaita-1-dev libvte-2.91-gtk4-dev libgtksourceview-5-dev openssh-client
```

Testa:

```bash
cd LinuxApp && cargo test --workspace
```

Kör appen:

```bash
cd LinuxApp && cargo run
```

## I CI

- **CodeQL** (GitHubs standardinställning) analyserar koden på varje pull request och på `main`. Fel och allvarliga säkerhetslarm stoppar merge.
- **Dokumentationen** byggs strikt med Zensical när `docs/` eller `zensical.toml` ändras i en pull request.
- **Releasen** väntar på kontrollerna i `.github/release-required-checks`; se [Release](release.md).


## Säkerhetsregler

- Privata nycklar, tokens och lösenord läggs aldrig i repot, i loggar eller i testdata.
- Värden som når ett skal citeras och skickas helst via `env:`.
- Ett beroende uppdateras i det manifest som faktiskt äger det.
