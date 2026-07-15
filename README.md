# Paranoid Android - Marble Kernel

## Setting up your machine ##

You must be running a 64-bit Linux distribution and must have installed some packages to build
Paranoid Android. Google recommends using [Ubuntu](http://www.ubuntu.com/download/desktop) for
this and provides instructions for setting up the system (with Ubuntu-specific commands) on
[the Android Open Source Project website](https://source.android.com/source/initializing.html#setting-up-a-linux-build-environment).

Once you have set up your machine according to the instructions by Google, return here and carry
on with the rest of the instructions.

## Grabbing the source ##

[Repo](http://source.android.com/source/developing.html) is a tool provided by Google that
simplifies using [Git](http://git-scm.com/book) in the context of the Android source.

### Installing Repo ###

```bash
# Make a directory where Repo will be stored and add it to the path
$ mkdir ~/.bin
$PATH=~/.bin:$PATH

# Download Repo itself
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo

# Make Repo executable
$ chmod a+x ~/.bin/repo

```

### Initializing Repo

```bash
# Create a directory for the source files
# You can name this directory however you want, just remember to replace
# WORKSPACE with your directory for the rest of this guide.
# This can be located anywhere (as long as the fs is case-sensitive)
$mkdir WORKSPACE$ cd WORKSPACE

# Install Repo in the created directory
$ repo init -u https://github.com/aospa-shadedark/kernel_manifest -b beryl-xiaomi-sm8450

```

### Downloading the source tree

This is what you will run each time you want to pull in upstream changes. Keep in mind that on your
first run, it is expected to take a while as it will download all the required Android source files
and their change histories.

```bash
# Let Repo take care of all the hard work
#
# The -j# option specifies the number of concurrent download threads to run.
# 8 threads is a good number for most internet connections.
# You may need to adjust this value if you have a particularly slow connection.
$ repo sync --no-tags --no-clone-bundle --current-branch -j8

```

## Building

```bash
# Go to the root of the source tree...
$ cd WORKSPACE
# ...and run the builder tool.
$ ./build.sh

# Optional arguments:
# -f : Full LTO (longer build time, generates slightly more optimized kernel image)
# -c : Clean build (remove leftover from previous builds)

```

---

## Upstream & Base Sources

This is an **OSS** kernel configuration based directly on the following [LineageOS](https://github.com/LineageOS) upstream trees for the Snapdragon 8 Gen 1 (SM8450) platform:

* **Kernel Source:** [LineageOS/android_kernel_xiaomi_sm8450](https://github.com/LineageOS/android_kernel_xiaomi_sm8450)
* **Kernel Modules:** [LineageOS/android_kernel_xiaomi_sm8450-modules](https://github.com/LineageOS/android_kernel_xiaomi_sm8450-modules)
* **Kernel Device Trees:** [LineageOS/android_kernel_xiaomi_sm8450-devicetrees](https://github.com/LineageOS/android_kernel_xiaomi_sm8450-devicetrees)

## Credits

* **[Adithya R](https://github.com/adithya2306)**
* **[The LineageOS Team](https://github.com/LineageOS)**
