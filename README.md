# SIDH for Open SSL

This release contains a patch for OpenSSL 1.0.2g to support the Supersingular Isogeny-based Diffie-Hellman (SIDH) key exchange<sub>1</sub>, using the implementation of Microsoft Research<sub>2</sub>. This scheme provides approximately 128 bits of quantum security and 192 bits of classical security.

### Details
The library specifies four ciphersuites:
* SIDH-ECDSA-AES128-GCM-SHA256 
* SIDH-RSA-AES128-GCM-SHA256 
* SIDH-ECDHE-ECDSA-AES128-GCM-SHA256 
* SIDH-ECDHE-RSA-AES128-GCM-SHA256 

The first two consist of a SIDH key exchange, as described in [1], authentication based on ECDSA or RSA digital signatures, authenticated encryption (with associated data) (AEAD) based on AES-128 in GCM (Galois Counter Mode); key derivation and hashing based on SHA-256. The last two offer hybrid ciphersuites that are as above, except the key exchange includes both SIDH and ECDH key exchange; the pre-master secret is the concatenation of the ECDH shared secret and the SIDH shared secret. All these ciphersuites require TLSv1.2 because of the use of AES-GCM.

### References
1. Craig Costello, Patrick Longa, and Michael Naehrig (Microsoft Research). "Efficient algorithms for supersingular isogeny Diffe-Hellman." https://eprint.iacr.org/2016/413.pdf. 
2. http://research.microsoft.com/en-us/projects/sidh/ 
3. https://openssl.org/source/old/1.0.2/openssl-1.0.2g.tar.gz
