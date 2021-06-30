# get-binutils

This is a simple bash script that downloads, builds, and retrieves useful gnu mips64-elf tools used in N64 decompilation projects. This is useful for platforms like ARM, where mips64 binutil packages are not avaliable.  

By default this script will get `as`, `ar`, `ld`, `objcopy`, and `objdump`. If you want to add any more programs, then you just need to edit the lines after `PRINT_STEP 5`. Note that some files get built as `<program>-new` for some reason, so you'll need to use the`RENAME_AND_INSTALL_FILE` macro instead of the `INSTALL_FILE` macro in that case.  

The default output folder is called `/binutils/` and will appear in the same folder as the script, and all the programs will have the prefix `mips64-elf-`. You can modify these settings at the top of the script.

## Dependencies

* `wget` for downloading the binutils source code
* `tar` for extracting the downloaded `.tar.xz` file.
* `make` to build the source code

## Performance

This script shouldn't be too slow on modern x86 computers. It does take advantage of all the computer's threads during the build phase. The Raspberry Pi 3 ended up taking over 10 minutes to complete, whereas my Ryzen 3600 system took less than a minute. Not sure if RAM speeds and/or capacities matter at all.

Here are some references based off the systems I use:

* Ryzen 3600 (with 16GB DDR4 3200 RAM)
    * 47 seconds
* Intel Core i5-8250U (with 8GB LPDDR4 2400 RAM)
    * 1 minute, 30 seconds
* Raspberry Pi 3 Model B (with 1GB LPDDR2 900 RAM)
    * 10 minutes, 45 seconds

