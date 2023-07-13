# miniTRASGO
Documentation and usage guide for the miniTRASGO Cosmic Ray telescope

## To edit the documentation:
The hierarchy of entries is simple: a new topic has to be added as a markdown file inside the /docs file. It can be edited and created online. To relate it to the final page the .yml has to be accessed and, in the 'nav' section just add the name of the new document.

Just send an email to us to get acces to the repository edition.

## To compile the page that has been edited online:
It is enough to clone the repository and build the page locally with 'mkdocs': the 'gh-deploy' command will automatically do the job. It only needs a token (password) to edit the online repository. The username can be anything.

You will need mkdocs, mkdocs-material and git. Then just execute this in the terminal:
    
    git clone https://github.com/cayesoneira/miniTRASGO.git
    cd miniTRASGO/
    mkdocs gh-deploy
    cd ..
    rm -rf miniTRASGO
