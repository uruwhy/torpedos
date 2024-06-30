# Red Development Cheatsheet

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
