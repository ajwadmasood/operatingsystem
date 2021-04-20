# 64-bit Operating System from scratch

## Prerequisites
- A text editor such as VS Code.
- Docker for creating our build-environment.
- Qemu for emulating our operating system.
  -Remember to add Qemu to the path so that you can access it from your command-line. (Windows instructions here)
  
## Setup

Build an image for our build-environment:

- __docker build buildenv -t myos-buildenv__

Build
-------------------------------------------------------------------------------
Enter build environment:

- Linux or MacOS: docker run --rm -it -v "$pwd":/root/env myos-buildenv
- Windows (CMD): docker run --rm -it -v "%cd%":/root/env myos-buildenv
- Windows (PowerShell): docker run --rm -it -v "${pwd}:/root/env" myos-buildenv
- NOTE: If you are having trouble with an unshared drive, ensure your docker daemon has access to the drive you're development environment is in. For Docker Desktop, this is in "Settings > Shared Drives" or "Settings > Resources > File Sharing".

Build for x86 (other architectures may come in the future):

- __make build-x86_64__

To leave the build environment, enter __exit__.

Emulate
-------------------------------------------------------------------------------
You can emulate your operating system using Qemu: (Don't forget to add qemu to your path!)

- __qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso_
- NOTE: When building your operating system, if changes to your code fail to compile, ensure your QEMU emulator has been closed, as this will block writing to kernel.iso.
Alternatively, you should be able to load the operating system on a USB drive and boot into it when you turn on your computer. (I haven't actually tested this yet.)

Cleanup
-------------------------------------------------------------------------------
Remove the build-evironment image:

- __docker rmi myos-buildenv -f__

Website
-------------------------------------------------------------------------------
[https://ajwadmasood.github.io/ajwadcoa/](https://ajwadmasood.github.io/ajwadcoa/)
