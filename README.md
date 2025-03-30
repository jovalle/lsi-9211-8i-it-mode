# lsi-9211-8i-it-mode
Repository that includes the EFI shell and firmware to flash a LSI 9211 8i HBA card to IT mode

## Contents
`/EFI/BOOT/BOOTX64.efi` - EFI Shell
`/2118it.bin` - Firmware v20 IT mode
`/mptsas2.rom` - Firmware ROM file
`/sas2flash.efi` - Flashing Utility

## Preparation

Wipe a flash drive with a tool like Rufus. Non-bootable, GPT, BIOS/UEFI, FAT32. 

Copy contents of this repo to root dir.

## Flashing

Boot into the UEFI partition of the drive. Once you have a UEFI shell, navigate to the flash drive's filesystem, clear the existing firmware and install anew with IT mode.

```dos
map
fs0:
ls
sas2flash.efi -listall
sas2flash.efi -o -e 6
sas2flash.efi -o -f 2118it.bin -b mptsas2.rom
sas2flash.efi -listall
```
