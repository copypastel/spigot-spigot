Spigot - DEV BRANCH NOTES
======

The intent of this branch is to circumvent the need to deal with the
spigot build process for normal development, and to facilitate
productive plugin development.

The spigot build process is normally something like:

- check out the buildtools project
- run a build, which:
- gets bukkit, craftbukkit
- gets the latest minecraft release and decompiles it
- applies patch files to aforementioned code
- then, finally, builds a spigot server jar

In normal dev and release, we want to ignore all of the
stuff that happens prior to the patching phase. That is,
we want to deal with ready-to-execute spigot server code.
The branches (in bukkit, craftbukkit, and spigot projects)
that capture this post-patch state of the code are all called
`patched-for-dev`.

The changes we add to this base server code are all captured on
these `dev` branches, where dev is a branch off of `patched-for-dev`.
We will build our own releases off of `dev` (er...um...maybe we
should rethink the branch name??).

So then in the future when we want to update the core server code
to the latest minecraft release, we would use the normal `buildtools`
process to get to the point where we have proper patched code for
that release. Then we would repoint the three `patched-for-dev` branches
at that patched code. Then we would rebase `dev` branches on top of the new
`patched-for-dev` branches.



Spigot
======

High performance Minecraft server implementation


How To
-----------

Init a Craftbukkit and Bukkit module : `git submodule update --init`

Apply Patches : `./applyPatches.sh`

### Create patch for server ###

`cd Spigot-Server`

Add your file for commit : `git add <file>`

Commit : `git commit -m <msg>`

`cd ..`

Create Patch `./rebuildPatches.sh`

### Create patch for API ###

`cd Spigot-API`

Add your file for commit : `git add <file>`

Commit : `git commit -m <msg>`

`cd ..`

Create Patch `./rebuildPatches.sh`




Compilation
-----------

We use maven to handle our dependencies.

* Install [Maven 3](http://maven.apache.org/download.html)
* Clone this repo and: `mvn clean install`
