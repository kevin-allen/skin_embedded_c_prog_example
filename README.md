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

If ./configure complains about the wrong libtool version
```
libtool: Version mismatch error.  This is libtool 2.4.7, but the
libtool: definition of this LT_INIT comes from libtool 2.4.6.
libtool: You should recreate aclocal.m4 with macros from libtool 2.4.7
libtool: and run autoconf again.
```

run 

```
autoreconf --force --install
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

For development, you might want to add the source from the directory where you are doing the development.

```
devtool add ~/repo/skin_embedded_c_prog_example
```

Otherwise, you can get the latest version via the GitHub repository. This is less practical if you want to test changes you made locally.

```
devtool add https://github.com/kevin-allen/skin_embedded_c_prog_example.git
```

A recipe will be added in this file 

```
ampliphy-vendor-xwayland_sdk/workspace/recipes/skin-embedded-c-prog-example/skin-embedded-c-prog-example_git.bb`
```

Notice that the recipe will have the source set to the GitHub repository by default. This means that someone using our recipe would get the code from there.

 
You can remove the recipe from the workspace layer using

```
devtool reset skin-embedded-c-prog-example
```



#### Build the recipe

If you are building from a local source directory in which you did local compilation for the host/desktop computer, clean the source tree from automake outputs. 

```
cd ~/repo/skin_embedded_c_prog_example
make distclean
```

Then use devtool to do the cross-compilation of the program from the recipe.
```
devtool build skin-embedded-c-prog-example
```

#### Test the application on the device

You will first need to put the image on the device and set up the network connection between your computer and the device.


```
devtool deploy-target skin_embedded_c_prog_bb_example root@192.168.0.2
```

You can then run the command on the target device.

