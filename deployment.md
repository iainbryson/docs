
### Abstract

This document describes the deployment design.  It begins from the state in Febryary, 2017: deployment is a semi-manual process:

1. SSH into the machine
2. CD into the enote directory
3. Pull with `./git-all.sh pull origin`
4. Run & build with `./run.sh`
5. Check that everything worked

We wish to improve this, with the following goals:


###
