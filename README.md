# WebAssembly FPGA Runtime Project

This is the project repository of the WebAssembly FPGA runtime.

# Workspace setup

This project uses [Google's Repo tool][repo] to work with multiple repositories.

## Install repo tool

    ~$ mkdir ~/bin
    ~$ PATH=~/bin:$PATH
    ~$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    ~$ chmod a+x ~/bin/repo

## Clone repositories

    ~git$ mkdir webassembly && cd webassembly
    ~git/webassembly$ repo init -u https://github.com/denisvasilik/wasm-fpga
    ~git/webassembly$ repo sync

## Create Vivado projects

This project uses a Xilinx FPGA, therefore [Xilinx Vivado][vivado] is used for 
bitstream generation. Each IP project contains a `Make` target named `project` 
that is used to establish a Vivado project.

    ~git/webassembly$ for d in wasm-fpga-*/ ; do cd $d && make project && cd .. ; done

[repo]:https://gerrit.googlesource.com/git-repo/+/refs/heads/master/README.md
[vivado]:https://www.xilinx.com/products/design-tools/vivado.html