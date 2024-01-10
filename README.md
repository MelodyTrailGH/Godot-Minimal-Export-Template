# Godot Minimal Export Templates

A grouping of the smallest export templates possible in Godot.

**PLEASE READ THIS!**

```txt
Due to the fact that these export templates are very small.
THERE will be A LOT OF FEATURES MISSING!

Edit the template build profile below to edit it for your needs.
```

## Guide

**Getting the source code:**

Via git: (*Remember to edit the \<directory\> placeholder!*)

```bash
git clone https://github.com/godotengine/godot.git --branch 3.5.3-stable <directory> --recursive
```

**Building Profile:**

```py
optimize = "size"
use_lto =" yes"
tools = "no"
disable_3d = "yes"
module_arkit_enabled = "no"
module_assimp_enabled = "no"
module_bmp_enabled = "no"
module_bullet_enabled = "no"
module_camera_enabled = "no"
module_csg_enabled = "no"
module_dds_enabled = "no"
module_enet_enabled = "no"
module_etc_enabled = "no"
module_gdnative_enabled = "no"
module_gridmap_enabled = "no"
module_hdr_enabled = "no"
module_jsonrpc_enabled = "no"
module_mbedtls_enabled = "no"
module_mobile_vr_enabled = "no"
module_opensimplex_enabled = "no"
module_opus_enabled = "no"
module_pvr_enabled = "no"
module_recast_enabled = "no"
module_regex_enabled = "no"
module_squish_enabled = "no"
module_svg_enabled = "no"
module_tga_enabled = "no"
module_theora_enabled = "no"
module_tinyexr_enabled = "no"
module_upnp_enabled = "no"
module_vhacd_enabled = "no"
module_vorbis_enabled = "no"
module_webm_enabled = "no"
module_webrtc_enabled = "no"
module_websocket_enabled = "no"
module_xatlas_unwrap_enabled = "no"
```

**It's suggested to put this in a file called `custom.py`.**

### Building for Linux/\*BSD

**Quick Warning!**

```txt
Linux binaries usually won't run on distributions that are older than the distribution they were built on (due to glibc version compatibilities.) 
If you wish to distribute binaries that work on most distributions, you should build them on an old distribution such as Ubuntu 16.04 for example.
You can use a virtual machine or a container to set up a suitable build environment (which is shown in this guide.)
```

#### Building locally

##### Required tools (Building locally)

