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
  * `integration-mc<version>` - Basically, a Minecraft mod

## Log collection server

For Eln2 pre-alpha development, we will have a crash log handler. What will happen is if the game crashes, we will automatically take the log, and send it out to the development team to a server that can receive these logs and then we can process them.

This will aid in development, and will likely be removed at the alpha stage unless we find it useful. At the pre-alpha stage, we will also send the UUID of players so that we know who had the bug.

## Phases

Just a FYI, these will all be copied sooner or later to GitHub Kanban boards, so that it's easier to track progress. There will be a proper set of milestones for this on each of the relevant repositories.

## Phase 1: Modding Integration [DONE]

Core:

- [x] MNA finished

## Phase 2: SingleNode [IN PROGRESS]

I say models and textures, but these are basic as almost all of these items will be removed/edited later.

- [ ] Basic Sim API (not mod-integration ready necessarily)

- [ ] SingleCable: a current based uninsulated cable that connects similarly to RF pipes
- [ ] SingleSource: a simple voltage source block
- [ ] SingleGround: a simple ground pin
- [ ] CreativeHeater: a simple thermal cable heater
- [ ] Heatsink: a simple heatsink with no fan
- [ ] Heatsink with a fan: a simple heatsink with a fan (12v, 24W)
- [ ] SingleSwitch: a current based uninsulated throw switch
- [ ] SingleResistor: a basic capacitor
- [ ] SingleCapacitor: a simple capacitor
- [ ] SingleInductor: a simple inductor
- [ ] Basic 12v Battery

- [ ] Shaft Networks:
    - [ ] generator
    - [ ] motor
    - [ ] turbines
    - [ ] clutch
    - [ ] static shaft

NOTE: Models are not a priority at this stage as most of the Single* items will be removed later.

Log Server:

- [ ] Centralized log collection server (might be postponed)
- [ ] config file disclaimer option (disables the mod in un-obfuscated contexts, unless the user agrees to not pester the devs before 1.0)
- [ ] crash logger code (catch Minecraft crashes?)

## Phase 3: MultiNode

- [ ] solar panels
- [ ] wind turbines
- [ ] autominer

## Phase 4: SixNode (Tiny Node if FMB?)

- [ ] "New" SixNode
    - [ ] cables
    - [ ] switches
    - [ ] resistors
    - [ ] inductor
    - [ ] capacitor
    - [ ] lamp sockets
    - [ ] lamp supply
- [ ] Remove Single* or at least de-list it (shadow registry)

## Phase 5: Alpha Release and debugging

- [ ] remove developer disclaimer config
- [ ] Initial rounds of bug fixing
- [ ] Some reasonable textures
- [ ] API v1.0 Stabilization (for mod compatibility)

## Phase 6: Machines and equipment

In no particular order:

- [ ] mod integration
    - [ ] oredict (items, fluids, gasses)
- [ ] Machines
    - [ ] crusher
    - [ ] air compressor
    - [ ] experimental teleporter
- [ ] Woodworking
    - [ ] saw
- [ ] Metalworking
    - [ ] lathe (electric, shaft)
    - [ ] mill (electric, shaft)
    - [ ] drill press (electric, shaft)
    - [ ] shaper (electric, shaft)
    - [ ] press break (manual, electric, shaft)
    - [ ] english wheel (electric, shaft)
    - [ ] oxy-acetylene torch (gas)
    - [ ] hot riveting machine (electric, shaft)
    - [ ] electric welder (electric)
    
- [ ] Industrial Metwalworking
    - [ ] rolling machine (electric, shaft)
    - [ ] forge hammer (electric, shaft)
    - [ ] forge heater (thermal)

- [ ] Pole update material:
    - [ ] data cables, fiber (Sigbus, OC)
        - [ ] fiber box
    - [ ] 200v, 480v (lower wires)
    - [ ] 16kV (standard height poles)
    - [ ] 125kV power transmission (extra height poles and power transmission)
    - [ ] 220kV power transmission (power transfer towers)
- [ ] Underground cable transmission
    - [ ] manholes
    - [ ] underground fiber
        - [ ] fiber box
    - [ ] <2kV cables/sigbus
        - [ ] Ground transformer
- [ ] Steam and Oil Processing
    - [ ] Oil fields
    - [ ] Oil rigs (factorio-esque with diminishing returns)
    - [ ] Oil Processing Tanks
    - [ ] Biofuel Processing
    - [ ] Solar Tower (generates steam from heat)
    - [ ] *Nuclear Reactor* (generates hot coolant)
        - [ ] Liquid Heat Exchangers (uses hot coolant and water to make steam and cold coolant)
        - [ ]Gas Heat Exchangers - uses exhaust from gas turbines to heat water to make steam
