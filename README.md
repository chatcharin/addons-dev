# addons-dev

Addons Forge

## Typical addon creating workflow:

* [Init](#init) - once per computer
* [Create new branch](#create-new-branch) - once per module (or set of modules). For managers only, because push access is needed.
* [Get branch from upstream](#get-branch-from-upstream) - once per module
* [Work](#work) - as much as needed.
* [Make final PR to target repo](#make-final-pr-to-target-repo) - once per module

# Init

1. Fork this repo
2. Clone to your machine:

        git clone git@github.com:USERNAME/addons-dev.git

3. Add remotes

        cd addons-dev

        git remote add upstream          git@github.com:yelizariev/addons-dev.git
        git remote add addons-yelizariev https://github.com/yelizariev/addons-yelizariev.git
        git remote add pos-addons        https://github.com/yelizariev/pos-addons.git
        git remote add mail-addons       https://github.com/yelizariev/mail-addons.git
        git remote add access-addons     https://github.com/yelizariev/access-addons.git
        git remote add website-addons    https://github.com/yelizariev/website-addons.git
        git remote add l10n-addons       https://github.com/yelizariev/l10n-addons.git

# Create new branch

    # specify target, repo and branch:
    export REPO=addons-yelizariev BRANCH=9.0 FEATURE=some_feature

    # fetch remote
    git fetch ${REPO}

    # create new branch
    git checkout -b ${REPO}-${BRANCH}-${FEATURE} ${REPO}/${BRANCH}

    # push to upstream
    git push upstream ${REPO}-${BRANCH}-${FEATURE}
    
    # done

# Get branch from upstream


    # get branch from upstream
    git fetch upstream addons-yelizariev-9.0-some_feature
    git checkout -b addons-yelizariev-9.0-some_feature upstream/addons-yelizariev-9.0-some_feature


# Work

   
    # work and make commits
    git commit ...
   
    # push to origin
    git push origin addons-yelizariev-9.0-some_feature
   
    # create pull request via github interface to yelizariev/addons-dev repo


# Make final PR to target repo

    # example for addons-yelizariev
    cd /path/to/addons-yelizariev

    # add remote if it doesn't exist yet
    git remote add addons-dev https://github.com/yelizariev/addons-dev.git

    # fetch remote
    git fetch addons-dev

    # create branch
    git checkout -b 9.0-some-feature addons-dev/addons-yelizariev-9.0-some_feature

    # push to your fork of target repo
    git push origin 9.0-some-feature

    # create PR to target repo
