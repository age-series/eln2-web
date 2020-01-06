# Progress on Eln2

General progress information about Eln2 development can be found here.

# Week 2 (Jan 5 - Jan 11)

* `jrddunbr` [set up a Travis CI page](https://travis-ci.com/jrddunbr/electrical-age-1.12) to have a build test on our commits and PR's. Plans are to hopefully have a CD pipeline at some point.
* `cam72cam` got back to us about UMC, and we began working to determine how to make UMC generic enough that two completely different mods can use it.
  * Quoting directly from `cam72cam` on the progress of UMC for newer versions:
    * 1.14.4 still needs support for injecting or generating recipes. I need to work on that at some point or have you two [`jrddunbr` and `Grissess`] help
    * I have no idea how any of the rendering will be able to be ported to 1.15.x
* `jrddunbr` set up the eln2.org website on GitHub Pages, after working with the DNS provider to determine why DNS was not propagating properly to some major resolvers.

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
