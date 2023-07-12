# miniTRASGO
Documentation and usage guide for the miniTRASGO Cosmic Ray telescope

## To edit the documentation:
The hierarchy of entries is simple: a new topic has to be added as a markdown file inside the /docs file. It can be edited and created online. To relate it to the final page the .yml has to be accessed and, in the 'nav' section just add the name of the new document.

## To compile the page that has been edited online:
It is enough to clone the repository and build the page locally with 'mkdocs': the 'gh-deploy' command will automatically do the job. It only needs a username and the token (password) to edit the online repository.
    
    git clone https://github.com/cayesoneira/miniTRASGO.git
    cd miniTRASGO/
    echo "Username: cayesoneira"
    echo "Password: ghp_AzAM7F6V7BoLXjy6EStNLUHK7CHHf71tjYL"
    echo "Password (fine grained token): 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"
    mkdocs gh-deploy
    cd ..
    rm -rf miniTRASGO
