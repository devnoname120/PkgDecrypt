# PkgDecrypt
Decrypts and extracts PS Vita PKG files.

# Dependencies
* zlib

# Features
* 1:1 file extraction,
* Support for klicensee and zRIF keys for work.bin 1:1 recreation,
* Can either extract PKG or decrypt it into PKGS file,
* Different output hierarchies can be chosen for easy transfer to VITA.

# Usage
```
pkg_dec [--make-dirs=id|ux] [--license=<key>] [--raw] filename.pkg [output_directory]
	--make-dirs=id|ux	Use output directory to create special hierarchy,
				id	places all output in the <CONTENTID> folder
				ux	places all output in ux0-style hierarchy
	--license=<key>		Provide key to use as base for work.bin (*.rif) file creation.
				Two formats accepted - klicensee key (deprecated) and zRIF (recommended)
				zRIF could be made by NoNpDrm fake RIFs using make_key
	--raw			Output fully decrypted PKG instead of unpacking it, exclusive
	<filename.pkg>		Input PKG file
	<output_directory>	Directory where all files will be places. Current directory by default.
```


# Requirements
* Windows x64(for precompiled build) or other supported OS,
* a)Vita with 3.60 henkaku, PKG file and license key[klicensee(deprecated) or zRIF(recommended)] for Vita installation,
* b)PKG file for extraction purposes only.

# Changelog:
### 1.1.0.0
New features:
- Support of generating fake RIFs from hex-encoded klicensee and zRIFs
- Unpacking files using ux0 hierarchy emulation
- Automatic recognition of DLC and GD packages (using pkg_info fields)
- make_key program to pack fake RIFs into zRIF format

Major refactoring of code:
- Split code over few modules, for example, key encoding and decoding done using keyflate.c
- Few utility functions (mkdirs and set of pkg_* functions mirroring stdio with transparent decryption)
- Improved code readability with structs defining various structures in pkg file

Bugfixes:
- Generated head.bin now have proper file size,
- Attempted to fix sku_flag value using drm_type of package (different solution from temp.bin),
- Other bugfixes.
### 1.0.0.3
* Added full support for license keys, now if you use license key it will generate fully working work.bin file,
* Added check for license, if license is not used, file work.bin will not be generated at all,
* All *.bin files are now generated in proper location `output_folder/sce_sys/packages/*.bin`
### 1.0.0.2
* Fixed Windows extraction, now it extract 1:1 files.
### 1.0.0.1
* St4rk's support for *.bin files
### 1.0.0.0
* St4rk Initial code

# ToDo list:
* Fix DLC extraction, 

# Thanks
St4rkDev for his wonderful code,

TheRadziu for PR, team management and testing,

Atrexia for supporting us with this idea, 

FatalErrorX for providing me with all files necessary for debug and PoC testing,

Brandonheat8 for the icon.
