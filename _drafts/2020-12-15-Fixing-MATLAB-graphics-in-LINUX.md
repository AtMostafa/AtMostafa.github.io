---
layout: post
title: "Fix MATLAB graphic acceleration in Linux"
author: Mostafa
tags: Matlab Python
---

[here](https://uk.mathworks.com/matlabcentral/answers/241374-libgl-error-persists-and-i-ve-tried-everything)

First I have gone to sys/os/glnxa64 under matlab and then do two thing.
```
mv libgcc_s.so.1 libgcc_s.so.1.bak
mv libstdc++.so libstdc++.so.bak
mv libstdc++.so.6 libstdc++.so.6.bak
mv libstdc++.so.6.** libstdc++.so.6.**.bak
```
Then, I link the system files by
```
ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6.20 libstdc++.so
ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6 libstdc++.so.6
```
which was suggested by some, and may require for few cases. But error was still there. Then I removed
`mv libgcc_s.so.1 libgcc_s.so.1.bak`

it didn't work, in the end:


I also ran into this issue on my Dell XPS 13 9360 which neither has a NVIDIA or AMD card, but an on-board intel graphics card.
I filed a bug report with MATHWORKS and they proposed two solutions:

    Create a file with the name 'java.opts' in the directory where MATLAB is executed (for me this is in '/usr/local/MATLAB/R2020a/bin/glnxa64') with the following line: `-Djogl.disable.openglarbcontext=1`
    If this does not work, then the above solution using export MESA_LOADER_DRIVER_OVERRIDE=i965 is working.

For me both solve my issue.



finally:
`opengl('save','hardware')` to see the resutls and `opengl info`