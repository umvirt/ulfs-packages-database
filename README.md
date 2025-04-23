# Umvirt Linux From Scratch packages database

Version:  0.2.3 

Based on: Linux From Scratch 12.3 (March 2025)

Status: Under development. Some packages are broken or missing.

## About

This database is contain information which needed by Umvirt Packages service to download, extract, configure, build and install source code packages and their dependencies.

## License

This database is licensed under GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007

Source packages license information can be found on source packages files and their official sites.

## Installation or update

### Database

- Go to ULFS Packages directory

- Copy contents of this directory in tmp/0.2.3 directory

- Go to bin directory in ULFS Packages directory

- Import this database by running

        ./load_data --path=../tmp/0.2.3 --release=0.2.3 --format=xml

### Files

- Download source package files. 
    - To download release specific files with wget go to temporary directory and run: 

            wget -x -i http://%repository_name%/linux/packages/files/0.2.3/wget

    - then copy files to storage directory with path "0.2.3/packages".

- Download source package patches. 
    - To download release specific patches with wget go to temporary directory and run: 

            wget -x -i http://%repository_name%/linux/packages/patches/0.2.3/wget

    - then copy patches to storage directory with path "0.2.3/patches".

- Scan files and add it to database

        ./scan_files

- Scan patches and add it to database

        ./scan_patches

- Update database links to files

        ./updatelinks2files

## Editing

To edit this database to meet your needs you can use:

- ULFS module in Umvirt YAPS CMS
- phpMyAdmin [https://www.phpmyadmin.net/](https://www.phpmyadmin.net/)
- console mySQL/MariaDB client application

## Additional release information

### Target system requirements

Supported CPU architectures:

- amd64
- i686

Supported GPUs:

- AMD
- QEMU VGA
- QEMU QXL

### Build system requirements

CPU:

- qemu64 - for common CPUs builds
- amd64 - for specific CPUs builds

Memory: Some packages are need 3GB per CPU core or more. If you don't have enough memory, you have to reduce CPU cores quantity.

### Features

- amdgpu_virtio support in MESA
- Spice protocol support in QEMU

### Differences with BLFS

- glib - Splited in 2 packages: glib & glib-gobject
- xmlto - Skip validation to work offline
- 7zip - Modified "for" loop in install script
- mesa 
    - New version to support amdgpu_virtio. 
    - Drivers which need rust compiler is disabled (nouveau)
- samba - Modified to offline build
- poppler-app - Disable qt support
- doxygen - Disable qt support
- gimp - New release against rc1. + rustless patches
- babl - New release to build gimp
- gegl - New release to build gimp
- network-manager-applet - obsolete. new version
- libreoffice 
    - build offline
    - build without java and gstreamer
- sane-backends - New version 1.3.1

### Additional packages not mentioned in BLFS

#### Emulation

- Bochs
- DosBoxes
- PCE
- PCEM
- Simh
- Fuse
- Spectemu
- Fceux

#### Software

- Audacity
- Blender
- Wine
- Shotcut
- OBS
- LibreCAD
- Libvirt
- Virt-Manager

#### Games

- Abuse 
- Glest
- GzDoom
- Extreme Tux Racer

### Known bugs

- OBS package is broke Mesa. Some OpenGL software and games are start refuse to work properly.
- Aufs Linux kerel patch which used by default and allows to make Live CD/DVD/USB is broke NFSv4: [https://aufs.sourceforge.net/](https://aufs.sourceforge.net/).