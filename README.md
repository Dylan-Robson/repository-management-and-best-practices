# Repository Management & Best Practices

## Legend

<table>
  <thead>
    <tr>
      <th>Instance</th>
      <th>Branch</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Stable</td>
      <td>stable</td>
      <td>Used to mirror the master branch for redundancy</td>
    </tr>
    <tr>
      <td>Working</td>
      <td>master</td>
      <td>Main branch to use for productionalized code & updates</td>
    </tr>
    <tr>
      <td>Feature/Issues</td>
      <td>Dev</td>
      <td>Branched off master/working and used to fix bugs or add features</td>
    </tr>
    <tr>
      <td>Hotfix</td>
      <td>hotfix</td>
      <td>Branch off stable and used for quick fixes</td>
    </tr>
  </tbody>
</table>

## Main Branch & Stable Branch

The main repository should have two branches:

* `master`
* `stable`

The main branch is considered the `master` and will be the main source code which always should reflect a the latest development changes for the
next version release. All other branches should be sourced from `master`.

The `stable` branch sits as a mirror image of a working `master` branch of productionalized code. This branch is for redundancy and should not be
interacted with.

When code is stable and working in the `master` branch and has been deployed, all changes will be merged into the `stable` and then tagged with a
release number.

## Support branches

Support branches are used as another source of parallel development for collaboration between team members, easing tracking of feature, and providing
a quick fix solution to live production issues. Unlike the main branch or stable branch, these are to be used to provide updates to production code
and have a limited lifespan due to being removed when production code is updated.

Different support branches to consider for a repo:

* Feature branches
* Bug branches
* Hotfix branches

Each branch has a specific usecase and typically has strict rules for their origin branch where they branched from and which branches they can merge
to.

### Feature Branches

Similar to a Dev Branch, these branches are used to test and introduce new features/enhancements that could potentially be added to production. If
features or enhancements meet the needs of the team then all changes will be reviewed for merging to the master branch.

Either the lead of the repository or similar can use the branch tool within Github to see if there have been commits since the feature (dev)
was branched. Any and all changes to `master` should be merged into the feature before merging back with changes to the `master` branch to
alleviate merge issues.

#### Working with a feature branch

If the branch doesn't exist, create the branch in a local environment and then push that branch back to the remote repo on Github. A feature branch should
always be a publiclly available branch to ensure all developnent by team members is in sync.

* Using git to create and push new branch
```
git checkout -b dev master                 // creates a local branch for developing new features
git push origin dev                       // pushes the dev/feature branch to the remote repo
```

```
git merge master                        // merge changes in the master branch to the dev branch
```

Typically when features are approved and merged to the master branch for production the feature branch is then deleted. This doesn't always have to be
the case depending on the team and or lifespan of feature additions to the code.

```
$ git checkout master                               // change to the master branch  
$ git merge --no-ff dev                             // makes sure to create a commit object during merge
$ git push origin master                            // push merge changes
$ git push origin :dev                              // deletes the remote branch
```

***Note that if you are developing in a windows based environment you can use the git-bash shell downloaded from the official[git](https://git-scm.com/download/win) site or setup git for windows terminal with the provided documentation on the site.



      
