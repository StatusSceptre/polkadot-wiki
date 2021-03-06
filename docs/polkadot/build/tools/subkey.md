# Subkey

Subkey is a commandline utility included with Substrate that generates or restores Substrate keys. 

`subkey` will use the [sr25519](http://wiki.polkadot.network/en/latest/polkadot/learn/cryptography/#keypairs-and-signing) cryptography by default. If you need to use the older ed25519 cryptography to generate or restore your key pass the `--ed25519` flag to any of the commands.

## Usage

### Generate a random account

```bash
subkey generate
```

Will output a mnemonic phrase and give you the seed, public key, and address of a new account. DO NOT SHARE your mnemonic or seed with ANYONE it will give them access to your funds. If someone is making a transfer to you they will only need your **Address**.

### Inspecting a key

You can inspect a given URI (mnemonic, seed, public key, or address) and recover the public key and the address.

```bash
subkey inspect <mnemonic,seed,pubkey,address>

OUTPUT:
  Public key (hex): 0x461edcf1ba99e43f50dec4bdeb3d1a2cf521ad7c3cd0eeee5cd3314e50fd424c
  Address (SS58): 5DeeNqcAcaHDSed2HYnqMDK7JHcvxZ5QUE9EKmjc5snvU6wF
```

### Signing

`subkey` expects a message to come in on STDIN, one way to sign a message would look like this:

```bash
echo <msg> | subkey sign <seed,mnemonic>

OUTPUT:
a69da4a6ccbf81dbbbfad235fa12cf8528c18012b991ae89214de8d20d29c1280576ced6eb38b7406d1b7e03231df6dd4a5257546ddad13259356e1c3adfb509
```

### Verifying a signature

```bash
echo <msg> | subkey verify <sig> <address>

OUTPUT:
Signature verifies correctly.
```

### Using the vanity generator

You can use the included vanity generator to find a seed that provides an address which includes the desired pattern. Be warned, depending on your hardware this may take a while.

```bash
subkey vanity 1337
```
