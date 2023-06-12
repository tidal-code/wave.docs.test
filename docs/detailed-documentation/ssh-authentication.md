---
layout: default
title: SSH Authentication
parent: Detailed Docs
nav_order: 16
---

# SSH Authentication

SSH authentication is the process of verifying the identity of a user or a system before granting access to a remote system using the Secure Shell (SSH) protocol. SSH is a cryptographic network protocol that allows secure remote access and control of remote systems over an unsecured network.

### Public key authentication: 
This method uses asymmetric key cryptography. The user generates a pair of cryptographic keys—a private key and a public key. The private key is kept securely on the user's local system, while the public key is copied to the remote server. During authentication, the client proves its identity by signing a challenge from the server using the private key. If the server can verify the signature using the associated public key, authentication is successful. Public key authentication is considered more secure and convenient than password authentication, especially when combined with strong passphrases.

### SSH Key generation in Windows
To generate an SSH key in Windows, you can use the OpenSSH client, which is built into Windows 10 and later versions. Here's a step-by-step guide:

In the command prompt or PowerShell window, type the following command to generate an SSH key pair:

```css
ssh-keygen
```

You will be prompted to specify the file name for the key pair. Press Enter to accept the default location and filename (usually C:\Users\YourUsername\.ssh\id_rsa).

Next, you'll be prompted to enter a passphrase. While it's optional, using a passphrase adds an extra layer of security to your SSH key. If you choose to set a passphrase, enter it and press Enter. If you prefer not to use a passphrase, simply press Enter without typing anything.

The key pair will be generated, consisting of a private key and a corresponding public key. By default, the private key is saved in C:\Users\YourUsername\.ssh\id_rsa and the public key in C:\Users\YourUsername\.ssh\id_rsa.pub.
That's it! You've successfully generated an SSH key pair on Windows. The private key should be kept secure and not shared with anyone, while the public key can be provided to remote servers or services that you wish to authenticate with using SSH public key authentication.


### Add your SSH private key to Azure DevOps

To add your SSH key to Azure DevOps, you need to perform the following steps:

1. Generate an SSH key pair: If you haven't already generated an SSH key pair, you can follow the instructions in the previous section to generate one.

2. Copy the public key: Open the file containing the public key (id_rsa.pub by default) using a text editor, and copy its entire contents.

3. Sign in to Azure DevOps: Go to the Azure DevOps website (dev.azure.com/ORG_NAME) and sign in to your account.

4. Access your user settings: Once you are signed in, click on the setting icon in the top-right corner of the Azure DevOps interface and select "SSH public keys" from the dropdown menu.

5. In the next page, click on "+ New Key".

6. Add your SSH public key: In the "Add New SSH Key" dialog, give your key a title (e.g., "windows_pc") and paste the public key you copied earlier into the "Public Key Data" field. Make sure that you are not pasting any extra white spaces. Otherwise the key verification will fail.

7. Save the SSH public key: Click on the "Add" button to save your SSH public key.

Once you have added your SSH public key to Azure DevOps, you can use it to authenticate with Azure DevOps repositories and services that support SSH authentication. Make sure that the corresponding private key (id_rsa by default) is stored securely on your local machine.

You can now clone or interact with Azure DevOps repositories using SSH URLs and authenticate seamlessly using your SSH key.