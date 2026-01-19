# ctflearn - Image Magic (hard)
## Problem
It looks like someone messed up my picture! Can anyone reorganize the pixels? The python module PIL (Python Imaging Library) might be useful! https://mega.nz/#!OKxByZyT!vaabCJRG5D9zAUp7drTekcA5pszu67r_TbQMtxEzqGE

Update: I think whoever messed up my image took every column of pixels and put them side by side. Update: I think the width of the image was 304 before they messed with it.

Link - https://ctflearn.com/challenge/89

The download link has an image that has nothing when opened up.

## Solving
The problem description contains a lot of very useful hints that set me on the right direction on how to start this ctf. It mentions to use PIL as well two additional pieces of information saying that the columns of pixels are side by side and that the width of the image was 304 originally.
I was not previously familiar with PIL or how to edit images so I had to do a bit of research on PIL. I found this documentation for pillows (https://pillow.readthedocs.io/en/stable/handbook/index.html) which is just a fork of PIL.

