# Cryptography
- Process to share information in a secret manner to protect its privacy or confidentiality.
- Authentication: Claims made by or about the subject are true. The user is who they claim to be.
- Integrity: Information that has not been tampered with in anyway between transfers.
- Non-repudiation: Prevent any dispute or challenge the validity.

## Hashing
- One way function
- The same plain text input run through a hash algo will always output the same cipher text.

# Symmetric-Key
- Sender and receiver share the same key.
- Examples: DES, AES, RC4, Blowfish

# Asymmetric Public-Key
- Two keys for each peer.
- Public Key is freely distributed, and corresponding private key that is kept secret.
- Public key is used for encryption, and private/secret key is used for decryption.

### Block Cipher: Handles bytes in blocks.
- Electronic Code Book(Deprecated): Message is divided into blocks and each block is encrypted separately.
- Cipher Block Chaining

### Stream Cipher: Data is handled one byte at a time.
- Each cipertext block is derived from the previous block, and the initialization vector is used for the first block.

### Public Key Infrastructure
- PKI is a set of hardware, software, people, policies, and procedures needed to create, manage, store, distribute, and revoke digital certs.
- PKI relies upon elements to make sure identity is certified and verified by a certificate authority(CA)
- Each id is unique for each CA
- x.509 is the standard for public key certs.

### Public Key certificate
- Binds public key with an id using a digital signature.
- Id info includes name of a person or org, etc..
- Cert is used to verify that a public key belongs to that individual
- CA signature assures the identity, and the CA acts as a trusted 3rd party
- Signatures on the certificate are attestations by the cert signer that the id info and the public key are bound together.
- Authenticity is verified by the validity of the certificate.
- confidentiality is achieved by a handshake between initial channel parameters encrypted with the SSL cert public key of the website.


### Secure Socket Layer - SSL
- Protocol used to communicate over the internet in a secure manner.
- Makes use of PKI and sym encryption for communication.
- Ensures no third party can tamper with the communication.

### Digital Signature
- Mechanism that authenticates a message. Proves message is sent from a sender.
