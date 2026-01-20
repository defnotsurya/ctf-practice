# ctflearn - Image Magic (hard)
## Problem
It looks like someone messed up my picture! Can anyone reorganize the pixels? The python module PIL (Python Imaging Library) might be useful! https://mega.nz/#!OKxByZyT!vaabCJRG5D9zAUp7drTekcA5pszu67r_TbQMtxEzqGE

Update: I think whoever messed up my image took every column of pixels and put them side by side. Update: I think the width of the image was 304 before they messed with it.

Link - https://ctflearn.com/challenge/89

The download link has an image that has nothing when opened up.

## Solving
The problem description contains a lot of very useful hints that set me on the right direction on how to start this ctf. It mentions to use PIL as well two additional pieces of information saying that the columns of pixels are side by side and that the width of the image was 304 originally.
I was not previously familiar with PIL or how to edit images so I had to do a bit of research on PIL. I found this documentation for pillows (https://pillow.readthedocs.io/en/stable/handbook/index.html) which is just a fork of PIL.

The first thing I did was load the image using PIL and numpy to inspect the current dimensions of the image
```
from PIL import Image
import numpy as np

img = Image.open(r"C:\Users\crazy\Downloads\out copy.jpg")
pixels = np.array(img)
print(pixels.shape)
```
This returned 
```
(1, 27968, 3)
```
Since we have the origninal width of the image, I take the total pixels and divide it by 304
```
orig_height = flat.shape[0] // orig_width
```
This gives the orginal image size of 92 x 34

I used `fixed = flat.reshape(orig_height, orig_width, c)` to try and correct the image but just got this
<img width="304" height="92" alt="image" src="https://github.com/user-attachments/assets/a0f359a7-0510-40fa-b83f-26ef95c2f5b5" />

After looking into it more I had to reshape the column order since that was what the attackers changed.

`fixed = flat.reshape((orig_height, orig_width, 3), order='F')`

This reshaped the columns of the image and undid the stacking
```
fixed_img = Image.fromarray(fixed.astype(np.uint8))
```
The last changes are to convert the numpy array back to a pillows image.
```
fixed_img.save(r"C:\Users\crazy\Downloads\outcopy fixed.jpg")
```
![recovered](https://github.com/user-attachments/assets/76102b4f-bc6a-483b-8d48-bb6dd5cb22f0)

## Conclusion
Doing this ctf taught me a lot of skills and taught me about a new python library that I had not used before. This was quite difficult to figure out since I did not have any experience with these tools before, but the hints from the ctf instructions as well as comments on the page helped a lot to put me on the right track in order to be able to solve this.




