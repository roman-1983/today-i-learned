# What is a SSH Key fingerprint?

Today a customer asked to send him a ssh fingerprint. I realized that i did not know, what a ssh-fingerprint ist - until today.

Generally its for easy identification & verification of the host i try to connect to.

If the fingerprint changes, the target machine has changed their public key. This may not be a bad thing (happens from re-installing ssh), but it could also indicate that it is a different machine at the same domain/IP (happens when  connecting through something like load balancer).
Also that you are being targeted with a man-in-the-middle attack, where the attacker is somehow intercepting/rerouting your ssh connection to connect to a different host which could be snooping your user/pw.

## How to generate a fingerprint?

It's quiet easy to create a fingerprint for an existing ssh-key. Just execute the following command:

    ssh-keygen -l -f id_rsa.pub

This will create a fingerprint for the given key.

    4096 SHA256:aJrZoYLHcJ1RCHNz/sRGnmkvP2LNDbLGoIZ7RxbIGGo

If i need the old-fashioned **MD5 fingerprint**, i have to add the `-E` parameter

    ssh-keygen -l -E md5 -f id_rsa.pub

This will print the following output:

    4096 MD5:6f:75:d1:74:75:35:64:7f:ec:89:4b:94:45:29:ff:2b
