# repo-cleaning-experiments

This repo demonstrates the effects of the bfg secrets removal tool on hashes both on merged branches and on tags.  By performing the steps below, I have demonstrated that tags created before use of bfg on a mirror are mapped successfully to their new hashes, and that the same is true even of merged and stale branches.  You can browse this repo to prove to yourself that the tags are unharmed, and the history is healthy and squeaky clean.  

The only downside to using bfg is that you cannot purge secrets from a Pull Request with it, since GitHub does not allow PR history modification.  If you wish to remove them, you would have to contact GitHub support.  However, since PR history is not cloned, there is limited risk to having secrets in a PR. 

Best practice dictates that when a secret is committed to git, you should:  
- Rotate the secret  
- Purge it from git  
- Purge it from git history with bfg, or filter-repo, etc  

Steps taken:  
- Clone the fresh repo
- Create a branch
- Make a change on that branch
- Push
- PR
- Merge
- Pull main
- Tag main
- Push tag

- Create branch 2
- Make a change on that branch
- Push
- PR
- Merge
- Pull main
- Tag main
- Push tag
- Create branch 3
- Remove secret
- Push
- PR
- Merge
- Clone a mirror
- Create secret file
- Run bfg replace text
- reflog + gc
- Force push

