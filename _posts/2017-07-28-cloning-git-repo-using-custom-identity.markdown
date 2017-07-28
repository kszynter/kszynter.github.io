---
layout: post
title:  "cloning git repo using custom identity"
date:   2017-07-28 10:50:29 +0200
categories:  ssh git github
---
If you cannot clone your own github repository and you see 'Permission denied (publickey)' like this one:

    $ git clone git@github.com:kszynter/kszynter.github.io.git
    Cloning into 'kszynter.github.io'...
    Permission denied (publickey).
    fatal: Could not read from remote repository.
    
    Please make sure you have the correct access rights
    and the repository exists.

It's because there's a problem matching identities between github repository and your local computer.
First of all go check if you have any (public) SSH keys added to your github account [1]. If you have,
then this needs to match (private and public) key pair locally. They are by default stored in:

    # windows
    C:\Users\%USERNAME%\.ssh

    # linux
    ~/.ssh/

If you have any files there, they are named similar to this:

    $ ls -1
    id_rsa
    id_rsa.pub

The one with a .pub suffix is a public key, and the other one is a private one. Both are what is called a key pair.
You need to add the public one to your github account [2].

If you don't have any files there or even the folder doesn't exist then you have to create a new RSA key pair [3]
and then add it to your github account [2].

Finally, if the git still can't match the identities (for example you can have multiple key pairs) then you need to
instruct git which one to use [4].

Links
=
[1] [github.com](https://github.com/settings/keys)

[2] [github.com](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

[3] [github.com](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)

[4] [superuser.com](https://superuser.com/a/232406)
