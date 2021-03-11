# Contributing to Eln2

Feel free to introduce yourself on our [Discord](https://discord.gg/YjK2JAD)!

You can make pull requests or issues, but please note that we are currently focused on making the mod functional, before adding major content and reviewing game balance.

## Licensing

Eln2 is licensed under the MIT license.

Models and artwork are [CC0](https://creativecommons.org/share-your-work/public-domain/cc0/) unless otherwise noted.

## Project Languages

#### Kotlin:
* Core
* Apps
* Minecraft

#### Google Protobuffs:
* Network sockets
* Shared memory

#### Rust:
* Log collector
* Optimized Sim code? (later date)

#### C#:
* Vintage Story

#### Markdown:
* https://eln2.org, compiled with MkDocs
* Most documentation

## Project Structure

* apps: Standalone applications and daemons
    * Asm Computer UI
* core: Core simulation code
    * compute: Various computer architectures for signal processing and other purposes
    * debug: Debug helpers
    * math: Math helpers
    * parsers: Parsers and import/export tools
    * sim: Electrical and Thermal simulators
    * space: various data structures and algorithms
* integration-mc1-16: Minecraft 1.16.5 Integration Code
* proto: A set of [Google Protocol Buffers](https://developers.google.com/protocol-buffers) for communication with all of our applications (proto3)

## Setting up the code development environment

In general, these instructions are roughly the same for Windows, Mac, and Linux.

### Tools Needed

You need:
* Intellij IDEA (Community Edition is sufficient) [[link](https://www.jetbrains.com/idea/download/)]
    * For a better experience, optionally install the Jetbrains Toolbox and then install IDEA [[link](https://www.jetbrains.com/toolbox-app/)]
* Git version control CLI:
    * Windows: [[link](https://git-scm.com/downloads)]
    * Mac: `brew install git`
    * .deb based: `apt install git`
    * .rpm based: `yum install git` (`dnf install git` for Fedora)
    * Arch Linux based: `pacman -Syu git`
* Java 8 SDK. There are a few options:
    * Oracle Java 8 SDK (paid) [[link](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)]
    * AdoptOpen JDK 8 (LTS) HotSpot SDK [[link](https://adoptopenjdk.net/?variant=openjdk8&jvmVariant=hotspot)]
    * IBM SDK 8 [[link](https://developer.ibm.com/javasdk/downloads/sdk8/)]
    * Amazon Corretto 8 [[link](https://docs.aws.amazon.com/corretto/latest/corretto-8-ug/what-is-corretto-8.html)]
    * .deb based: `apt install openjdk-8-jdk`
    * .rpm based: `yum instal java-1.8.0-openjdk` (`dnf install java-1.8.0-openjdk` for Fedora)
    * Arch Linux based: `pacman -Syu jdk8-openjdk`

IDEA will also install Java 11 or so, but that will not work for Eln2 development last we checked.

### Clone the repository

First, clone the repository down in whatever method works best for you. Winodws users will want to use Git Bash for these commands.

For most people, use this command. It will create a folder with the repository data.

`git clone https://github.com/eln2/eln2.git`

If you have a GitHub account with SSH keys on it, use this instead:

`git clone git@github.com:eln2/eln2.git`

Once you have downloaded the repository, configure Git:

```sh
git config --global user.name Your Name (or GitHub alias)
git config --global user.email Your Email
```

### Start and configure IDEA

IDEA is pretty simple.

1. Start the application, then say "Open or Import".
2. Find the `build.gradle.kts` file in the root of the repository, then click next.
3. Select all defaults on following screens.

## Add build configurations, and run

From the main IDEA window, you can configure different tasks to run with Gradle.

1. In the upper right, click `Edit Configurations...`
2. Inside this menu, on the top left, click the `+` sign
3. Select Gradle
4. Ignoring the name field, click the folder icon with the blue square next to the text box for Gradle Project
5. Depending on the task you want to run, select the correct project namespace (see below)
6. Enter the task name (see below)
7. Optionally, change the name for this build/run configuration

Different build configurations:

| Project Namespace | Task Name | Task purpose |
| --- | --- | --- |
| eln2:core | test | Tests the Eln2 Core |
| eln2:core | build | Builds the Eln2 Core, running tests |
| eln2:apps | build | Builds the Eln2 Applications (requires eln2:core automatically) |
| eln2 | build | Builds and runs tests for all of Eln2 |
| eln2 | bundle | Builds and runs tests for all of Eln2 |
| eln2:integration-mc-1-16 | runClient | Runs a minecraft client in a development environment (no username, cannot connect to servers) |
| eln2:integration-mc-1-16 | runServer | Runs a minecraft server in a development environment |
| eln2:integration-mc-1-16 | publish | Supposedly, builds a usable Minecraft mod. You will need to install Bookshelf, Forge, and some other tidbits... |

## Helpful resources for contributing

Please see the [library page](library.md) for helpful tips, documents, and inspiration.

We also have a Google Drive with a bunch of planning documents [here](https://drive.google.com/drive/folders/1rWXCEy9EQmKbeYGKnJssirRZnXX0fHkj).

## PR Guidelines

* Please use concise subject messages on commits, and a commit message body explaining the changes is highly encouraged.
* Keep commits in a PR to one topic, if possible. This permits us to use version control to find software regressions more easily.
* Avoid mass operations such as folder moves and restructures next to logical changes in the code in the same commit. It makes the commit diffs messy and difficult to follow.
* Use the PR message on GitHub to describe changes; use markdown check marks to show intended progress towards a goal.
* Keep your PR up to date with the `dev` branch to ease merges. It is preferred that you rebase rather than merge where possible.
* PR's should come with their code documented and unit tested (as much as possible, as decided by the head developers).
* If you make a PR, you agree to the licenses of the project, and that the code and content you are contributing complies with the applicable license.

## Branch Naming

Please use concise names that accurately describe what you are doing.
For example, `feature/add-variable-resistor` may describe some new Variable Resistor you are adding.

The following naming convention is to be used.

* `dev` – Branch that all of the developers work out of.
* `stable` - When applicable, stable releases of the code
* `feature/(branch name)` – Branches created by developers that add new features

Unit testing should be sufficient for watching for errors in the code. If a buf is found, push a fix and push a release.
Releases will just be simple release tags/labels on the `dev` or `stable` branch.

## Contributing via GitHub

This guide tries its best to make sure you don't need to know too much Git, but you may need help.

1. Make the changes you want to make
2. `git checkout -b feature/<your new feature>`
3. Verify that you have changed what you want by running `git status`
4. `git add .`
5. `git commit`
6. Push the code to upstream
    * If you have Eln2 repository access
        1. `git push origin feature/<your new feature>` (as above)
    * If you do not have access:
        1. Fork the repo on GitHub
        2. Push the code
            * If you used the repo links above to clone, do:
                1. `git remote add fork <your repositories remote url>` (for example, `https://github.com/<github username>/eln2.git`)
                2. `git push fork feature/<your new feature>` (as above)
            * Otherwise, do:
                1. `git push origin feature/<your new feature>` (as above; "origin" is your fork in this case)
7. Make a pull request. If you are confident that you are done with writing the code, and it meets contribution guidelines, then make it as a standard pull request. Otherwise, select the down arrow and then `Draft PR` and then click Create Pull Request.
8. If you have further changes, start with step 3 and continue to step 6. It will update the PR with changes automatically.
9. Wait for someone to accept or reject your PR. We get email notifications when PR's are created. We may make suggestions, in which you fix your code and come back to us with those changes.
10. Once your code is merged, `git checkout dev` and then `git pull --ff-only`.

## Other Contributing options

If you are not comfortable with your Git-fu, you send your repository state or proposed textures/models/sounds as a zip/7z/tar to [jrddunbr@ja4.org](mailto:jrddunbr@ja4.org).

You can also send textures in the [Electrical Age Discord](https://discord.gg/YjK2JAD), but we ask that you please archive your contributions to prevent Discord from lossy compressing the assets.