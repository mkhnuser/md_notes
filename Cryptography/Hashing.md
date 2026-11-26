# Hashing

## Objectives

Hashing allows one to achieve data integrity through a one-way transformation.
In this way, you create a fingerprint of your data.

## Hash Functions

Hash functions map an almost infinite domain into a fixed range of values.

All hash functions have to satisfy the following:

* Consistency:

      Given a fixed input, a hash function always produces the same output.

* Compression:

      Given a large input, a small output should be produced.

* Lossiness:

      Given a fixed input,
      a hash function output should contain no information about the input.

See "Practical Cryptography in Python", Chapter 2, Hashing.

## Cryptographic Hash Functions

All cryptographic hash functions have to satisfy the following:

* Preimage resistance:

      Given a cryptographic hash function output,
      it should be extremely hard to obtain an input which was used.
      An input can obviously be any binary sequence of data: files, images, numbers, etc.

* Second-preimage resistance.

      Given a cryptographic hash function output, and even if one preimage becomes known,
      it should be still extremely hard to find another preimage.

* Collision resistance.

      A good cryptographic hash function follows an avalanche property:
      ideally, for a small input change, at least 50% of output bits have to changed.

See "Practical Cryptography in Python", Chapter 2, Hashing.

## MD5

MD stands for a message digest, which is the same as a message hash.
MD5 algorithm produces an integer which occupies 16 bytes or 128 bits of RAM.
Common uses of MD5 are file checksums to ensure their integrity: `md5sum`.

See "Practical Cryptography in Python", Chapter 2, Hashing.

## SHA1

SHA1 algorithm produces an integer which occupies 20 bytes or 160 bits of RAM.

See "Practical Cryptography in Python", Chapter 2, Hashing.

## SHA256

SHA256 algorithm produces an integer which occupies 32 bytes or 256 bits of RAM.
SHA256 is the recommended default for hashing, though sometimes a KDF has to be used.

See "Practical Cryptography in Python", Chapter 2, Hashing.

## Salt

Salt is an random sequence which is added to a password before hashing.
Salt prevents a reverse table lookup attack.

One should create salt on a per-user basis
so that when two users have the same passwords, the hashes are different.

So, one might store the following record in a database:

      u, s, H(p + s)

Where `u` is a user id, `p` is a password and `s` is a per-user salt value.

An example password hashing flow:

1. Obtain user id.
2. Just right before hashing, generate salt.
3. Hash the password with salt.
4. Store user id, salt, hashed password.

Once again: consider the usage of a KDF for passwords.
Observe: some high-level libraries generate salt for you automatically.

See "Practical Cryptography in Python", Chapter 2, Hashing.

## Key Derivation Functions

Key derivation functions require a compute power to generate passwords.
The purpose of a KDF is to prevent GPU/ASIC accelerated attacks.
Essentially, the derived key you obtain means the same as a hash.

Examples of key derivation functions are: PBKDF2, scrypt, bcrypt, argon2id.

Note: be sure to save compute parameters and salt along with the derived key.
Usually, a derived key will contain all the necessary information.
