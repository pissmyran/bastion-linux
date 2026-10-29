# RSA keys are disabled

Bastion for Linux does not connect with RSA keys right now. This applies to key files, certificates and keys in ssh-agent.

## Why

The SSH library russh uses the `rsa` crate for RSA. That crate has a known vulnerability, [RUSTSEC-2023-0071](https://rustsec.org/advisories/RUSTSEC-2023-0071) (the Marvin attack), with no fixed version. That is why russh's `rsa` feature is turned off in `LinuxApp/Cargo.toml`, and the crate is not in the dependency tree at all.

## What to do instead

Create an Ed25519 key and add the public part to the server:

```bash
ssh-keygen -t ed25519
```

Bastion can also add the key to the server for you.

## When RSA comes back

When `rsa` has a fixed version, the feature is turned on again in `LinuxApp/Cargo.toml`, together with tests for the RSA paths.
