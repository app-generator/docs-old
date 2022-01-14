---
description: Learn how to install WSL (Windows Subsystem for Linux) using the terminal
---

# Install WSL

The Windows Subsystem for Linux lets developers run a GNU/Linux environment directly on Windows. The latest version is WSL 2, which powers the Windows Subsystem for Linux to run ELF64 Linux binaries on Windows.&#x20;

> List available WSL distros

```bash
$ wsl -l -o

NAME            FRIENDLY NAME
Ubuntu          Ubuntu
Debian          Debian GNU/Linux
kali-linux      Kali Linux Rolling
openSUSE-42     openSUSE Leap 42
SLES-12         SUSE Linux Enterprise Server v12
Ubuntu-16.04    Ubuntu 16.04 LTS
Ubuntu-18.04    Ubuntu 18.04 LTS
Ubuntu-20.04    Ubuntu 20.04 LTS
```

> Install WSL via `powershell`

Below command installs Ubuntu distribution.&#x20;

```bash
$ wsl --install Ubuntu
```

> Check Current WSL Version

```bash
$ wsl -l -v
```

> Update from **WSL 1** to **WSL 2**

```bash
$ wsl --set-version Ubuntu 2
```



For more information, feel free to access:&#x20;

* [WSL Documentation](https://docs.microsoft.com/en-us/windows/wsl/)
* [WSL basic commands](https://docs.microsoft.com/en-us/windows/wsl/basic-commands)&#x20;
