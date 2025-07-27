# AWS EC2 Instance Creation and Connection

## Create an AWS EC2 Instance

```
Amazon Linux
Instance type: t2.micro
Key pair type: RSA (.pem)
```

-   Prepare the .pem key file
    Format: RSA (.pem)

## Set Permissions for .pem Key

```
chmod 400 ~/Desktop/pem/chatbot-key.pem
```

## Connect to EC2 via Terminal

-   Connect using your EC2 public IPv4 address:

```
ssh -i ~/Desktop/pem/chatbot-key.pem ec2-user@"ipv4 address"
```

-   On first connection, you’ll see:

```
The authenticity of host 'your IP' can't be established.
ED25519 key fingerprint is ~~~~~~~~
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'your IP' (ED25519) to the list of known hosts.
   ,     #_
   ~\_  ####_        Amazon Linux 2023
  ~~  \_#####\
  ~~     \###|
  ~~       \#/ ___   https://aws.amazon.com/linux/amazon-linux-2023
   ~~       V~' '->
    ~~~         /
      ~~._.   _/
         _/ _/
       _/m/'
```

## Set Up SSH Config File

```
vi ~/.ssh/config
```

-   Inside vi, press i to enter insert mode, then paste:

```
Host chatbot
    HostName <your-ec2-IPv4 DNS>
    User ec2-user
    IdentityFile ~/Desktop/pem/chatbot-key.pem
```

-   After pasting:
    Press ESC, then type :wq and press Enter to save and exit.

## Connect Easily with Config

```
ssh chatbot
```
