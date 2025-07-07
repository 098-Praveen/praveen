
# YOCTO PROJECT USING RASPBERRY PI

## RECIPE

A **recipe** is a set of instructions that tells BitBake how to build the software.  
A file with `.bb` extension in Yocto is called a **BitBake recipe**.

### RECIPE DESCRIBES:
- **WHAT TO BUILD**: Name and version of the software to build.  
  *Example*: `busybox`
- **LOCATION OF SOURCE CODE**: From a URL, Git repository, etc.

---

## TASK FUNCTIONS

These are functions that perform specific steps in the build process:

- `do_fetch`:  
  Downloads source code from the location where the source is present.

- `do_unpack`:  
  Unpacks the source code (extracts it into a temporary folder for building).

- `do_patch`:  
  Applies patches (modifies the source code if needed).

- `do_configure`:  
  Prepares the code for building by:
  - Running configuration tools like `./configure`, `make`
  - Generating build files (e.g., Makefile)
  - Setting environment and options (installation paths, feature toggles)
  - Configuring the source code to meet the specifications of the target system (hardware + OS)

- `do_compile`:  
  Converts the source code into binary using cross-compilers like `make`, `cmake`.

- `do_install`:  
  Installs the compiled binaries, libraries, configuration files, etc.,  
  into a temporary directory `${D}`, which is later used to generate packages.

- `do_package`:  
  Takes the files inside the temporary directory and splits them into different packages:

  - `.rpm`: Red Hat Package Manager — for software distribution on RPM-based systems.
  - `.deb`: Debian package — for software distribution on Debian-based systems.

---

## DEPENDENCIES

**Dependency** refers to something the software needs to work correctly.  
In Yocto, there are two types:

1. **Build Time Dependency**:
   - Needed while compiling the software.
   - Requires compilers, header files, and build tools.

2. **Run Time Dependency**:
   - Needed while running the software.
   - Requires shared libraries, shells, and external commands.

---

## LICENSE INFO

Provides:
- Type of license (e.g., MIT, GPLv2)
- Path to the license file

---

## .bbappend File

`.bbappend` is an extension of the recipe file (`.bb`), also called **BitBake append file**.  
It is used to modify or customize the `.bb` file **without rewriting it**.

### Uses:
- Adding patches
- Changing build, configure, or install steps
- Modifying variables like dependencies and paths
