# Eln 2 agenda

## Phases

These are better expressed in the Kanban boards on GitHub.

[ [General Development Board](https://github.com/orgs/age-series/projects/1) ]

[ [MNA](https://github.com/orgs/age-series/projects/6) ]
[ [Sim](https://github.com/orgs/age-series/projects/5) ]
[ [Blocks](https://github.com/orgs/age-series/projects/4) ]
[ [Items](https://github.com/orgs/age-series/projects/3) ]

## Phase 1: MNA Code [DONE]

Core:

- [x] MNA finished

## Phase 2: SingleNode [IN PROGRESS]

Kanban board: [Phase 2 Projects](https://github.com/orgs/age-series/projects/2)

- [ ] config file disclaimer option (disables the mod in un-obfuscated contexts, unless the user agrees to not pester the devs before 1.0)

- [ ] Basic Sim API (not mod-integration ready necessarily)

- [ ] Thermal Networks:
    - [ ] CreativeHeater: a simple thermal cable heater
    - [ ] Heatsink: a simple heatsink with no fan
    - [ ] Heatsink with a fan: a simple heatsink with a fan (12v, 24W)

- [ ] Shaft Networks:
    - [ ] generator
    - [ ] motor
    - [ ] turbines
    - [ ] clutch
    - [ ] static shaft

- [ ] Electrical Networks (with Thermal System)
    - [ ] SingleCable: a current based uninsulated cable that connects similarly to RF pipes
    - [ ] SingleSource: a simple voltage source block
    - [ ] SingleGround: a simple ground pin
    - [ ] SingleSwitch: a current based uninsulated throw switch
    - [ ] SingleResistor: a basic capacitor
    - [ ] SingleCapacitor: a simple capacitor
    - [ ] SingleInductor: a simple inductor
    - [ ] Basic 12v Battery

NOTE: Models are not a priority at this stage as most of the Single* items will be removed later.

## Phase 2.5: Sim Revisit

Cameron wants to revisit the Electrical Simulator code after we finish Node.

If you want a good read, you shoud find a book about non-linear dynamic circuit systems.

Theoretically, this fixes our issues with InterSystem from the 1.7.10 version of Electrical Age.

## Phase 3: MultiNode

- [ ] Ghost Node implementation
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

- [ ] Initial rounds of bug fixing
- [ ] Some reasonable textures
- [ ] API v1.0 Stabilization (for mod compatibility)
- [ ] Documentation subsystem using [Patchouli](https://www.curseforge.com/minecraft/mc-mods/patchouli)
    - [ ] Write a converter to make this also presented on the website.
- [ ] PDF "Datasheets" for components, akin to the ones in [Shenzhen I/O](https://usermanual.wiki/Document/SHENZHENIOManual.736522646/view)
- [ ] Mod translation code

When done:

- [ ] remove developer disclaimer config
- [ ] Release 2.0

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
