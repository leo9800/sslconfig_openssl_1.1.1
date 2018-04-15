# Deprecated:
This can only work with OpenSSL 1.1.1-dev(TLS 1.3 draft 18 or 19).

The same feature can be implemented by the configuration command `Options:+PrioritizeChacha` on later version. (from 1.1.1-pre1 on)

This feature can be backported to OpenSSL 1.1.0 by applying [https://github.com/Hardrain980/openssl-1.1.0-patch](https://github.com/Hardrain980/openssl-1.1.0-patch)

------

# CHACHA20-POLY1305 preference patch for OpenSSL 1.1.1-dev

#### The original version of patch is from CloudFlare, at [https://github.com/cloudflare/sslconfig](https://github.com/cloudflare/sslconfig)

With this patch, OpenSSL 1.1.1-dev can now prefer to use CHACHA20-POLY1305 ciphers(including `TLS13-CHACHA20-POLY1305` for TLS 1.3) on devices without AES instruction sets.

How to use:

1. use `git clone` or any downloading tool to have `s3_lib.c` cloned to your system
2. backup and delete `{$OPENSSL_1.1.1_PATH}/ssl/s3_lic.c`
3. copy `s3_lib.c` in this repository to `{$OPENSSL_1.1.1_PATH}/ssl/`
4. compile and install
5. \*.recompile your application depends on OpenSSL if it's linked to OpenSSL statically(_NOT_ shared)
