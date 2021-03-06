# MTK-Tools by Bruno Martins
## MTK unpack and repack scripts

If you are looking for a way to easily unpack / repack boot.img, recovery.img or logo.bin from your MediaTek device, don't look any further. Here you can find my own Perl scripts.

Scripts were first based on the ones available on [Android-DLS WiKi](http://android-dls.com/wiki/index.php?title=HOWTO:_Unpack%2C_Edit%2C_and_Re-Pack_Boot_Images), but are now highly modified in order to work with specific MTK boot and recovery images. The scripts fully work with every image from all known MediaTek SoC:
- MT6516
- MT65x3 (MT6513 and MT6573)
- MT65x5 (MT6515 and MT6575)
- MT6577
- MT65x2 (MT6572, MT6582 and MT6592)
- MT6589
- MT83xx (MT8377 and MT8389)
- MT6595

#### Unpack script usage:

	Usage: unpack-MTK.pl <infile> [COMMAND ...]
	  Unpacks boot, recovery or logo image
	
	Optional COMMANDs are:
	
	  -info_only
	    Display boot or recovery image information only
	     (useful to check image information without unpacking)
	
	  -kernel_only
	    Extract kernel only from boot or recovery image
	
	  -ramdisk_only
	    Extract ramdisk only from boot or recovery image
	
	  -force_logo_res <width> <height>
	    Forces logo image file to be unpacked by specifying image resolution,
	    which must be entered in pixels
	     (only useful when no zlib compressed images are found)
	
	  -invert_logo_res
	    Invert image resolution (width <-> height)
	     (may be useful when extracted images appear to be broken)

- Note: for the new platforms requirements, the unpack script will now display the complete information about input image (example shown bellow) and also create an extra file with arguments needed for further repacking.
```
Input file information (example):

 Header:

  Boot magic:                   ANDROID!
  Kernel size (bytes):          3436480         (0x00346fc0)
  Kernel load address:          0x10008000

  Ramdisk size (bytes):         1989254         (0x001e5a86)
  Ramdisk load address:         0x11000000
  Second stage size (bytes):    0               (0x00000000)
  Second stage load address:    0x10f00000

  Tags address:                 0x10000100
  Page size (bytes):            2048            (0x00000800)
  ASCIIZ product name:          ''
  Command line:                 ''
  ID:                           727cb3e6a37d7973d94f5061a4fb6169a8c4da77

 Other:

  Boot magic offset:            0x00000000
  Base address:                 0x10000000

  Kernel offset:                0x00008000
  Ramdisk offset:               0x01000000
  Second stage offset:          0x00f00000
  Tags offset:                  0x00000100
```

#### Repack script usage:

	Usage: repack-MTK.pl <COMMAND ...> <outfile>
	
	COMMANDs are:
	
	  -boot [--more_verbose] <kernel> <ramdisk-directory>
	    Repacks boot image
	
	  -recovery [--more_verbose] <kernel> <ramdisk-directory>
	    Repacks recovery image
	
	  -logo [--no_compression] <logo-directory>
	    Repacks logo image

- Note: for the new platforms requirements, repack script now takes into account the file (created when unpacking) containing extra arguments. More information about the built image is now also displayed (example shown bellow).
```
Build information (example):

 Base address and offsets:

  Base address:                 0x10000000
  Kernel offset:                0x00008000
  Ramdisk offset:               0x01000000
  Second stage offset:          0x00f00000
  Tags offset:                  0x00000100

 Other:

  Page size (bytes):            2048
  ASCIIZ product name:          ''
  Command line:                 ''
```

#### Credits:

- **Android-DLS** for the initial scripts
- **starix** (from forum.china-iphone.ru) for the decryption of logo.bin files structure
- **carliv** (from forum.xda-developers.com) for new platform support and new binaries

#### Support page:

Visit the [support page](http://forum.xda-developers.com/showthread.php?t=1587411) for any questions or comments. Please don't just leech the files and go away. You can easily say thanks just by pressing "Thanks" button on XDA-Developers forum.

#### Copyright:

Copyright (C) 2012 Bruno Martins (bgcngm@XDA)

You may not distribute nor sell this software or parts of it in Source, Object nor in any other form without explicit permission obtained from the original author.
