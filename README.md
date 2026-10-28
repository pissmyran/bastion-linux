# Bastion för Linux

**Dokumentation:** [pissmyran.github.io/bastion_linux](https://pissmyran.github.io/bastion_linux/)

Bastion är en SSH-klient. Det här repot innehåller versionen för Linux med GTK 4, byggd med Rust, GTK 4, libadwaita, VTE och russh. Övriga plattformar har egna repon: [Bastion för Apple](https://github.com/pissmyran/bastion_apple), [Bastion för Windows](https://github.com/pissmyran/bastion_windows), [Bastion för Android](https://github.com/pissmyran/bastion_android).

## Innehåll

| Plats | Innehåll |
| --- | --- |
| `LinuxApp/src/` | Appen: sessioner, terminal, SFTP, synk, vidarebefordran och verktyg |
| `LinuxApp/integrations/` | Integrationer, till exempel Docker |
| `LinuxApp/tests/fixtures/` | Kopior av synkformatets fixturer från Bastion för Apple |
| `LinuxApp/packaging/` | Skrivbordsfil och RPM-bygge |

## Kom igång

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

## Mer

- [Dokumentationen](https://pissmyran.github.io/bastion_linux/) – kom igång, arkitektur, drift, synkformat och release
- [SECURITY.md](SECURITY.md) – rapportera en sårbarhet
- [CONTRIBUTING.md](CONTRIBUTING.md) – bidra
