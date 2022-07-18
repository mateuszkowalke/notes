# Message Authenticity Code

Not to be confused with [[MAC address]], sometimes known as a tag, is a short piece of information used for authenticating a message. In other words, to confirm that the message came from the stated sender (its authenticity) and has not been changed. The MAC value protects a message's data integrity, as well as its authenticity, by allowing verifiers (who also possess the secret key) to detect any changes to the message content.

### Informally MAC system consists of three algorithms:

- A **key generation algorithm** selects a key from the key space uniformly at random.
- A **signing algorithm** efficiently returns a tag given the key and the message.
- A **verifying algorithm** efficiently verifies the authenticity of the message given the key and the tag. That is, return accepted when the message and tag are not tampered with or forged, and otherwise return rejected.

![[MACimg.png]]