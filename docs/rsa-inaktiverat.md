# RSA-nycklar är inaktiverade

Bastion för Linux ansluter inte med RSA-nycklar just nu. Det gäller nyckelfiler, certifikat och nycklar i ssh-agent.

## Varför

SSH-biblioteket russh använder craten `rsa` för RSA. Den har en känd sårbarhet, [RUSTSEC-2023-0071](https://rustsec.org/advisories/RUSTSEC-2023-0071) (Marvin-attacken), som saknar rättad version. Därför är russh:s `rsa`-funktion avstängd i `LinuxApp/Cargo.toml`, och craten finns inte alls i beroendeträdet.

## Vad du gör i stället

Skapa en Ed25519-nyckel och lägg in den publika delen på servern:

```bash
ssh-keygen -t ed25519
```

Bastion kan också lägga in nyckeln på servern åt dig.

## När kommer RSA tillbaka

När `rsa` har en rättad version slås funktionen på igen i `LinuxApp/Cargo.toml`, tillsammans med tester för RSA-vägarna.
