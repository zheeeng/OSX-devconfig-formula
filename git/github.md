# Github

> Verifying your primary email address ensures strengthened security and allows GitHub staff to better assist you if you forget your password.

Goto `Emails` panel in profile settings, check your emails or add && verify your email addresses.

## Adding GPG key to Github account

To enable you sign commits and tags with GPG, you'd add your GPG public key into your account settings. Before it, make sure you've verified your email address. If there are not any existing GPG keys, follow the instruction in [Credentials/GPG](../Credentials/README.html#GPG) section. You'd ensure the email address for this GPG keypair is the verified email address at GitHub. After your GPG keys get ready, copy the contents of your GPG public key to your clipboard:

    gpg --armor --export <key-id> | pbcopy

Then, login Github and goto `SSH and GPG Keys` panel in profile settings. Paste && submit your public GPG key to Github, save the configuration.

## Adding SSH key to GitHub account

To enable you access your GitHub repository without passphrase, you'd add your SSH public key into your account settings.

First, make sure your SSH pub/secret keys are generated, just run `ls ~/.ssh`. If there are not any existing SSH keys, follow the instruction in [Credentials/SSH](../Credentials/README.html#SSH) section. After your SSH keys get ready, copy the contents of the id_rsa.pub file to your clipboard:

    pbcopy < ~/.ssh/id_rsa.pub

Then, login Github and goto `SSH and GPG Keys` panel in profile settings. Paste && submit your public SSH key to Github, save the configuration and test it:

    ssh -T git@github.com

You will meet the SSH key's fingerprint confirmation when you access through SSH at first time. The published officail fingerprint are:

    # GitHub's public key fingerprints (in hexadecimal format):
    16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48 (RSA)
    ad:1c:08:a4:40:e3:6f:9c:f5:66:26:5d:4b:33:5d:8c (DSA)
       
    # SHA256 hashes shown in OpenSSH 6.8 and newer (in base64 format):
    nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8 (RSA)
    br9IjFspm1vxR3iA35FWE+4VTyz1hYVLIE2t1/CeyWQ (DSA)

After this, we expect a bonjour message is printed out at every time you access GitHub by SSH.

**Note:** If you're switching from HTTPS to SSH, you'll need to update your remote repository URLs.


