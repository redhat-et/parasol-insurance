# Git and branching workflow for developers

Note: The latest code is not in the main branch of the repo but in release or version specific branches that mirror corresponding branches from the parent repository (for example the main-rhoai-2.13 branch). Hence your changes/ PRs need to be merged into this branch and not into main.  Here is a git dev and branching workflow that you can follow to do this. 

1. This assumes you already have created a personal fork created off redhat-et's parasol project (which itself is a fork of the aiservices bu's parasol project). In my case this personal form would be
https://github.com/srampal/parasol-insurance

1. Clone your local fork locally. For example
git clone git@github.com:srampal/parasol-insurance.git

1. Move into the local cloned repo
cd parasol-insurance

1. Check the list of remotes, currently there should be only 1 viz the origin pointing to your personal fork
git remote -v

1. Now add a remote called upstream to point to the rehat-et fork
git remote add upstream git@github.com:redhat-et/parasol-insurance.git

1. Now when you check the list of remotes, you will see 2
git remote -v

origin	git@github.com:srampal/parasol-insurance.git (fetch)
origin	git@github.com:srampal/parasol-insurance.git (push)
upstream	git@github.com:redhat-et/parasol-insurance.git (fetch)
upstream	git@github.com:redhat-et/parasol-insurance.git (push)

1. Now fetch branches from the upstream repo
git fetch upstream

1. Now create a local branch for your planned fix but set it to track the main-rhoai-2.13 branch from the upstream repo.

git checkout -b fix --track upstream/main-rhoai-2.13

1. Now make the changes ndded for your fix or feature

1. When the changes are complete, tested and ready to push, DO NOT not perform the default git push since upstream tracking has been set to the upstream repo and not origin. Hence explicitly push to origin as follows

git push origin fix

1. Now on github, when you see the option to create a PR, you need to change the destination/ target branch of the PR to be the main-rhoai-2.13 branch of the upstream repo redhat-et/parasol-insurance. (and not the default draft PR suggestion by github which will point to the main branch as the destination branch)

1. After PR review and merge, if you navigate to the upstream repo
(redhat-et/parasol-insurance) on github, you will also see a suggestion to create a PR to merge changes into the main branch. DO NOT follow this suggestion. Ignore it since per our current project branching plan, we are keeping our final code in the main-rhoai-2.13 branch and not in main.

