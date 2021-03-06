# GPG

> GnuPG (GNU Privacy Guard) is a free software replacement for [PGP](https://en.wikipedia.org/wiki/Pretty_Good_Privacy), it includes keypair creation, exchanging and verifying keys, encrypting and decrypting documents, and authenticating documents with digital signatures.

## Installation

    brew install gpg

## Generating a GPG Key

    gpg --gen-key

You cloud identify each public by `<user-id>`. In keypair generating, instruction prompts ask your `your_name`, `your_email@example.com`, `key comment` and a `passphrase`. The `<user-id>` will finally look like `"your_name (key comment) <your_email@example.com>"`.

## Other common usages

```shell
# Display public keys or secret keys, from here you can obtain the key-id of your keys,
# feed with '--fingerprint', or use this option stand alone, obtain the fingerprint of your keys:
gpg --list-keys [--fingerprint]
gpg --list-secret-keys [--fingerprint]
gpg --fingerprint <user-id | key-id | fingerprint>
# Delete secret or public key (secret deletion must before its public key deletion):
gpg --delete-secret-key <user-id | key-id | fingerprint>
gpg --delete-key <user-id | key-id | fingerprint>
# Export public and secret key with ASCII:
gpg --armor [--output <public.key>] --export <user-id | key-id | fingerprint>
gpg --armor [--output <private.key>] --export-secret-keys <user-id | key-id | fingerprint> > 
# Import a public key file:
gpg --import <publick.key>
# Encrypt and Decrypt a file:
gpg --recipient <user-id | key-id | fingerprint> [--output file.gpg] --encrypt <file>
gpg [--output <file>] --decrypt <file.gpg>
# Sign a file in binary form in text form:
gpg [--output <file.gpg>] [--local-user <user-id | key-id | fingerprint>] --sign <file>
gpg [--output <file.asc>] [--local-user <user-id | key-id | fingerprint>] --clearsign <file>
# Create detached signature on a file:
gpg [--armor] [--output <file.sig>] [--local-user <user-id | key-id | fingerprint>] --detach-sign <file>
# Verify signature:
gpg --verify <file.gpg | file.asc>
gpg --verify <file.sig> <file>
```

*More docs on: <https://www.gnupg.org/gph/en/manual.html>*

### Distributing GPG keys and fetching

You cloud send your keys to a keyserver which closes to you. The major keyservers around the world synchronize themselves.

```shell
# Send keys to keyservers:
gpg [--keyserver <keyserver address>] -send-keys <keyid | fingerprint>
# Receive keys from keyservers:
gpg [--keyserver <keyserver address>] -recv-keys <keyid>
```

A list of a serval popular keyservers:

* keys.gnupg.net
* hkp://subkeys.pgp.net
* http://pgp.mit.edu
* hkp://pool.sks-keyservers.net
* hkp://zimmermann.mayfirst.org
* http://keyserver.ubuntu.com

## Using gpg-agent to manage your private keys

The `pinentry` bundled with `gpg-agent` will require your passphrase when the cache ttl times out. The `pinentry-mac` is a GUI version of `pinentry` and allows the user to store the passphrase in the Mac OS X keychain. It avoids you from frequently typing your passphrase.

1. Install the dependencies:

        brew install gpg-agent pinentry-mac

    You will get these instruction prompts:

    ```
    Remember to add "use-standard-socket" to your ~/.gnupg/gpg-agent.conf file.
    ```

    ```
    You can now set this as your pinentry program like
    ~/.gnupg/gpg-agent.conf
        pinentry-program /usr/local/bin/pinentry-mac
    ```

    ```
    .app bundles were installed.
    Run `brew linkapps pinentry-mac` to symlink these to /Applications.
    ```

2. Following these instructions, configure the GPG components:

        echo 'use-standard-socket' >> ~/.gnupg/gpg-agent.conf && echo 'pinentry-program /usr/local/bin/pinentry-mac' >> ~/.gnupg/gpg-agent.conf
        brew linkapps pinentry-mac

    Edit `~/.gnupg/gpg.conf` and uncomment `# use-agent` to tell gpg to use external agent

3. Check [Zsh plugins: gpg-agent](../iTerm2/zsh-plugins.html#gpg-agent) section and add this plugin:

    > Plugin `gpg-agent` enables gpg-agent startup automatically when you log in and export an env variable pointing GPG to the gpg-agent socket.

4. Configuration will work after `.oh-my-zsh` is loaded.

Every time pinentry-mac prompt out for passphrase, you could select the option `Save in Keychain`.

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

SSH has many powerful tunneling features, if you're interested in them, plz read [SSH: The Secure Shell: The Definitive Guide, Section 9.2 Port Forwarding](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch09_02.htm) published by O'Reilly.

## Generating an SSH key

> SSH keys are a way to identify trusted computers without involving passwords.

1. Generate SSH key, it is necessary to set a passphrase what you like:

        ssh-keygen
        
2. Send the public key to the remote host:

        ssh user@host 'mkdir -p .ssh && cat >> .ssh/authorized_keys' < ~/.ssh/id_rsa.pub

    You can also use other ways to pass your pubkey to the `.ssh/authorized_keys` file at remote.

## Using ssh-agent to manage your private keys

By default, OS X automatically starts `ssh-agent` when you login. You can check whether it does work by:

    ps -e | grep ssh-agent

If not, you'd run the agent and make it run automatically when you login:

    eval "$(ssh-agent -s)" && echo 'eval "$(ssh-agent -s)"' >> $ENVCONFIG/bootstrap.sh

Don't make multiple agents running.

1. Add your SSH key to the ssh-agent:

        ssh-add ~/.ssh/id_rsa

2. Check the loaded keys or test whether the passphrase-free works if you has passed by your pubkey to the remote host:

        ssh-add -l
        ssh -T user@host

