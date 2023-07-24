# miniTRASGO documentation
Reposotory used to host the documentation and usage guide for the miniTRASGO Cosmic Ray telescope. This page is deployed through `mkdocs`, a python-based resource to build html pages from a simple tree of markdown files.

## To edit the documentation:
The hierarchy of entries is simple: a new topic has to be added as a markdown file inside the /docs file. It can be edited and created online. To relate it to the final page the `.yml` has to be accessed and, in the 'nav' section, just added with its path in the repository.

Just send an email to us to get access to the repository edition, even though you could create a branch of the reository and wait until our aproval.

## Two ways of compiling and deploying the page that has been edited online
We are currently using the one where we need a url. Currently we have automatically programmed it to execute every hour.

### Standard mkdocs method
It is enough to clone the repository and build the page locally with 'mkdocs': the 'gh-deploy' command will automatically do the job. It only needs a token (password) to edit the online repository. The username can be anything.

You will need mkdocs, mkdocs-material (pip install them) and git. Then just execute this in the terminal:
    
    git clone https://github.com/cayesoneira/miniTRASGO.git
    cd miniTRASGO/
    mkdocs gh-deploy
    cd ..
    rm -rf miniTRASGO

### If you already have a site (with its url)
Configure the ssh config file to add the following directions:

    Host nuclab2
        HostName nuclab2.fis.ucm.es
        User petgfn
        PubkeyAcceptedAlgorithms +ssh-rsa
        HostkeyAlgorithms +ssh-rsa
        KexAlgorithms +diffie-hellman-group1-sha1
    Host nuc1
        Hostname nuc1.fis.ucm.es
        User petgfn

The computer `nuc1` is the one from which the page has to be deployed, but we can only access to it from the nuclab2 as a tunnel. Connect to the `nuc1` using the `nuclab2` as bridge with the following order:

    ssh -J nuclab2 nuc1

Once in the `nuc1`, execute the following command:

    /home/www/html/update-minitrasgo.sh
