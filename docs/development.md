# Eln 2 development

Some tidbits about development.

### Licensing

Right now `Grissess` and `jrddunbr` have basically written the mod from scratch. The current suggestion is to be alright with anything from MIT license up to the old Eln license, but likely we will LGPLv2+ unless we see reason to license it otherwise.

Models and artwork need to be under some creative commons license that allows modification and distribution.

### Language(s)

Eln2 is to be written in entirely **Kotlin**, except for where it is not possible.

Tutorials on Kotlin can be found online if you are familiar with Java. It is not too much different, but if you don't know what a functional programming language is, I'd suggest [reading at least part of this book](http://learnyouahaskell.com/learnyouahaskell.pdf) ([amazon](https://www.amazon.com/Learn-You-Haskell-Great-Good-dp-1593272839/dp/1593272839/)) before starting development.

Things like this:

```kotlin
val fruits = ["bananas", "oranges", "apples"]
val fruits2 = fruits.filter{"e" in it}.map{it.toUpperCase()}
fruits2.forEach{println(it)}
```

will possibly make a lot more sense after reading that book.

### Project Structure

There are multiple repositories:
  * [electrical-age-1.12](https://github.com/jrddunbr/electrical-age-1.12): The actual Minecraft part of Electrical Age 2, written for MC 1.12
  * [eln2-core](https://github.com/jrddunbr/eln2-core): The core code of Eln2. This code is intended to be 100% portable between MC versions.
  * [eln2-web](https://github.com/jrddunbr/eln2-web): This is the website you are reading.

Inside the repositories, you will find a lot of `org.eln2` repositories:

In the `electrical-age-1.12` repository, one will find roughly the following:

* `org.eln2`
    * `mc1.12`
        * `block`: all regular minecrafty blocks (ores, ..) that are not TE's
        * `item`: all items
        * `simplenode`: all single block TE's
        * `sixnode`: all sixnode (6 sides of a block) TE's
        * `multinode`: all multi block TE's

In the `eln2-core` repository, one will find roughly the following:

* `org.eln2`
    * `math`: all sorts of mathy stuff
    * `sim`: all sorts of simulation code (mna, electrical, thermal)

When you build Eln2, you will generally operate out of the `electrical-age-1.12` folder, and that will load in UMC as well as Eln2-core.

As a result, all of those imports will be accessible to be used for Minecraft code.

At some point, I want to move these repositories to `https://github.com/eln2`, namely, we would probably call them `eln2-mc-integration`, `eln2-core`, and `eln2-web` at that organization.

The different versions of the eln2 Minecraft integrations (say 1.12, 1.14, 1.15, etc) would be branches by those names on that repository, which matches the way that UMC is structured.

### Log collection server

For Eln2 pre-alpha development, we will have a crash log handler. What will happen is if the game crashes, we will automatically take the log, and send it out to the development team to a server that can recieve these logs and then we can process them.

This will aid in development, and will likely be removed at the alpha stage unless we find it useful. At the pre-alpha stage, we will also send the UUID of players to be sent back as well so that we know who had the bug.

## Phases

Just a FYI, these will all be copied sooner or later to GitHub issues, so that it's easier to track progress.

### Phase 1: UniversalModLib

- [ ] configure UniversalModLib
    - [ ] fix UniiversalModLib
    - [ ] package UniversalModLib
- [ ] config file disclaimer option (disables the mod unless the user agrees to not pester the devs before alpha)
- [ ] crash logger
- [ ] rebuild MNA from scratch (apparently)

#### Verification:

- [ ] running `./gradlew build` in the main workspace will prepare libraries and compile our mod to a functional jar
- [ ] works in TravisCI
- [ ] config option works

### Phase 2: SingleNode

I say models and textures, but these are basic as almost all of these items will be removed/edited later.

- [ ] SingleCable: a current based uninsulated cable that connects similarly to RF pipes
    - [ ] Electrical Sim
    - [ ] Thermal Sim
- [ ] SingleSource: a simple voltage source block
    - [ ] Electrical Sim
- [ ] SingleGround: a simple ground pin
    - [ ] Electrical Sim
- [ ] CreativeHeater: a simple thermal cable heater
    - [ ] Thermal Sim (creates heat at a predefined rate of energy)
    - [ ] Inventory Texture
    - [ ] Model
- [ ] Passive Cooler: a simple heatsink with no fan
    - [ ] Thermal Sim
    - [ ] Inventory Texture
    - [ ] Model (use existing 1.7.10?)
- [ ] Active Cooler: an simple heatsink with a fan (12v, 24W)
    - [ ] Electrical Sim
    - [ ] Thermal Sim
    - [ ] Inventory Texture
    - [ ] Model (use existing 1.7.10?)
- [ ] SingleSwitch: a current based uninsulated throw switch
    - [ ] Electrical Sim
    - [ ] Thermal Sim (similar to a cable, except when open we may reduce the thermal transfer)
- [ ] SingleResistor: a basic capacitor
    - [ ] Electrical Sim
    - [ ] Thermal Sim
- [ ] SingleCapacitor: a simple capacitor
    - [ ] Electrical Sim
    - [ ] Thermal Sim?
- [ ] SingleInductor: a simple inductor
    - [ ] Electrical Sim
    - [ ] Thermal Sim?
- [ ] Basic 12v Battery
    - [ ] Electrical Sim
    - [ ] Thermal Sim
    - [ ] Inventory Texture
    - [ ] Model (use existing 1.7.10?)

NOTE: Models are not a priority at this stage as most of the Single* items will be removed later.

#### Validation

- [ ] Verify Electrical Sim works and that reasonable currents are being moved. Get Matrix Size to the user
- [ ] Verify Thermal Sim works and that heat transfers through items properly
- [ ] Verify that WAILA-style integrations work with other mods.
- [ ] Verify that Capacitors work as they should IRL
- [ ] Verify that Inductors work as they should IRL
- [ ] Verify that Batteries work as they should IRL

### Phase 3: MultiNode

- [ ] autominer
- [ ] solar panels

### Phase 4: SixNode

- [ ] "New" SixNode
    - [ ] cables
    - [ ] switches
    - [ ] resistors
    - [ ] inductors
    - [ ] capacitors
    - [ ] lamp sockets
    - [ ] lamp supply
- [ ] Remove Single* or at least delist it (shadow registry)
- [ ] API v1.0
- [ ] Some reasonable textures

### Phase 5: Alpha Release and debugging

- [ ] remove developer disclaimer config
- [ ] Initial rounds of bugfixing

### Phase 6: Machines and equipment

In no particular order:

- [ ] mod integration
    - [ ] pay back IR folks by making electric trains a bit more electric
        - [ ] cantenaries (over track wires)
    - [ ] oredict
- [ ] Machines
    - [ ] crusher - 100v to 800v
    - [ ] roller - 100v to 800v
    - [ ] press - 100v to 400v
    - [ ] air compressor - 12v to 400v
    - [ ] saw  - 12v to 200v
    - [ ] experimental teleporter
- [ ] Pole update material:
    - [ ] data cables, fiber (Sigbus, OC/CC)
        - [ ] fiber box
    - [ ] 200v, 480v? (lower wires)
    - [ ] 16kV (standard height poles)
    - [ ] 125kV power transmission (extra height poles and power transmission)
    - [ ] 220kV power transmission (power transfer towers)
- [ ] Underground cable transmission
    - [ ] manholes
    - [ ] underground fiber
        - [ ] fiber box
    - [ ] <2kV cables/sigbus
        - [ ] Ground transformer
- [ ] Shaft Networks:
    - [ ] generator
    - [ ] motor
    - [ ] turbines
    - [ ] clutch
    - [ ] static shaft
    - [ ] shaft machines
        - [ ] crusher
        - [ ] roller
        - [ ] saw
        - [ ] air compressor
- [ ] Steam and Oil Processing
    - [ ] Oil fields
    - [ ] Oil rigs (factorio-esque with diminishing returns)
    - [ ] Oil Processing Tanks
    - [ ] Biofuel Processing
    - [ ] Solar Tower (generates steam from heat)
    - [ ] *Nuclear Reactor* (generates hot coolant)
        - [ ] Liquid Heat Exchangers (uses hot coolant and water to make steam and cold coolant)
    - [ ] More efficient gas turbine operationv (~60% return in lost heat energy)
        - [ ]Gas Heat Exchangers - uses exhaust from gas turbines to heat water to make steam
- [ ] Ore Processing
    - [ ] Some kind of *something*
