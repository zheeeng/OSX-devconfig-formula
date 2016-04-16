# GPG

> GnuPG (GNU Privacy Guard) is a free software replacement for [PGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy), it includes keypair creation, exchanging and verifying keys, encrypting and decrypting documents, and authenticating documents with digital signatures.

## Installation

    brew install gpg

## Generating a GPG Key

    gpg --gen-key

You cloud identify each public by `<key-id>`. In keypair generating, instruction prompts ask your `your_name`, `your_email@example.com`, `key comment` and a `passphrase`. The `<key-id>` will finally look like `"your_name (key comment) <your_email@example.com>"`.

## Other common Usage

```shell
# Generate fingerprint:
gpg --fingerprint <key-id>
# Display keys or only secret keys:
gpg --list-keys
gpg --list-secret-keys
# Delete secret or public key (secret deletion must before its public key deletion):
gpg --delete-secret-key <key-id>
gpg --delete-key <key-id>
# Export public and secret key with ASCII:
gpg --armor --export <key-id> > public.key
gpg --armor --export-secret-keys <key-id> > private.key
# Import public key file:
gpg --import <publick.key>
# Encrypt and Decrypt file:
gpg --recipient <key-id> --encrypt file --output file.gpg
gpg --decrypt file.gpg --output file
```

*More docs on: <https://www.gnupg.org/gph/en/manual.html>*

# SSH

> Secure Shell, or SSH, is a cryptographic (encrypted) network protocol operating at layer 7 of the OSI Model to allow remote login and other network services to operate securely over an unsecured network.

## Usage

```shell
# Logoin a host:
ssh [-p port] user@host
# Run commands and on remote machine and print the output locally through ssh:
ssh [-p port] user@host <command>
# Secure copy, option '-r' means recursively copy entire directories:
scp [-r] user@host1:file1 user@host2:file2
```
**Note:** The default port of SSH protocal is 22.

## Generating an SSH key

> SSH keys are a way to identify trusted computers without involving passwords.

1. Generate SSH key:

        ssh-keygen
        
2. Send public key to remote host:

        ssh user@host 'mkdir -p .ssh && cat >> .ssh/authorized_keys' < ~/.ssh/id_rsa.pub


