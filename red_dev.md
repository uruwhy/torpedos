# Red Development Cheatsheet

## Dev Box Setup
[Win11 VM from MSFT](https://developer.microsoft.com/en-us/windows/downloads/virtual-machines/)
- [Optional debloat](https://github.com/Raphire/Win11Debloat)
- Note - disable 3d acceleration, otherwise a lot of applications like WinDBG will have their GUIs messed up

Tools to install:
- [git](https://git-scm.com/download/win)
  - Alternatively,
  ```PowerShell
  winget install --id Git.Git -e --source winget
  ```
  - [Generate SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent): `ssh-keygen -t ed25519 -C "your_email@example.com"`
- [Kate text editor](https://www.microsoft.com/store/apps/9NWMW7BB59HW)
- [Windbg](https://aka.ms/windbg/download)
- [x64dbg](https://github.com/x64dbg/x64dbg)
- NASM: `winget install nasm -i`
  - Add to path: `C:\Program Files\NASM`, verify with `nasm --version` 
- msys2: `winget install MSYS2.MSYS2`
- [mingw](https://code.visualstudio.com/docs/cpp/config-mingw):
  - From msys2: `pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain`
  - Add to path: `C:\msys64\ucrt64\bin`
  - Verify with:
  ```cmd
  gcc --version
  g++ --version
  gdb --version
  ```
- [Rust](https://forge.rust-lang.org/infra/other-installation-methods.html)

## PE Format

### IAT
```
dumpbin /imports path\to\executable
```

### Resources
- [A dive into the PE file format](https://0xrick.github.io/win-internals/pe1/)
- [PE Internals Part 1: A few words about Export Address Table](https://ferreirasc.github.io/PE-Export-Address-Table/)
- [Exploring the Export Table](https://dev.to/wireless90/exploring-the-export-table-windows-pe-internals-4l47)

## WinDBG
Install via PowerShell:
```powershell
winget install Microsoft.WinDbg
```

## GitHub Tricks
Push as a different user (using different SSH key):
```
$ GIT_SSH_COMMAND="ssh -i path/to/private/key" git push
```
## Rust
Cross-compile Windows on Linux
```
rustup target add x86_64-pc-windows-gnu
cargo build --target x86_64-pc-windows-gnu
```

## Windows Documentation
- [Data type - typedefs and sizes](https://learn.microsoft.com/en-us/windows/win32/winprog/windows-data-types)
