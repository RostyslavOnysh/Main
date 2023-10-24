
Paste the text below, substituting in your GitHub email address.
```bash

$ ssh-keygen -t ed25519 -C "your_email@example.com"
```
Note: If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
This creates a new SSH key, using the provided email as a label

> Generating public/private ALGORITHM key pair.
When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ssh_keyname with your custom key name.

> Enter a file in which to save the key (/home/YOU/.ssh/ALGORITHM):[Press enter]
At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases."

> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key.
Start the ssh-agent in the background.
```bash
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```
Depending on your environment, you may need to use a different command. For example, you may need to use root access by running sudo -s -H before starting the ssh-agent, or you may need to use exec ssh-agent bash or exec ssh-agent zsh to run the ssh-agent.

Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
```bash
$ ssh-add ~/.ssh/id_ed25519
```
Add the SSH key to your account on GitHub. For more information, see "Adding a new SSH key to your GitHub account."

Generating a new SSH key for a hardware security key
If you are using macOS or Linux, you may need to update your SSH client or install a new SSH client prior to generating a new SSH key. For more information, see "Error: Unknown key type."

Insert your hardware security key into your computer.

Open Terminal.

Paste the text below, substituting in the email address for your account on GitHub.
```bash
$ ssh-keygen -t ed25519-sk -C "YOUR_EMAIL"
```
Note: If the command fails and you receive the error invalid format or feature not supported, you may be using a hardware security key that does not support the Ed25519 algorithm. Enter the following command instead.
```
$ ssh-keygen -t ecdsa-sk -C "your_email@example.com"
```
When you are prompted, touch the button on your hardware security key.

When you are prompted to "Enter a file in which to save the key," press Enter to accept the default file location.

> Enter a file in which to save the key (/home/YOU/.ssh/id_ed25519_sk):[Press enter]
When you are prompted to type a passphrase, press Enter.

> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
