# UefiSeven
## Summary
Special version only for set GOP resolution before use CSMWrap for use Windows 7 or WinXP 32-bit and Longhorn winload.exe 5472.5

## Usage instructions
Run from UEFI Shell on FAT32 HDD or USB stick

## Settings
Settings can be applied by placing u7.ini file in the directory containing the main efi file. Use verbose enabled and 1024x768 or native monitor resolution:
```
verbose=1         ; enable verbose mode
resheight=1024    ; preferred height
reswidth=768      ; preferred width
```

## Build instructions (Tested with edk2-stable202108)
```
wget https://github.com/tianocore/edk2/releases/download/edk2-stable202108/edk2-edk2-stable202108.zip
wget https://github.com/tianocore/edk2/releases/download/edk2-stable202108/submodule-BaseTools-Source-C-BrotliCompress-brotli.zip
wget https://github.com/tianocore/edk2/releases/download/edk2-stable202108/submodule-MdeModulePkg-Library-BrotliCustomDecompressLib-brotli.zip
7z x edk2-edk2-stable202108.zip
mv edk2-edk2-stable202108 MyWorkspace
7z x -oMyWorkspace submodule-BaseTools-Source-C-BrotliCompress-brotli.zip
7z x -oMyWorkspace submodule-MdeModulePkg-Library-BrotliCustomDecompressLib-brotli.zip
7z x -yoMyWorkspace uefiseven-1.31-1.zip
cd MyWorkspace
make -C BaseTools
. edksetup.sh
build -a X64 -t GCC49 -b RELEASE -p UefiSevenPkg/UefiSevenPkg.dsc --conf=UefiSevenPkg/Conf
```
