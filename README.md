# C++ Project Manager

Use **project_manager.py** script to managing C++ project. It manages CMake caching, build, documentation generation, and project execution. It also generates VSCode configuration files.

## Features

- **Cleanup**: Removes build and cache folders.
- **Build**: Runs CMake and Ninja to build the project.
- **Documentation**: Generates documentation using Doxygen.
- **Run**: Executes the built project.
- **Configuration Info**: Prints configuration information.
- **Example Usage**: Provides example usage of the script.
- **Configuration Generation**: Generates VSCode configuration files.

## Script Overview

### Directories and Files

- **Start Directory**: Current working directory.
- **VSCode Directory**: `.vscode` directory in the start directory.
- **Cache Directory**: `.cache` directory inside `.vscode`.
- **Build Directory**: `build` directory in the start directory.
- **Script Directory**: `scripts` directory in the start directory.
- **Bin Directory**: `bin` directory in the start directory.
- **Docs Directory**: `docs` directory in the start directory.
- **Cache File**: `.cache/cmake_sha1sum.txt` in the start directory.
- **CMake File**: `scripts/CMakeLists.txt`.
- **Database File**: `build/compile_commands.json`.
- **Clangd Database File**: `.vscode/compile_commands.json`.
- **Vscode launch File**: `.vscode/launch.json`.
- **Vscode tasks File**: `.vscode/tasks.json`.
- **Project Name**: `project`.

### Functions

- **`print_debug(*args, **kwargs)`**: Prints debug messages.

- **`cleanup()`**: Removes build and cache folders.

- **`create_dir()`**: Creates build and cache folders and an empty checksum file.

- **`generate_cmake_flags(build_type)`**: Generates flags for the CMake command.

- **`generate_vscode_files()`**: Generates VSCode configuration files.

- **`check_cmakelists_change()`**: Checks if `CMakeLists.txt` has changed based on SHA1 sum or if the build folder does not exist.

- **`compile(build_type="Debug")`**: Runs CMake and Ninja based on build type.

- **`generate_docs()`**: Generates documentation using Doxygen.

- **`copy_compile_commands()`**: Copies `compile_commands.json` to the VSCode folder.

- **`generate_project(build_type)`**: Builds the project and copies compile commands.

- **`run_project()`**: Runs the project executable.

- **`check_executable(executable)`**: Checks if an executable is installed.

- **`test_required()`**: Checks if required executables are installed.

- **`print_example()`**: Prints example usage.

- **`print_config()`**: Prints configuration information.

## Command Line Arguments

- **`-h`, `--help`**: Print help message.
- **`-c`, `--clean`**: Remove build and cache folders.
- **`-r`, `--run`**: Run the project.
- **`-t`, `--type`**: Specify build type (`release` or `debug`).
- **`-b`, `--build`**: Build the project.
- **`-d`, `--docs`**: Generate documentation.
- **`-i`, `--info`**: Print configuration information.
- **`-e`, `--example`**: Print example usage.
- **`-g`, `--generate`**: Generate VSCode configuration files.

## Example Usage

To rebuild and run the project in debug mode with documentation generation:
```bash
./project_manager.py -cbrtd debug
```

## Requirements

- **Python 3.6+**
- **CMake**
- **Ninja**
- **Doxygen**
- **dot**
- **Clangd**
- **GCC**
- **G++**
- **rsync**
- **sha1sum**

## Command to Install Required Packages
```bash
sudo apt install cmake ninja-build doxygen graphviz clangd gcc g++ rsync coreutils
```

## Notes
To generate vscode configuration files, run the following command:
```bash
./project_manager.py -g
```
To debug **`https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools`** is required in VSCode.