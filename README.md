# WebAssembly FPGA Runtime

This is the project repository of the WebAssembly FPGA runtime. It comprises
project goals, architectural documentation and general information regarding
development and contribution.

# Prerequisites

* [Xilinx Vivado 2019.2][vivado]
* HxS Interface Generation Tool

# Workspace setup

This project uses [Google's Repo tool][repo] to work with multiple repositories.

## Install repo tool

Use the following instructions to install the Repo tool.

    ~$ mkdir ~/bin
    ~$ PATH=~/bin:$PATH
    ~$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    ~$ chmod a+x ~/bin/repo

Further information regarding the Repo tool can be found [here][repo].

## Clone repositories

After having installed the Repo tool, all project related repositories can be 
synced.

    ~git$ mkdir webassembly && cd webassembly
    ~git/webassembly$ repo init -u https://github.com/denisvasilik/wasm-fpga
    ~git/webassembly$ repo sync

Now, the workspace is ready for development.

## Create Vivado projects

This project uses a Xilinx FPGA, therefore [Xilinx Vivado][vivado] is used for 
bitstream generation. Each IP project contains a `Make` target named `project` 
that is used to establish a Vivado project.

    ~git/webassembly$ for d in wasm-fpga-*/ ; do cd $d && make project && cd .. ; done

The Vivado project is located in the `work` directory of each `wasm-fpga-*` root 
folder.

[repo]:https://gerrit.googlesource.com/git-repo/+/refs/heads/master/README.md
[vivado]:https://www.xilinx.com/products/design-tools/vivado.html