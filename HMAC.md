# HMAC

keyed-hash message authentication code || hash-based message authentication code

It's a kind of [[MAC]], which means it can be used both for checking integrity of the message and it's authenticity. It can use any kind of hashing algorithm underneatch (MD-5, SHA-256). HMAC uses two passes of hash computation. The secret key is first used to derive two keys – inner and outer. The first pass of the algorithm produces an internal hash derived from the message and the inner key. The second pass produces the final HMAC code derived from the inner hash result and the outer key. Thus the algorithm provides better immunity against length extension attacks.

### Definition from RFC 2104:

$HMAC(K,m) = H((K'{\oplus}opad)||H((K'{\oplus}ipad)||m))$
// todo
// https://en.wikipedia.org/wiki/HMAC
$K' =$
where

H is a cryptographic hash function
m is the message to be authenticated
K is the secret key
K' is a block-sized key derived from the secret key, K; either by padding to the right with 0s up to the block size, or by hashing down to less than or equal to the block size first and then padding to the right with zeros
‖ denotes concatenation
⊕ denotes bitwise exclusive or (XOR)
opad is the block-sized outer padding, consisting of repeated bytes valued 0x5c
ipad is the block-sized inner padding, consisting of repeated bytes valued 0x36