# CRAM-MD5

CRAM-MD5 is a challenge–response authentication mechanism (CRAM) based on the [[HMAC]]-MD5 algorithm. As one of the mechanisms supported by the Simple Authentication and Security Layer (SASL), it is often used in email software as part of SMTP Authentication and for the authentication of POP and IMAP users, as well as in applications implementing LDAP, XMPP, BEEP, and other protocols.

### Protocol

The CRAM-MD5 protocol involves a single challenge and response cycle, and is initiated by the server:

- Challenge: The server sends a base64-encoded string to the client. Before encoding, it could be any random string, but the standard that currently defines CRAM-MD5 says that it is in the format of a Message-ID email header value (including angle brackets) and includes an arbitrary string of random digits, a timestamp, and the server's fully qualified domain name.
- Response: The client responds with a string created as follows.
- The challenge is base64-decoded.
- The decoded challenge is hashed using HMAC-MD5, with a shared secret (typically, the user's password, or a hash thereof) as the secret key.
- The hashed challenge is converted to a string of lowercase hex digits.
- The username and a space character are prepended to the hex digits.
- The concatenation is then base64-encoded and sent to the server
- Comparison: The server uses the same method to compute the expected response. If the given response and the expected response match, then authentication was successful.