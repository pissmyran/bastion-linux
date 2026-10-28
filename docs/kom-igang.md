# Kom igång

## Förutsättningar

Rust (senaste stabila versionen) och GTK-utvecklingspaketen ovan.

## Bygg och testa

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

`openssh-client` behövs för att testerna av nyckelimport kör `ssh-keygen`. RPM-paketet byggs med `LinuxApp/packaging/build-rpm.sh`.

## Innehåll

| Plats | Innehåll |
| --- | --- |
| `LinuxApp/src/` | Appen: sessioner, terminal, SFTP, synk, vidarebefordran och verktyg |
| `LinuxApp/integrations/` | Integrationer, till exempel Docker |
| `LinuxApp/tests/fixtures/` | Kopior av synkformatets fixturer från Bastion för Apple |
| `LinuxApp/packaging/` | Skrivbordsfil och RPM-bygge |
