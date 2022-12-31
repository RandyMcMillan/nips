NIP-0X
======

Simple Deterministic Aliases
--------------------------------------

`draft` `optional` `author:@RandyMcMillan`

### Generating new profiles deterministically from an existing secure privkey or entropy using sha256

There are many reasons nostr users may need to generate a new or temporary profile. Scenarios include many privacy issues or simply the users wants multiple profiles that are derived from the user's _master private key_. Simular to a *bip-0085 HD child wallet* in Bitcoin, the use cases for _determinsitc aliases_ are too numerous to list here.

The **Simple Deterministic Alias** generation scheme described here focuses on simplicity, and the user can accomplish this with a command line utility independently of any client implementation. The emphasis on simplicity is for user autonomy - reducing dependency on any specific implementation or exotic cryptographic method. For our example we use the `openssl dgst -sha256` command which is widely available.

##### For demonstration purposes we will use easily reproducable values.

Starting with a secure source of entropy or key generation method:

### null_privkey:

`null_privkey`=`$(echo -en "" | openssl dgst -sha256)`

```shell
$ null_privkey=$(echo -en "" | openssl dgst -sha256) && echo $null_privkey
e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
```

### Test seed phrases - abandon art

#### Root: 24 words
abandon abandon abandon abandon abandon abandon abandon abandon abandon abandon abandon abandon
abandon abandon abandon abandon abandon abandon abandon abandon abandon abandon abandon art


#### BIP39 seed:
408b285c123836004f4b8842c89324c1f01382450c0d439af345ba7fc49acf705489c6fc77dbd4e3dc1dd8cc6bc9f043db8ada1e243c4a0eafb290d399480840

```shell
$ abandon_art_privkey=$(echo -en "408b285c123836004f4b8842c89324c1f01382450c0d439af345ba7fc49acf705489c6fc77dbd4e3dc1dd8cc6bc9f043db8ada1e243c4a0eafb290d399480840" | openssl dgst -sha256) && echo $abandon_art_privkey
273be55792f7ca3f3bcb445ff07f39f64dd6a324ce6d8eb025951267f61b4d33
```
Using the shasum -a 256 command 
shasum -a 256:
273be55792f7ca3f3bcb445ff07f39f64dd6a324ce6d8eb025951267f61b4d33

===

NOSTR PRIVATE KEY:
nsec1yua724uj7l9r7w7tg30lqlee7exadgeyeekcavp9j5fx0asmf5esvagd2d

NOSTR PUBLIC KEY:
npub175fjerv9f2dcwgg2s9y4vrhxwgjnhymgh34q33x6un3glcd9wxhshxkl0r

===

