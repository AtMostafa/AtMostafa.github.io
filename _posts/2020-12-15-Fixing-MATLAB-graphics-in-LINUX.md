---
layout: post
title: "Fix MATLAB graphic acceleration in Linux"
author: Mostafa
tags: Matlab Python opengl graphic gpu
---

I realised that graphics are very slow in my freshly-installed MATLAB on KDE Neon Distro.
My laptop doesn't have a dedicated GPU, only the onboard Intel graphics, but still.

Run `opengl('save','hardware')`, restart Matlab and check the results of `opengl info`.
There must be some sort of renderer detected (in my case, _MESA X11_).
After losing a couple of hours, I found the solution, partly from [here](https://uk.mathworks.com/matlabcentral/answers/241374-libgl-error-persists-and-i-ve-tried-everything).

First, I navigated to `.../sys/os/glnxa64` under the Matlab installation directory and then did the following:
```
mv libgcc_s.so.1 libgcc_s.so.1.bak
mv libstdc++.so libstdc++.so.bak
mv libstdc++.so.6 libstdc++.so.6.bak
mv libstdc++.so.6.** libstdc++.so.6.**.bak
```
The exact version might differ.

Then, I linked the system files by:
```
ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6.20 libstdc++.so
ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6 libstdc++.so.6
```
Again, the exact file paths and file versions might differ.

Apparently that was enough for some people, but not for me.
The error was still there.
Then, I found something else online:

> Create a file with the name `java.opts` in the directory where MATLAB is executed (for me this is in `'/usr/local/MATLAB/R2020a/bin/glnxa64'`) with the following line: `-Djogl.disable.openglarbcontext=1`
> If this does not work, then the above solution using `export MESA_LOADER_DRIVER_OVERRIDE=i965` is working.

Both solutions worked for me!
Finally:
`opengl('save','hardware')` once more, restart and `opengl info` now returns:
```
>> opengl info
                          Version: '4.6 (Compatibility Profile) Mesa 20.0.8'
                           Vendor: 'Intel'
                         Renderer: 'Mesa Intel(R) UHD Graphics 620 (WHL GT2)'
                   MaxTextureSize: 16384
                           Visual: 'Visual 0x442, (RGBA 32 bits (8 8 8 8), Z depth 16 bits, Hardware acceleration, Double buffer, Antialias 8 samples)'
                         Software: 'false'
             HardwareSupportLevel: 'full'
        SupportsGraphicsSmoothing: 1
    SupportsDepthPeelTransparency: 1
       SupportsAlignVertexCenters: 1
                       Extensions: {293×1 cell}
               MaxFrameBufferSize: 16384

>> 
```
Voila!