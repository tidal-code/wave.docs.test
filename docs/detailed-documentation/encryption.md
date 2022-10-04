---
layout: default
title: Password Encryption
parent: Detailed Docs
nav_order: 1000
---

# Password Encryption and Decryption

The framework support Jasypt password decryption. It is always safer to keep your
passwords encrypted even if your project is private. 

You can find more information about Jasypt [here](http://www.jasypt.org){:target='_blank'}

To encrypt or decrypt your passwords or secret values, refer 
[this](https://www.devglan.com/online-tools/jasypt-online-encryption-decryption){:target='_blank'}

To make Sqsite aware of the password encryption; wrap your hashed(encrypted) string with ENC().
 Otherwise the framework will treat it like a normal string. For example if your hashed string is `XKdtKa1jZ6YcJ5exkrBaBu3/ysUtAkvW`, 
 you should wrap it like `ENC(XKdtKa1jZ6YcJ5exkrBaBu3/ysUtAkvW)`.
You should supply the secret value as an environment property. 

To supply the value as an environment property you need to supply a key to recognise the value.
For that create a file named \'configuration.properties\' under your test resources folder and add the below value: <br>
`secretKeyName=your-secret-key-name`

For example if you have stored your secret value in your environment variables as my_project_secret_key=mySecretKey, 
then you should supply the secret key name \'my_project_secret_key\' as
`secretKeyName='my_project_secret_key'`

The framework will look for an environment variable or property with the name \'my_project_secret_key\' and that value will
be used to decrypt your password.

## An alternate method (Jasypt Plugin)

You can encrypt and decrypt passwords using Jasypt Plugin as described in this [article](https://medium.com/geekculture/encrypt-passwords-and-keys-in-a-spring-boot-project-using-jasypt-6b4406891c09){:target='_blank'}








