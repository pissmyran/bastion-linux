# Arkitektur

Bastion för Linux är en fristående Rust-app. Den delar ingen kod med de andra plattformarna, men läser och skriver samma synkformat som Bastion för Apple.

```text
        +------------------------------+
        |   GTK 4 + libadwaita + VTE   |
        +---------------+--------------+
                        |
        +---------------+--------------+
        |  LinuxApp/src (Rust, tokio)  |
        |  ssh, sftp, sync, forwarding |
        +---------------+--------------+
                        |
                 russh, reqwest
```

## Delar

- **SSH** går genom russh. RSA-stödet är avstängt i russh eftersom `rsa`-craten har en olöst sårbarhet (RUSTSEC-2023-0071); se kommentaren i `LinuxApp/Cargo.toml`.
- **Synk** (`sync.rs`, `sync_crypto.rs`, `sync_webdav.rs`) följer formatet från Bastion för Apple. WebDAV-uppgifter skickas bara över HTTPS eller till uttryckligen tillåten loopback.
- **Verktyg** som Tailscale hämtas av `external_binary_fetcher.rs` och kontrolleras mot SHA256 innan de används.

## Säkerhetsgräns

Värdnyckelkontrollen i `known_hosts.rs` avvisar en ändrad nyckel för samma värd och port. Nycklar och lösenord lagras aldrig i repot eller i testdata.
