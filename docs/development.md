# Eln 2 development

Some tidbits about development.

## Licensing

Eln2 is licensed under the MIT license.

Models and artwork need to be under some creative commons license that allows modification and distribution *with* commercial use, [such as this license](https://creativecommons.org/licenses/by-sa/4.0/).

## Languages

Eln2 Core, Apps, and Minecraft Integration is going to be written in Kotlin. Network sockets and shared memory will use Google Protobuffs, and Vintage Story will use C#. The log server uses Rust.

## Project Structure

There are two repositories:
  * [eln2](https://github.com/eln2/eln2): This is all of the Eln2 code.
  * [eln2-web](https://github.com/eln2/eln2-web): This is the website you are reading.

Inside the `eln2` repository, you will find multiple folders:
  * `core` - All of the core MNA, thermal, and shaft based simulation code. No Minecraft or VS code ends up here.
  * `apps` - Standalone Applications and daemons.
  * `integration-mc<version>` - Integration code that is between `core` and Minecraft Forge/Bookshelf.
  * `integration-vs` - Integration code that is between `core` and the Vintage Story Modding API.
  * `logcollector` - our Rust log collector.

## Log collection server

For Eln2 pre-alpha development, we will have a crash log handler. What will happen is if the game crashes, we will automatically take the log, and send it out to the development team to a server that can receive these logs and then we can process them.

This will aid in development, and will likely be removed at the alpha stage unless we find it useful. At the pre-alpha stage, we will also send the UUID of players so that we know who had the bug.

## Phases

Just a FYI, these will all be copied sooner or later to GitHub issues, so that it's easier to track progress. There will be a proper set of milestones for this on each of the relevant repositories.

## Phase 1: Modding Integration [DONE]

Core:

- [x] MNA finished

Minecraft:

- [x] configure UniversalModLib

Vintage Story:

- [x] Make build environment cross-platform with easy to use instructions

## Phase 2: SingleNode [IN PROGRESS]

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

Log Server:

- [ ] Centralized log collection server
- [ ] config file disclaimer option (disables the mod unless the user agrees to not pester the devs before alpha)
- [ ] crash logger

## Phase 3: MultiNode

- [ ] solar panels
- [ ] wind turbines

## Phase 4: SixNode

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

## Phase 5: Alpha Release and debugging

- [ ] remove developer disclaimer config
- [ ] Initial rounds of bugfixing

## Phase 6: Machines and equipment

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
