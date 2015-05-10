# 帮助文档：如何用 gpg 签名

## 准备

1. 安装 gnupg 软件包（``sudo apt-get install gnupg``）
2. 用 ``gpg --gen-key`` 命令生成公私钥，存储在 ``~/.gnupg`` 目录里
3. 用 ``gpg --list-keys`` 命令列出刚生成的公私钥

    $ gpg --gen-key
    gpg: WARNING: unsafe permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg (GnuPG) 1.4.18; Copyright (C) 2014 Free Software Foundation, Inc.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.
    
    gpg: WARNING: using insecure memory!
    gpg: please see http://www.gnupg.org/documentation/faqs.html for more information
    Please select what kind of key you want:
       (1) RSA and RSA (default)
       (2) DSA and Elgamal
       (3) DSA (sign only)
       (4) RSA (sign only)
    Your selection? 1
    RSA keys may be between 1024 and 4096 bits long.
    What keysize do you want? (2048)
    Requested keysize is 2048 bits
    Please specify how long the key should be valid.
             0 = key does not expire
          <n>  = key expires in n days
          <n>w = key expires in n weeks
          <n>m = key expires in n months
          <n>y = key expires in n years
    Key is valid for? (0) 10y
    Key expires at Mon, Dec  2, 2024 10:23:28 PM CST
    Is this correct? (y/N)
    
    You need a user ID to identify your key; the software constructs the user ID
    from the Real Name, Comment and Email Address in this form:
        "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"
    
    Real name: Bojie Li
    Email address: bojieli@gmail.com
    Comment: USTC
    You selected this USER-ID:
        "Bojie Li (USTC) <bojieli@gmail.com>"
    
    Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? O
    You need a Passphrase to protect your secret key.
    
    We need to generate a lot of random bytes. It is a good idea to perform
    some other action (type on the keyboard, move the mouse, utilize the
    disks) during the prime generation; this gives the random number
    generator a better chance to gain enough entropy.
    .+++++
    ....+++++
    We need to generate a lot of random bytes. It is a good idea to perform
    some other action (type on the keyboard, move the mouse, utilize the
    disks) during the prime generation; this gives the random number
    generator a better chance to gain enough entropy.
    +++++
    +++++
    gpg: /home/Bojie/.gnupg/trustdb.gpg: trustdb created
    gpg: key 5BABFFEE marked as ultimately trusted
    public and secret key created and signed.
    
    gpg: checking the trustdb
    gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
    gpg: depth: 0  valid:   1  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 1u
    gpg: next trustdb check due at 2024-12-02
    pub   2048R/5BABFFEE 2014-12-05 [expires: 2024-12-02]
          Key fingerprint = B968 8A92 04CC FA83 04A3  1D60 7C1F 3FE5 5BAB FFEE
    uid                  Bojie Li (USTC) <bojieli@gmail.com>
    sub   2048R/2F08C87A 2014-12-05 [expires: 2024-12-02]


    $ gpg --list-keys
    gpg: WARNING: unsafe permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: using insecure memory!
    gpg: please see http://www.gnupg.org/documentation/faqs.html for more information
    /home/Bojie/.gnupg/pubring.gpg
    ------------------------------
    pub   2048R/5BABFFEE 2014-12-05 [expires: 2024-12-02]
    uid                  Bojie Li (USTC) <bojieli@gmail.com>
    sub   2048R/2F08C87A 2014-12-05 [expires: 2024-12-02]


    $ ls ~/.gnupg/
    gpg.conf  pubring.gpg  pubring.gpg~  random_seed  secring.gpg  trustdb.gpg


    jie)-(boj-laptop)-(22:35:01)-(~/ra)-(git:master)
    (! 3534)-> gpg --output ra.sig --sign ra.md
    gpg: WARNING: unsafe permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: using insecure memory!
    gpg: please see http://www.gnupg.org/documentation/faqs.html for more information

    You need a passphrase to unlock the secret key for
    user: "Bojie Li (USTC) <bojieli@gmail.com>"
    2048-bit RSA key, ID 5BABFFEE, created 2014-12-05


## 对文件进行签名

1. gpg --output doc --decrypt ra.sig


    (Bojie)-(boj-laptop)-(22:36:28)-(~/ra)-(git:master)-($?:130)
    (! 3536)-> gpg --output doc --decrypt
    gpg: WARNING: unsafe permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: using insecure memory!
    gpg: please see http://www.gnupg.org/documentation/faqs.html for more information

    gpg: Interrupt caught ... exiting


    (Bojie)-(boj-laptop)-(22:36:35)-(~/ra)-(git:master)-($?:130)
    (! 3537)-> gpg --output doc --decrypt ra.sig
    gpg: WARNING: unsafe permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: unsafe enclosing directory permissions on configuration file `/home/Bojie/.gnupg/gpg.conf'
    gpg: WARNING: using insecure memory!
    gpg: please see http://www.gnupg.org/documentation/faqs.html for more information
    gpg: Signature made Fri, Dec  5, 2014 10:36:12 PM CST using RSA key ID 5BABFFEE
    gpg: Good signature from "Bojie Li (USTC) <bojieli@gmail.com>"



