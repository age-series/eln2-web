# Progress on Eln2

General progress information about Eln2 development can be found here.

# Week 18 (April 26 - May 2)

A slight hiatus while `Caeleron` has exams, `jrddunbr` has interviews.
* `Baughn` updated the codebase to 1.15.2 and included Bookshelf as our UMC replacement.

# Week 17 (April 19 - April 25)

* `Caeleron` worked on uarchComputer
* `Baughn` migrated us away from UMC. Baughn wanted something different after working with it briefly.
* `Grissess` did some work with the Falstad importer and fixed some other minor MNA bugs.

# Week 16 (April 12 - April 18)

* `jrddunbr` worked on various parsers and the AsmComputer
* `jrddunbr` and `Caeleron` worked on Vintage Story builds using VS Codium, as well as developing the Blueprint Core application
* `Caeleron` worked on code cleanup as well as working on a GNU Plot importing system.
* `Baughn` continued to work on CI progress and started working on Integration for Minecraft
* The community voted for Minecraft 1.14 development over Minecraft 1.12 development, after `Baughn` and `jrddunbr` noticed that it would be difficult to use Gradle 4.10.3 for any further progress on the project, and thinking that Miinecraft 1.12 did not support Gradle 5 and Forge Gradle 3.
* We are currently nearing the end of Phase 1. Woo!
* `Baughn` pulled in UMC as a Git Subtree.

# Week 15 (April 5 - April 11)

* `Baughn` helped us configure CI using GitHub actions and `Caeleron` worked on making our standardized tests meet those CI testing requirements.
* `Baughn` suggests we set up better tests which `Grissess` and `jrddunbr` will do.
* `Baughn` and `jrddunbr` set up the Discord chat on Eln to have new chat rooms for developers.
* `jrddunbr` updates the website as there is growing interest in doing Eln2 work. Website was not updated because website development tool was not cooperating.
* `Baughn` updated our Gradle configs and also helped us move to Gradle 5

# Week 13 - 14 (March 22 - April 4)

* We discovered Vintage Story is a thing and they have a much better modding API. `Caeleron` joins the dev team and focuses mostly on making Vintage Story moding work.
* `cam72cam` pushes a new UMC release that has a brand new Gradle deployment system that removes the need for special powershell/shell scripts to set up their environment. We have yet to integrate that into our codebase.

# Week 12 (Mar 15 - Mar 21)

* `Baughn` said he has free time coming up, and so we brought him up to speed some on how Eln2 development is going and how to contribute. He suggested we convert to a monorepo, and so we have [prepared such a repository](https://github.com/eln2/eln2). We are still waiting to hear from Grissess and get a concensus on that decision before going with it.

* `Grissess`, `Baughn`, and `jrddunbr` determined that the repository will be MIT licensed, and we will aim for CC0 or share-alike (commercial friendly). This will be fine, because UMC is LGPLv2.1, which allows us to have a different license so long as we keep our UMC on GitHub basically. There are two scripts in the Integration part of the mod code that are from IR-Integration, and so we may need those few files cleared as MIT to call the whole repo MIT, but we can also just use a license header in those applicable files.

# Weeks 4-11 (Jan 18 - Mar 14)

* We were both really busy, and did not have time to develop code. :/

# Week 3 (Jan 12 - Jan 18)

* `Grissess` works a lot on the MNA solver after `jrddunbr` tries to do some work but encounters some difficulty with configuring the datatypes efficiently. He also uses a similar methodology to the Falstad solver by having "stamps" that modify the matrix from the components. It's worth noting that the old MNA also had the concept of a stamp, and also had some matricies, but the names were a bit.. odd, and difficult to follow.
* `jrddunbr` writes a Falstad importer, which can ingest (basic) Falstad circuits and load them into the MNA for processing.

# Week 2 (Jan 5 - Jan 11)

* `jrddunbr` [set up a Travis CI page](https://travis-ci.com/jrddunbr/electrical-age-1.12) to have a build test on our commits and PR's. Plans are to hopefully have a CD pipeline at some point.
* `cam72cam` got back to us about UMC, and we began working to determine how to make UMC generic enough that two completely different mods can use it.
  * Quoting directly from `cam72cam` on the progress of UMC for newer versions:
    * 1.14.4 still needs support for injecting or generating recipes. I need to work on that at some point or have you two [`jrddunbr` and `Grissess`] help
    * I have no idea how any of the rendering will be able to be ported to 1.15.x
* `jrddunbr` set up the eln2.org website on GitHub Pages, after working with the DNS provider to determine why DNS was not propagating properly to some major resolvers.
* `jrddunbr` works on Kotlinizing the `sim` code
* `Grissess` works on figuring out the Gradle import code, turns out it's going to be more difficult than we thought.
* `jrddunbr` and `Grissess` work on determining how to use alternate MNA matrix math providers and make efficient wrappers around different math libraries for benchmarking.

# Week 1 (Jan 1 - Jan 4)

Beginning of the revived Eln2 efforts. Developers are `jrddunbr` and `Grissess`

* On Jan 1, 2020, [ eln2.org](https://eln2.org) was purchased. This allowed development using the `org.eln2.*` Java namespace to proceed without suddenly having the domain bought from under our feet.

* `jrddunbr` builds a new clean repo for eln2 dev, with just the old `mods.eln.sim` directory copied on top of a 1.12.2 Forge environment (refactored to `org.eln2.sim`) and all Minecraft related methods  (eg, NBT) deleted.

* Eln2 developers guide was created by `jrddunbr`

* `cam72cam` was contacted about [Universal Mod Core](https://github.com/TeamOpenIndustry/UniversalModCore)
  * UMC was selected because:
    * It supports MC 1.12
    * It is actively developed and maintained
    * It claims that it will support MC 1.14 and MC 1.15 in the near future, and has some decent work to show for it.
    * `Grissess` and `jrddunbr` know the developer personally.

* `Grissess` worked for three days on figuring out why we were having Gradle issues with importing UMC, but was unable to determine a reliable solution. Builds often failed as below:

```
FAILURE: Build failed with an exception.

* What went wrong:

Could not determine the dependencies of task ':UniversalModCore:compileJava'.
> Could not resolve all task dependencies for configuration ':UniversalModCore:forgeGradleMc'.
   > Could not find net.minecraftforge:forgeBin:1.12.2-14.23.4.2705.
     Searched in the following locations:
       - https://minecraft.curseforge.com/api/maven/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.pom
       - https://minecraft.curseforge.com/api/maven/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.jar
       - https://files.minecraftforge.net/maven/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.pom
       - https://files.minecraftforge.net/maven/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.jar
       - https://repo.maven.apache.org/maven2/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.pom
       - https://repo.maven.apache.org/maven2/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.jar
       - https://libraries.minecraft.net/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.pom
       - https://libraries.minecraft.net/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.jar
       - file:/home/travis/.gradle/caches/minecraft/deobfedDeps/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.pom
       - file:/home/travis/.gradle/caches/minecraft/deobfedDeps/net/minecraftforge/forgeBin/1.12.2-14.23.4.2705/forgeBin-1.12.2-14.23.4.2705.jar
       - file:/home/travis/.gradle/caches/minecraft/net/minecraftforge/forge/1.12.2-14.23.4.2705/snapshot/20171003/forgeBin-1.12.2-14.23.4.2705.jar
       - file:/home/travis/.gradle/caches/minecraft/net/minecraftforge/forge/1.12.2-14.23.4.2705/snapshot/20171003/forgeBin.jar
     Required by:
         project :UniversalModCore
```
