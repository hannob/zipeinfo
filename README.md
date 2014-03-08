zipeinfo - ZIP encryption info
==============================

parses ZIP files and tells user about used encryption method

created by [Hanno Boeck](http://hboeck.de)
License: CC0 / Public Domain

Background
==========

The ZIP file format supports various methods to encrypt files. The original
ZIP encryption has been broken by an attack by Biham/Kocher in 1994.

Two competing formats introduced "strong" encryption into ZIP files. WinZip
introduced an AES-based encryption and PKWARE, creator of the original PKZIP,
created an extension supporting various encryption algorithms, some of them
completely broken (DES, RC2), others still good today (AES and others).


zipeinfo
========

I became curious in ZIP encryption formats and found no tool that will
easily tell me which encryption was used.

So I hacked together this python script. It may break on malformed files,
only checks the header parts that are relevant for encryption and ignores
the rest.

Feedback (and patches) welcome. Especially if there are any other ZIP
encryption formats out there I'd like to hear about them.


Algorithm classification
========================

zipeinfo puts all encryption algorithms in three rough categories.

insecure: Attacks known, can be broken on a normal home PC.
Algorithms: PKZIP/Original, DES, RC2

weak: No known practical attacks, but considered weak.
Algorithms: RC4, 3DES with 112 bit

ok: Probably not breakable by anyone.
Algorithms: AES (all sizes), Blowfish, Twofish, 3DES with 168 bit

More Info
=========

* [PkCrack - attack on legacy ZIP encryption](https://www.unix-ag.uni-kl.de/~conrad/krypto/pkcrack.html)
* [A Known Plaintext Attack on the PKZIP Stream Cipher (1994, Eli Biham, Paul C. Kocher)](ftp://utopia.hacktic.nl/pub/crypto/cracking/pkzip.ps.gz)
* [.ZIP File Format Specification](https://www.pkware.com/documents/casestudies/APPNOTE.TXT)
* [WinZip AES Encryption Information: Encryption Specification AE-1 and AE-2](http://www.winzip.com/aes_info.htm)
