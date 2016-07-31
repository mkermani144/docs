Cryptography in networking
====


Types of Cryptography
----
* Symmetric
* Asymmetric


Asymmetric cryptography
----
In asymmetric, or public key cryptography, two keys are generated: A public key and a private key.

The client sends it's public key to the other side of the connection. Everyone can see the public key while it is getting sent to the other side. Afterwards, the other side gets the public key, encrypts it's message with that key and sends the encrypted message to our client. Finally, our client decrypts the message with it's private key.

The key point of this method is that private key cannot be made from public key, so knowing public key is not an advantage.


To-do
----
- [ ] Symmetric encryption
- [ ] Encryption methods
