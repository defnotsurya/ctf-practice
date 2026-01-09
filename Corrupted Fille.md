# ctflearn - Corrupted File (hard
## Problem
Help! I can't open this file. Something to do with the file header… Whatever that is. https://mega.nz/#!aKwGFARR!rS60DdUh8-jHMac572TSsdsANClqEsl9PD2sGl-SyDk

Link - https://ctflearn.com/challenge/138

The link from the problem downloads a .gif file that is corrupted and unopenable. 

## Solving
The hint from the problem description gives me some information on what approach I need to take in order to solve this, it has something to do with the gif header. Looking at the comments I realized I needed a hexediter in order to be able to edit the header of the file to make it playable
I used HxD (https://mh-nexus.de/en/hxd/) to edit the file, and use Garry Kesslers file signature table (https://www.garykessler.net/library/file_sigs_GCK_latest.html) to find the correct signature for .gif files.
<img width="376" height="38" alt="image" src="https://github.com/user-attachments/assets/d52c2918-a631-4b95-816c-2f5c79583a61" />


<img width="518" height="13" alt="Screenshot 2026-01-09 181102" src="https://github.com/user-attachments/assets/50478579-dde2-4b6c-9fe3-ed9649a6522f" />

Changed to

<img width="514" height="16" alt="image" src="https://github.com/user-attachments/assets/b6fa6403-f71d-44e7-ac17-91406d1a82cd" />

After editing the file in HxD the gif is finally openable. 

![unopenable](https://github.com/user-attachments/assets/15866881-9aef-46f1-a5ea-1b18ee258f65)

The gif contains a message to decode presumably of the key, but it was too hard to read in .gif format so I used an online .gif to .jpg converter. (https://ezgif.com)

After looking at each image in the gif, the text looks to be in base64 so I used CyberChef to decode it.

<img width="198" height="61" alt="Screenshot 2026-01-09 154801" src="https://github.com/user-attachments/assets/f0ee57f7-5fd0-4c55-afaa-c321c603da71" />


<img width="136" height="68" alt="Screenshot 2026-01-09 154807" src="https://github.com/user-attachments/assets/82372a0d-0fd4-4bb6-a908-abb1d28b45f7" />

## Conclusion
This was an interesting ctf for me as I have not used hexeditors previously and was not super familiar with file headers/signatures. It was cool to be able to use a hexedit tool to be able to fix a corrupted file.
