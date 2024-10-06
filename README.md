**This is a fork of SkePU and is not a mirror.**

# Language Server For SkePU
This is a langauge server implementation for [SkePU](https://skepu.github.io/). This was made as a master thesis project <Insert link to rapport> and is based on clangd. The implementation constists of two parts, a language client extension which lies in the submodule vscode-clangd, and a language server /llvm/clang-tools-extra/skepud.

## Setup

### Cloning with submodules
This repository should be cloned with `git clone --recursive $URL` in order to also clone the submodules it links to. `git submodule update --init` can be used to clone submodules to an existing repository.

### SkePU
First and foremost, build SkePU by following the instructions of the [main repo](https://github.com/skepu/skepu/)

### Langauge Server
1. Create a build directory, for example at LLVM/build.
2. Inside the build directory run: `cmake ../llvm/ -DCMAKE_BUILD_TYPE=Release -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra`".
3. Afterwards you can build the language server with `cmake --build . --target skepud`. **IMPORTANT: This takes a long time to build the first time**

### Language Client
Inside the extension.ts check the file path of the server modules so that it matches the executable language server
Follow the project setup from [clangd](https://clangd.llvm.org/installation) on how to setup the file `compile_commands.json`.

## How to Run
Open up the language client folder (vscode-clangd) in VS code and then if everything is setup correctly you can hit launch extension in the `Run and Debug` menu. This will openup a new seperate window in which you will have to open up the examples folder of the repo.

## Modifying language server
### Language Client
To modify is really simple, just type go ahead and open up the folder vscode-clangd in vscode, make your changes and then run it.

### Language Server
Open up /llvm/clang-tools-extra/skepud in your favorite editor, make changes, save.
Then in the build directory of LLVM run `cmake --build . --target skepud` this will build your updated language server.

