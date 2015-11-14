git-wtf
-------

A useful script that displays local & remote branches, what are in sync
and what need merging,\
and so on, like so:

    Local branch: heads/master
    [x] in sync with remote

    Remote branch: origin/master (git@github.com:account/project.git)
    [x] in sync with local

    Feature branches:
    [x] ticket_827 is merged in
    [ ] ticket_831 is NOT merged in (1 commit ahead; 18 commits behind)
        - [dependencies] Depend on library X, version Y [bfda321]

### Usage

Usage: git wtf [branch+] [options]

If [branch] is not specified, git-wtf will use the current branch. The possible
[options] are:

    -l, --long          include author info and date for each commit
    -a, --all           show all branches across all remote repos, not just
                        those from origin
    -A, --all-commits   show all commits, not just the first 5
    -s, --short         don't show commits
    -k, --key           show key
    -r, --relations     show relation to features / integration branches
        --dump-config   print out current configuration and exit

git-wtf uses some heuristics to determine which branches are integration
branches, and which are feature branches. (Specifically, it assumes the
integration branches are named "master", "next" and "edge".) If it guesses
incorrectly, you will have to create a .git-wtfrc file.

To start building a configuration file, run "git-wtf --dump-config >
.git-wtfrc" and edit it. The config file is a YAML file that specifies the
integration branches, any branches to ignore, and the max number of commits to
display when --all-commits isn't used.  git-wtf will look for a .git-wtfrc file
starting in the current directory, and recursively up to the root.

IMPORTANT NOTE: all local branches referenced in .git-wtfrc must be prefixed
with heads/, e.g. "heads/master". Remote branches must be of the form
remotes/<remote>/<branch>.


### Requirements
Ruby.

If you're on a Mac you've got it. If you're on Linux you've probably got
it. If you're on Windows you'll have to figure that out on your own.

### Installation

Put the `git-wtf` file into a directory on your path, or add this directory
to your path. [Google has many links with instructions](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=bash%20editing%20path) on editing your path if you don't know how.


## NOTE regarding maintenance / support
This particular script has an odd history. It was written, and apparently 
abandoned by [William Morgan](https://gitorious.org/willgit/mainline) then
cloned from gitorious to Github, where a few folks have forked and tweaked it,
and left notes in their README's about how the script is not maintained. 

**THIS ONE IS.**

I've pulled together some of those improvements and **do maintain this repo**.
If you've got changes or improvements please send me a PR.

### Contributors

* Daniel Vartanov
* Esteban Torres
* Kris Williams
* masukomi
* Michael Klishin
* Tom Meier
* Vincent Bonmalais
* William Morgan

### License
This is distributed under the GPL v3 license which can be found [here](http://www.gnu.org/licenses).
