skin_embedded_c_prog_example
==========

Example of c application that can be compiled with autotool. The example contain a shared library.

This repository can be used as a source repository for a Yocto/OpenEmbedded recipe.


### Compile on host computer using the host compiler.

Use a terminal in which you have not set variables for cross-compiling (see yocto eSDK documentation).


Install libtool.

```
sudo apt-get install libtool
```

run

```
autoreconf
./configure 
make
sudo make install
```


### Include this c program to a yocto project using the eSDK

With a new terminal, set the environment to work with the eSDK.

```
cd ~/ampliphy-vendor-xwayland_sdk
. environment-setup-cortexa53-crypto-phytec-linux
```

Add a recipe to the eSDK image and build from source

```
devtool add https://github.com/kevin-allen/skin_embedded_c_prog_example.git
#devtool edit-recipe skin-embedded-c-prog-example
devtool build skin-embedded-c-prog-example
```

Test the application on the device

```
devtool deploy-target skin_embedded_c_prog_bb_example root@192.168.0.2
```
