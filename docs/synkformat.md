# Synkformat

Bastion för Linux läser och skriver samma synkformat som de andra plattformarna. **Källan** till formatet är Swift-modellerna i [Bastion för Apple](https://github.com/pissmyran/bastion_apple).

## Fixturerna

`LinuxApp/tests/fixtures/` innehåller kopior av fixturerna i [Bastion för Apple](https://github.com/pissmyran/bastion_apple/tree/main/Tests/fixtures). Testerna i `host.rs` och `tool_release.rs` läser dem och visar att Rust-sidan kan avkoda formatet.

## När formatet ändras i Bastion för Apple

1. Kopiera de ändrade fixturerna från `Tests/fixtures/` i Bastion för Apple till `LinuxApp/tests/fixtures/`.
2. Uppdatera läsare och skrivare i `host.rs`, `snippet.rs`, `sync.rs` och `sync_crypto.rs`.
3. Kör testerna. Ändra aldrig en fixtur för att få ett test grönt.
