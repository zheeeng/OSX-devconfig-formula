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

## Using gpg-agent to manage your private keys

*Reference: <https://gist.github.com/bmhatfield/cc21ec0a3a2df963bffa3c1f884b676b>*

> In order for gpg to find gpg-agent, gpg-agent must be running, and there must be an env variable pointing GPG to the gpg-agent socket.

1. `gpg-agent-startup.sh` does this work above. It is sourced in the processing of `envconfig`, see the [envconfig/gpg-agent-startup.sh](../envconfig.sh/gpg-agent-startup.sh.html) section.

    Details in <https://gist.github.com/bmhatfield/cc21ec0a3a2df963bffa3c1f884b676b#file-profile>.

2. Install the dependencies:

        brew install gpg-agent pinentry-mac

3. Configure the GPG components:

    * In `~/.gnupg/gpg.conf`, uncomment `# use-agent` and add `batch` for preventing the successful interactive messages. 

        Details in <https://gist.github.com/bmhatfield/cc21ec0a3a2df963bffa3c1f884b676b#file-gpg-conf>.

    * In `~/.gnupg/gpg-agent.conf`, add `use-standard-socket
` and `pinentry-program /usr/local/bin/pinentry-mac`.

        Details in <https://gist.github.com/bmhatfield/cc21ec0a3a2df963bffa3c1f884b676b#file-gpg-agent-conf>.

4. Restart your terminal for sourcing the `gpg-agent-startup.sh`.

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

SSH has many powerful tunneling features, if you're interested at them, plz read [SSH: The Secure Shell: The Definitive Guide, Section 9.2 Port Forwarding](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch09_02.htm) published by O'Reilly.

## Generating an SSH key

> SSH keys are a way to identify trusted computers without involving passwords.

1. Generate SSH key, it is necessary to set a passphrase what you like:

        ssh-keygen
        
2. Send public key to the remote host:

        ssh user@host 'mkdir -p .ssh && cat >> .ssh/authorized_keys' < ~/.ssh/id_rsa.pub

    You can also use other ways to pass your pubkey to the `.ssh/authorized_keys` file at remote.

## Using ssh-agent to manage your private keys

By default, OS X automatically start `ssh-agent` when you login. You can check whether it does work by:

    ps -e | grep ssh-agent

If not, you'd run the agent and make it run automatically when logining:

    eval "$(ssh-agent -s)" && echo 'eval "$(ssh-agent -s)"' >> $ENVCONFIG/bootstrap.sh

Don't make multiple agents running.

1. Add your SSH key to the ssh-agent:

        ssh-add ~/.ssh/id_rsa

2. Check the loaded keys or test whether the passphrase-free works if you has passed by your pubkey to the remote host:

        ssh-add -l
        ssh -T user@host

