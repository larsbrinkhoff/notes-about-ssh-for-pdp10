A small set of primitives needed for SSH, as advised by Niels Möller.

- For key exchange: diffie-hellman-group14-sha256 and/or
  curve25519-sha256.

- For public key authentication: rsa-sha2-256 and/or ssh-ed25519.

- For session encryption: aes128-ctr.

- For session authentication: hmac-sha2-256.

Consider chacha20-poly1305@openssh.com instead of aes and hmac.

Maybe it would be simplest to just support the most modern primitives:
curve25519-sha256, ssh-ed25519, chacha20-poly1305@openssh.com.
ssh-ed25519 requires 64-bit computations, so it may be simpler to
stick to rsa; then sha256 is the only hash function you need.

dropbear and tinyssh are small implementations.

- https://matt.ucc.asn.au/dropbear/dropbear.html "Dropbear can compile
  to a 110kB statically linked binary with uClibc on x86 (only minimal
  options selected)"

- https://tinyssh.org/ "TinySSH has less than 100000 words of code",
  "all memory statically allocated (less than 1MB)"
