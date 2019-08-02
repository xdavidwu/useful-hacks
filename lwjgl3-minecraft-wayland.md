# lwjgl3-minecraft-wayland

Make Minecraft runs native on Wayland

## Why

I use it for HiDPI. On sway with scale, Xwayland has lower resolution is scaled by sway which make it blur.
Running native on Wayland make it render at native resolution regardless of scale.

Performance may also differ from X11 setup.

Why hacking and patching on lwjgl? Just because it has source.

## How

Make those functions that are not working yet/ not possible on Wayland do nothing.
See the patch for detail.

## Why this is dirty

Of course it is. It fixes Minecraft's code by hacking a library.

Those LWJGL/ GLFW behavior on Wayland is well-documented and intended.

It's Minecraft that haven't updated their code to support Wayland.

## Why don't make it clean

Not interested in decompiling Minecraft.

## How to use

```
Launch Minecraft and note down the full command line
Get LWJGL source
Patch
Run ant
cd bin/classes/lwjgl/glfw
zip -u <lwjgl-glfw jar path observed from Minecraft launching command> org/lwjgl/glfw/GLFW.class
Run Minecraft by the command with -Dorg.lwjgl.glfw.libname=glfw_wayland injected into JVM args.
```

Don't run Minecraft from launcher anymore. It may check the library checksum, find it altered and re-download the library.
