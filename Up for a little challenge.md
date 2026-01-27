# ctflearn - Up For a Little Challenege (medium)
## Problem
https://mega.nz/#!LoABFK5K!0sEKbsU3sBUG8zWxpBfD1bQx_JY_MuYEWQvLrFIqWZ0

You Know What To Do ...

Link - https://ctflearn.com/challenge/142

## Solving
The description of the problem doesn't really give me much to work with, so the only start is to download the files from the link.
The download contains the file `Begin Hack.jpg`. 

I first use `binwalk -e Begin\ Hack.jpg` to check for any hidden files I need to extract. 

<img width="637" height="161" alt="Screenshot 2026-01-27 034952" src="https://github.com/user-attachments/assets/63bfe38e-fbd4-45f5-aba2-477ed9d863c6" />

The extraction brings up nothing extra, so I move onto trying `strings -n 10 Begin\ Hack.jpg` to look for any hidden data

<img width="642" height="195" alt="Screenshot 2026-01-27 035011" src="https://github.com/user-attachments/assets/2227afb7-a07e-45bb-add0-d4b70a3c28fd" />

This shows us a lot of hidden data with an additional mega file link, as well as an unlock key and a password. There is also a flag at the bottom which I try just in case but as expected it does not work
The download from the link gives us "Up For A Little Challenge.zip . I extract the file using `binwalk -e Up\ For\ A\ Little\ Challenge.zip

<img width="640" height="419" alt="Screenshot 2026-01-27 035030" src="https://github.com/user-attachments/assets/c426afa7-0c2c-4ef6-ab40-1a1df2f907e2" />

<img width="634" height="49" alt="Screenshot 2026-01-27 035135" src="https://github.com/user-attachments/assets/d7b55d6a-ca47-4037-8d8b-519c6b425bef" />

After extracting there is a folder "Did I Forget Again?". The folder contains only one file "Loo Nothing Becomes Useless ack.jpg". I use strings and binwwalk on the file but don't get any extra information.

I use `ls -la` to check for any hidden files in the folder which shows the hidden file ".Processing.cerb4"

<img width="642" height="149" alt="Screenshot 2026-01-27 035144" src="https://github.com/user-attachments/assets/0c969635-7ae4-4fe5-8666-ed23aa3191f2" />

I am not really sure what to do with this file since it has this wierd .cerb4 extension but after looking on google a bit I realize that it is just a .zip file disguised. I proceed to unzip the file which brings me to a password entry selection.

<img width="633" height="94" alt="Screenshot 2026-01-27 035202" src="https://github.com/user-attachments/assets/b81b6fe2-3da7-4fbd-8d3b-72a53e2cd3e6" />

I go back to the passwords and unlock key options from the previous strings results from Begin Hack.jpg

<img width="349" height="41" alt="Screenshot 2026-01-27 035219" src="https://github.com/user-attachments/assets/611e639c-94b6-4b65-b6a0-c95f918e4489" />

I enter `Nothing Is As it Seems` into the password entry and unlocks and image.

In the corner of the image I find a flag which is the correct flag to solve the ctf.

<img width="177" height="141" alt="Screenshot 2026-01-27 035233" src="https://github.com/user-attachments/assets/387786c2-cb67-40d9-850e-63607705faa9" />

## Conclusion
This was a very fun ctf that felt like I was looking for some hidden treasure. There was a lot of hidden data and infomration in the different files that required looking around and using different sorts of commands to find all the data. It was a little tricky because of the hidden files and the extra useless files in the folders, but was not too difficult in terms of the tools and skills needed to solve.


