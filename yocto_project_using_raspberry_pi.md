
# YOCTO PROJECT USING RASPBERRY PI

---

## RECIPE

A recipe is a set of instructions that tells BitBake how to build the software.  
A file with `.bb` extension in Yocto is called a **BitBake recipe**.

### RECIPE DESCRIBES:
- **WHAT TO BUILD**: Name and version of software to build.  
  Example: `busybox`
- **LOCATION OF SOURCE CODE**: From a URL, Git repository, etc.

---

## TASK FUNCTIONS

These are the functions that perform specific steps in the build process:

- `do_fetch`: Downloads source code from its source.
- `do_unpack`: Unpacks the source code into a temporary folder for building.
- `do_patch`: Applies patches (modifications) to the source code.
- `do_configure`: Prepares the code for building using tools like `./configure` and `make`.  
  Sets up build files (e.g., Makefile), environment paths, and enables/disables features.
- `do_compile`: Converts the source code into binary using cross compilers like `make` or `cmake`.
- `do_install`: Installs compiled binaries, libraries, configuration files, etc. into a temporary directory (`${D}`).
- `do_package`: Splits installed files into different packages such as `.rpm`, `.deb`.

#### Package Types:
- `.rpm`: Red Hat Package Manager – used on RPM-based Linux distributions.
- `.deb`: Debian package – used on Debian-based Linux distributions.

---

## DEPENDENCIES

Dependencies are components that software needs to work correctly in Yocto.

1. **Build Time Dependency**  
   Needed while building the software. Examples: compilers, header files, build tools.

2. **Runtime Dependency**  
   Needed while running the software. Examples: shared libraries, shells, external commands.

---

## LICENSE INFO

Provides details about:
- Type of license (MIT, GPLv2, etc.)
- Path of license file

---

## .bbappend FILE

- Extension of a recipe (BitBake append file)
- Used to modify or customize the `.bb` file without rewriting it
- Common uses: adding patches, changing build/configure/install steps, modifying variables

---

## CLASSES

A **class** is a reusable `.bbclass` file that contains common code (functions, variables, tasks).

- Shared by multiple recipes
- Example usage: `inherit <class name>`
- Common classes: `image.bbclass`, `kernel.bbclass`

### Tasks: 
Compilation, installation, etc.  
### Variables:
Examples: `EXTRA_OECONF`, `CFLAGS`

---

## LAYERS

A **Layer** is a collection of metadata such as:
- Recipes
- Configuration files
- Classes
- Machine definitions
- Images

### Configuration File:
Contains variables/settings used by the build system. Describes:
- What to build
- How to build
- Which settings to apply

### Class in Yocto:
Reusable `.bbclass` file with shared build logic.

### Recipe Usage:
To reuse class logic: `inherit <class name>`

---

## MACHINE

A **Machine** is a specific hardware board for which Linux is being built.  
Examples: Raspberry Pi, BeagleBone

---

## IMAGE

Final output of the Yocto build system – a bootable Linux OS for the device.

---

## LAYER NAMING

Each layer starts with prefix `meta-`, followed by its name.  
Example: `meta-raspberrypi`

---

## TYPES OF LAYERS IN YOCTO

1. **Core Layer**  
   - Provides essential build infrastructure and base recipes  
   - Includes core utilities, BitBake classes, toolchains  
   - Example: `meta`, `openembedded-core`

2. **BSP Layer**  
   - Supports specific hardware or SoC (e.g., Raspberry Pi, BeagleBone)  
   - Includes kernel, bootloader, device tree, firmware  
   - Example: `meta-raspberrypi`, `meta-intel`

3. **Distro Layer**  
   - Defines distribution behavior: build rules and configurations  
   - Includes preferred versions, package types, distro features  
   - Example: `meta-poky`

4. **Application Layer**  
   - Adds general/domain-specific packages  
   - Includes user-space tools, libraries, utilities  
   - Example: `meta-openembedded`, `meta-python`

5. **UI/Feature Layer**  
   - Adds UI-related or graphical functionality  
   - Includes multimedia, Qt, UI frameworks  
   - Example: `meta-qt5`, `meta-gnome`, `meta-xfce`

6. **Tool/Dev Layer**  
   - Adds SDK, debugging, and development tools  
   - Example: `meta-devtools`, `meta-sdk`

7. **Custom Layer**  
   - Contains project-specific recipes, patches, and configurations  
   - Includes custom applications and modified packages  
   - Example: `meta-customer`

---
