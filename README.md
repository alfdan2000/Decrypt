# Decrypt

University coursework: reads an RSA private key from a PEM file and decrypts a
message produced by the companion [Encrypt](https://github.com/alfdan2000/Encrypt)
project.

## Keys are not committed

`Decrypt.java` expects `alfredCazaresClientEncryptPrivate.pem` in the working
directory. That file is **not** in this repository, and should not be.

A real RSA private key was originally committed here. It was 1024-bit, generated
in 2017 for this assignment, and protected nothing else — but a private key does
not belong in a public repository regardless of what it guards, so it has been
removed. It remains in this repository's git history, where it is inert.

To run this, generate your own keypair. `PemUtils` already provides
`writePrivateKey` and `writePublicKey` for exactly that, or use OpenSSL:

```bash
openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 \
  -out alfredCazaresClientEncryptPrivate.pem
openssl rsa -in alfredCazaresClientEncryptPrivate.pem -pubout \
  -out alfredCazaresClientEncryptPublic.pem
```

Use 2048-bit or better. 1024-bit RSA is no longer considered safe.

`encryptedMessage.txt` was encrypted with the original key, so it will not
decrypt under a newly generated one. Re-encrypt it with `Encrypt` using your own
public key.
