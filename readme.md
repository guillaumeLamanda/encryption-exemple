# Public / Private key demo

This repository is a demontration of messages encryption/decyption based on public/private keys.

## Prerequired

- Have `openssl` installed.

## Generate keys

### Alice

```sh
mkdir alice && cd alice
# generate private key
openssl genrsa -out key.pem 2048
# extract public key
openssl rsa -in key.pem -outform PEM -pubout -out public.pem
```

### Bob

```sh
mkdir bob && cd bob
# generate private key
openssl genrsa -out key.pem 2048
# extract public key
openssl rsa -in key.pem -outform PEM -pubout -out public.pem
```

## Create message
 
```sh
echo 'Hello bob !' > alice/message-to-bob.txt
```

## encrypt message

```sh
openssl rsautl -encrypt -pubin -inkey bob/public.pem  -in alice/message-from-alice-to-bob.txt  -out message.txt.enc 
```

Look at the message

```sh
cat message.txt.enc
``` 

## decrypt message

```sh
openssl rsautl -decrypt -inkey bob/key.pem  -in message.txt.enc  -out message.txt i
```

## Generate keys 
