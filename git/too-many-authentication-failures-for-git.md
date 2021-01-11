# Too many authentication failures for git

My colleague had a problem to push changes to a remote. We encountered that he was using a lot of ssh-keys (about 10!).
 
With the command `ssh -v git@gitlab.xxx.de` we tried to connect to the system and we saw the following output:

    debug1: Offering RSA public key: /Users/abc/.ssh/id_rsa.cn0
    debug1: Authentications that can continue: publickey,password,hostbased
    debug1: Offering RSA public key: /Users/abc/.ssh/id_rsa.cn6
    debug1: Authentications that can continue: publickey,password,hostbased
    debug1: Offering RSA public key: /Users/abc/.ssh/id_rsa.cn1
    debug1: Authentications that can continue: publickey,password,hostbased
    debug1: Offering RSA public key: /Users/abc/.ssh/id_rsa.cn2
    debug1: Authentications that can continue: publickey,password,hostbased
    debug1: Offering RSA public key: /Users/abc/.ssh/id_rsa.cn5
    debug1: Authentications that can continue: publickey,password,hostbased
    debug1: Offering RSA public key: /Users/abc/.ssh/id_rsa.cn8
    Received disconnect from 192.168.100.218: 2: Too many authentication failures for git
    
The last line gives the error-message `Too many authentication failures for git` and just before the last line you can see a lot keys that were tried to login.
 
## Fix it in .ssh/config

The error can be prevented by telling ssh the specific `IdentifyFile` which should be used for the system. We added the following lines to `.ssh/config`.

    Host            gitlab.xxx.com
      Hostname        gitlab.xxx.com
      User            git
      IdentityFile    ~/.ssh/id_rsa.gitlab
      IdentitiesOnly yes