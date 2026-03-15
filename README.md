# HybridVectorSearch
---
## Requirements

### All Platforms

* **Git**
* **CMake ≥ 3.21**
* **Ninja**
* **C++20 compiler**

---

### macOS

Install required tools:

```bash
brew install cmake ninja
xcode-select --install
```

---

### Ubuntu

Install required tools:

```bash
sudo apt update
sudo apt install -y \
  build-essential \
  cmake \
  ninja-build \
  curl \
  zip \
  unzip \
  tar \
  pkg-config
```

---

### Windows

Install:

* **Visual Studio Build Tools / Visual Studio Community**
* Select **Desktop Development with C++**
* Ensure **MSVC compiler** is installed

Also install:

* Git
* CMake
* Ninja

---

# Clone the Repository

Because the project uses **vcpkg as a submodule**, clone with submodules:

```bash
git clone --recurse-submodules https://github.com/<your-username>/HybridVectorSearch.git
cd HybridVectorSearch
```

If you forgot `--recurse-submodules`:

```bash
git submodule update --init --recursive
```

---

# Bootstrap vcpkg

### macOS / Ubuntu

```bash
./vcpkg/bootstrap-vcpkg.sh
```

### Windows

```powershell
.\vcpkg\bootstrap-vcpkg.bat
```

This installs the `vcpkg` executable used by CMake.

---

# Build the Project

The project uses **CMake Presets** for deterministic builds.

---

## macOS / Ubuntu

Configure:

```bash
cmake --preset default
```

Build:

```bash
cmake --build --preset default
```

Run:

```bash
./build/default/HybridVectorSearch
```

---

## Windows (MSVC)

Configure:

```powershell
cmake --preset windows-msvc
```

Build:

```powershell
cmake --build --preset windows-msvc
```

Run:

```powershell
.\build\default\HybridVectorSearch.exe
```

---

# Project Structure

```
HybridVectorSearch
│
├── CMakeLists.txt
├── CMakePresets.json
├── vcpkg.json
│
├── src/
│   └── main.cpp
│
├── include/
│
├── tests/
│
├── scripts/
│   ├── setup-macos.sh
│   ├── setup-ubuntu.sh
│   └── setup-windows.ps1
│
├── vcpkg/                 # dependency manager (submodule)
│
└── .github/workflows/
    └── ci.yml             # cross-platform CI
```

---

# Continuous Integration

Every push and pull request triggers builds on:

* **Ubuntu**
* **macOS**
* **Windows**

CI validates that:

* dependencies install correctly
* the project configures successfully
* the project builds without errors

---

# Development Workflow

Typical workflow:

```bash
git clone --recurse-submodules <repo>
cd HybridVectorSearch

./vcpkg/bootstrap-vcpkg.sh
cmake --preset default
cmake --build --preset default
```

---

# Adding Dependencies

Dependencies are declared in:

```
vcpkg.json
```

Example:

```json
{
  "dependencies": [
    "fmt"
  ]
}
```

After editing `vcpkg.json`, simply re-run:

```bash
cmake --preset default
```

vcpkg will automatically install new packages.


---