# SSH

## Keygen
-t and -b are the parameters that go with the ssh-keygen utility.
-t rsa, -b 4096

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

 
```-t``` (type) - Specifies the algorithm to be used for generating the keys. Algorithms available are -  rsa , dsa , ecdsa

	rsa - Rivest–Shamir–Adleman
	dsa - Digital Signature Algorithm. A key size of 1024 would normally be used with it.
	ecdsa - Elliptic Curve Digital Signature Algorithm - three key sizes are supported: 256, 384, and 521 bits.

```-b``` (bits) - Specifies the no. of bits for the key size. These were 1024, 2048 earlier.

```-C``` (Comment)

https://man.openbsd.org/ssh-keygen.1

2048 * 2 = 4096 is considered strong. Hence the recommended key size.

2048 bits is considered to be sufficient for RSA keys. This is the default key size if you don't mention the -b flag.


## Permissions for SSH files / directories

.ssh directory: 700 (drwx------)
public key (.pub file): 644 (-rw-r--r--)
private key (id_rsa): 600 (-rw-------)
Home directory should not be writeable by the group or others (at most 755 (drwxr-xr-x)).

Note: home directory is not writeable by other users
chmod g-w,o-w ~