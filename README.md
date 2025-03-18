# Umvirt Linux From Scratch packages database

Version:  0.2 

Based on: Linux From Scratch 12.0 (September 2023)

Status: Archived. Almost stable. 

## About

This database is contain information which needed by Umvirt Packages service to download, extract, configure, build and install source code packages and their dependencies.

## License

This database is licensed under GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007

Source packages license information can be found on source packages files and their official sites.

## Installation or update

- Go to ULFS Packages directory

- Copy contents of this directory in tmp/0.2 directory

- Go to bin directory in ULFS Packages directory

- Import this database by running

        ./load_data --path=../tmp/0.2 --release=0.2 --format=xml

## Edit

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
- nVidia
- QEMU VGA
- QEMU QXL

### Build system requirements

CPU:

- qemu64 - for common CPUs builds
- amd64 - for specific CPUs builds

Memory: Some packages are need 2GB per CPU core or more. If you don't have enough memory, you have to reduce CPU cores quantity.

### Features

-  QEMU with SPICE support

### Differences with BLFS

Modified packages
- libxml2 - used old version
- xmlto - skip validation to work offline

Additional packages
- MATE
- SPICE
