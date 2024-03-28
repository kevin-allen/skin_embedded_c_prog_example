skin_embedded_c_prog_example
==========

Example of c application that can be compiled with autotool. The example contain a shared library.

This repository can be used as a source repository for a Yocto/OpenEmbedded recipe.


```
cd ~/ampliphy-vendor-xwayland_sdk
. environment-setup-cortexa53-crypto-phytec-linux
devtool add https://github.com/kevin-allen/skin_embedded_c_prog_bb_example.git
#devtool edit-recipe skin_embedded_c_prog_bb_example
devtool build skin_embedded_c_prog_bb_example
devtool deploy-target skin_embedded_c_prog_bb_example root@192.168.0.2
