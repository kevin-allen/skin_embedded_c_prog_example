skin_embedded_c_prog_example
==========

Example of c application that can be compiled with autotool. The example contain a shared library.

This repository can be used as a source repository for a Yocto/OpenEmbedded recipe.


### Compile on host computer using the host compiler.

Use a terminal where you have not set variables for cross-compiling (see yocto eSDK documentation).

```
cd ~/repo
git clone https://github.com/kevin-allen/skin_embedded_c_prog_example.git
cd skin_embedded_c_prog_example
```


Install libtool.

```
sudo apt-get install libtool
```

run

```
cd ~/repo/skin_embedded_c_prog_example
autoreconf
./configure 
make
sudo make install
```

You can then run the program using 
```
./skin_embedded_c_prog_example
```

### Include this c program to a yocto project using the eSDK

To do this part, you will have to [install the eSDK](https://github.com/kevin-allen/phyBOARD/blob/main/yocto_eSDK.md) for your target image on your computer.

Here is some information on how I did this: https://github.com/kevin-allen/phyBOARD/blob/main/phytec_distribution.md

#### Set your environment

With a new terminal, the environment must be set to work with the eSDK. Do the following.

```
cd ~/ampliphy-vendor-xwayland_sdk
. environment-setup-cortexa53-crypto-phytec-linux
```

#### Adding a recipe to your image

Add a recipe to the eSDK image and build from the source.

```
devtool add https://github.com/kevin-allen/skin_embedded_c_prog_example.git
#devtool edit-recipe skinembedded-c-prog-example
devtool build skin-embedded-c-prog-example
```

#### Test the application on the device

You will first need to put the image on the device and set up the network connection between your computer and the device.


```
devtool deploy-target skin_embedded_c_prog_bb_example root@192.168.0.2
```

You can then run the command on the target device.