* [GNU GCC](https://gcc.gnu.org) 7.x or newer or [LLVM Clang](https://gcc.gnu.org) 6.x or newer.
* [CPython](https://python.org) 3.5.x or newer.
* [Scons](https://scons.org) 3.0 or newer.
* [pkg-config](https://www.freedesktop.org/wiki/Software/pkg-config) *(This should be included with your Linux distro.)*
* [X11](https://www.x.org) development libraries and tools. *(This should be included with your Desktop Environment.)*
* [MesaGL](https://www.mesa3d.org) development libraries.
* [ALSA](https://www.alsa-project.org) development libraries.
* [PulseAudio](https://www.freedesktop.org/wiki/Software/PulseAudio) development libraries.

**Distro specific single-liners:**  
Here are a couple of single-liners to automatically install the tools and dependencies needed.  
*Ordered from A to Z*  

###### Alpine Linux

```sh
apk add scons pkgconf gcc g++ libx11-dev libxcursor-dev libxinerama-dev libxi-dev libxrandr-dev mesa-dev libexecinfo-dev eudev-dev alsa-lib-dev pulseaudio-dev
```

###### Arch Linux

```sh
pacman -S --needed scons pkgconf gcc libxcursor libxinerama libxi libxrandr mesa glu libglvnd alsa-lib pulseaudio yasm
```

###### Debian-based

```sh
sudo apt-get install build-essential scons pkg-config libx11-dev libxcursor-dev libxinerama-dev libgl1-mesa-dev libglu-dev libasound2-dev libpulse-dev libudev-dev libxi-dev libxrandr-dev yasm
```

###### Fedora Linux

```sh
sudo dnf install scons pkgconfig libX11-devel libXcursor-devel libXrandr-devel libXinerama-devel libXi-devel mesa-libGL-devel mesa-libGLU-devel alsa-lib-devel pulseaudio-libs-devel libudev-devel yasm gcc-c++ libstdc++-static libatomic-static
```

###### FreeBSD

```sh
sudo pkg install py37-scons pkgconf xorg-libraries libXcursor libXrandr libXi xorgproto libGLU alsa-lib pulseaudio yasm
```

###### Gentoo Linux

```sh
emerge -an dev-util/scons x11-libs/libX11 x11-libs/libXcursor x11-libs/libXinerama x11-libs/libXi media-libs/mesa media-libs/glu media-libs/alsa-lib media-sound/pulseaudio dev-lang/yasm
```

###### Mageia Linux

```sh
urpmi scons task-c++-devel pkgconfig "pkgconfig(alsa)" "pkgconfig(glu)" "pkgconfig(libpulse)" "pkgconfig(udev)" "pkgconfig(x11)" "pkgconfig(xcursor)" "pkgconfig(xinerama)" "pkgconfig(xi)" "pkgconfig(xrandr)" yasm
```

###### OpenBSD

```sh
pkg_add python scons llvm yasm
```

###### openSUSE

```sh
sudo zypper install scons pkgconfig libX11-devel libXcursor-devel libXrandr-devel libXinerama-devel libXi-devel Mesa-libGL-devel alsa-devel libpulse-devel libudev-devel libGLU1 yasm
```

###### NetBSD

```sh
pkg_add pkg-config py37-scons yasm pulseaudio
```

###### Solus

```sh
sudo eopkg install -c system.devel scons libxcursor-devel libxinerama-devel libxi-devel libxrandr-devel mesalib-devel libglu alsa-lib-devel pulseaudio-devel yasm
```

###### Compiling (Building locally)

**Remember to use the profile above before building!**

With this one-liner you can build both debug and release export templates in one go.  
*(Make sure to have the GNU GCC Multilib installed!)*

```sh
\
scons platform=x11 target=release bits=64 profile=custom.py && \
scons platform=x11 target=release_debug bits=64 profile=custom.py && \
scons platform=x11 target=release bits=32 profile=custom.py && \
scons platform=x11 target=release_debug bits=32 profile=custom.py
```

(Single Line)

```sh
scons platform=x11 target=release bits=64 profile=custom.py && scons platform=x11 target=release_debug bits=64 profile=custom.py && scons platform=x11 target=release bits=32 profile=custom.py && scons platform=x11 target=release_debug bits=32 profile=custom.py
```

#### Building in an Ubuntu container

##### Required tools (Building in a container)

* [Docker](https://www.docker.com)

**Notice!**

```txt
This part of the guide was designed for root-less docker in mind.
If you have a standard Docker installation, remember to add "sudo" to the beginning of the docker commands.
(Ignore this if you're a root/wheel user.)
```

**Creating the container:**

This one-liner should get you into a Ubuntu 16.04 interactive container.
*(Remove the sudo placeholder if you're using rootless docker.)*

```sh
docker pull ubuntu:18.04 && \
docker run -it --name godot-linux-build f9a80a55f492
```

```sh
docker pull ubuntu:18.04 && docker run -it --name godot-linux-build f9a80a55f492
```

Now that you're in the container, you're going to need to manually build the tools required  
since this version of Ubuntu is EOL and modern packages aren't supported.  

First update the `apt` mirrors.

```sh
apt-get update
```

Now we can install all the required packages

```sh
apt-get install -y \
python3 \
python3-venv \
python3-pip \
build-essential \
gcc-multilib \
pkg-config \
libx11-dev \
libxcursor-dev \
libxinerama-dev \
libgl1-mesa-dev \
libglu-dev \
libasound2-dev \
libpulse-dev \
libudev-dev \
libxi-dev \
libxrandr-dev \
yasm \
libssl-dev \
software-properties-common
```

or

```sh
apt-get install -y python3 python3-venv python3-pip build-essential gcc-multilib pkg-config libx11-dev libxcursor-dev libxinerama-dev libgl1-mesa-dev libglu-dev libasound2-dev libpulse-dev libudev-dev libxi-dev libxrandr-dev  yasm libssl-dev software-properties-common
```

We also need the 32-bit versions as well:

*Run this command first to add 32-bit support to apt.*

```sh
dpkg --add-architecture i386 && apt-get update && apt-get -y install multiarch-support:i386
```

then run

```sh
apt-get install -y \
libx11-dev:i386 \
libxcursor-dev:i386 \
libxinerama-dev:i386 \
libgl1-mesa-dev:i386 \
libglu-dev:i386 \
libasound2-dev:i386 \
libpulse-dev:i386 \
libudev-dev:i386 \
libxi-dev:i386 \
libxrandr-dev:i386
```

or

```sh
apt-get install -y libx11-dev:i386 libxcursor-dev:i386 libxinerama-dev:i386 libgl1-mesa-dev:i386 libglu-dev:i386 libasound2-dev:i386 libpulse-dev:i386 libudev-dev:i386 libxi-dev:i386 libxrandr-dev:i386
```

Now with all of the local packages installed now time to get some from pip too.  

First create a virtual environment.  

```sh
python3 -m venv .venv && source .venv/bin/activate
```

Now we can install some pip packages.

```sh
pip install SCons==3.1.2
```

###### Compiling (Building in a container)

**Remember to use the profile above before building!**

With this one-liner you can build both debug and release export templates in one go.  

```sh
\
scons platform=x11 target=release bits=64 profile=custom.py && \
scons platform=x11 target=release_debug bits=64  profile=custom.py && \
scons platform=x11 target=release bits=32  profile=custom.py && \
scons platform=x11 target=release_debug bits=32  profile=custom.py
```

(Single Line)

```sh
scons platform=x11 target=release bits=64  profile=custom.py && scons platform=x11 target=release_debug bits=64  profile=custom.py && scons platform=x11 target=release bits=32  profile=custom.py && scons platform=x11 target=release_debug bits=32  profile=custom.py
```
