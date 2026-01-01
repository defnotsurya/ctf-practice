# ctflearn - forensics (medium)
## Problem
https://mega.nz/#!CXYXBQAK!6eLJSXvAfGnemqWpNbLQtOHBvtkCzA7-zycVjhHPYQQ I think I lost my flag in there. Hopefully, it won't get attacked...
Link - https://ctflearn.com/challenge/97

Clicking the link brings to a mega file download, downloading an png file of an Americas Got Talent contestant.

## Solving
This was similar to a CTF I had solved in school, so I had a decent idea of what to do. I used `binwalk` to extract the png further to see if there were any hidden files.

using binwalk, I extracted the AGT.png file and found this

<img width="163" height="23" alt="Screenshot 2025-12-31 180643" src="https://github.com/user-attachments/assets/75a81894-24de-4a07-a9c0-2b28c7b42e35" />

```
$ binwalk -e AGT.png  

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------

WARNING: Extractor.execute failed to run external extractor 'jar xvf '%e'': [Errno 2] No such file or directory: 'jar', 'jar xvf '%e'' might not be installed correctly
9584          0x2570          Zip archive data, at least v1.0 to extract, name: Secret Stuff.../
9646          0x25AE          Zip archive data, at least v2.0 to extract, name: Secret Stuff.../.DS_Store
10270         0x281E          Zip archive data, at least v1.0 to extract, name: __MACOSX/
10325         0x2855          Zip archive data, at least v1.0 to extract, name: __MACOSX/Secret Stuff.../
10396         0x289C          Zip archive data, at least v2.0 to extract, name: __MACOSX/Secret Stuff.../._.DS_Store
10546         0x2932          Zip archive data, at least v1.0 to extract, name: Secret Stuff.../Don't Open This.../
10627         0x2983          Zip archive data, at least v2.0 to extract, name: Secret Stuff.../Don't Open This.../.DS_Store
10988         0x2AEC          Zip archive data, at least v1.0 to extract, name: __MACOSX/Secret Stuff.../Don't Open This.../
11078         0x2B46          Zip archive data, at least v2.0 to extract, name: __MACOSX/Secret Stuff.../Don't Open This.../._.DS_Store
11247         0x2BEF          Zip archive data, at least v2.0 to extract, name: Secret Stuff.../Don't Open This.../I Warned You.jpeg
150550        0x24C16         Zip archive data, at least v2.0 to extract, name: __MACOSX/Secret Stuff.../Don't Open This.../._I Warned You.jpeg

WARNING: Extractor.execute failed to run external extractor 'jar xvf '%e'': [Errno 2] No such file or directory: 'jar', 'jar xvf '%e'' might not be installed correctly
151832        0x25118         Zip archive data, at least v1.0 to extract, name: Secret Stuff.../
151894        0x25156         Zip archive data, at least v2.0 to extract, name: Secret Stuff.../.DS_Store
152518        0x253C6         Zip archive data, at least v1.0 to extract, name: __MACOSX/
152573        0x253FD         Zip archive data, at least v1.0 to extract, name: __MACOSX/Secret Stuff.../
152644        0x25444         Zip archive data, at least v2.0 to extract, name: __MACOSX/Secret Stuff.../._.DS_Store
152794        0x254DA         Zip archive data, at least v1.0 to extract, name: Secret Stuff.../Don't Open This.../
152875        0x2552B         Zip archive data, at least v2.0 to extract, name: Secret Stuff.../Don't Open This.../.DS_Store
153236        0x25694         Zip archive data, at least v1.0 to extract, name: __MACOSX/Secret Stuff.../Don't Open This.../
153326        0x256EE         Zip archive data, at least v2.0 to extract, name: __MACOSX/Secret Stuff.../Don't Open This.../._.DS_Store
153495        0x25797         Zip archive data, at least v2.0 to extract, name: Secret Stuff.../Don't Open This.../I Warned You.jpeg
292768        0x477A0         Zip archive data, at least v2.0 to extract, name: __MACOSX/Secret Stuff.../Don't Open This.../._I Warned You.jpeg
294050        0x47CA2         Zip archive data, at least v1.0 to extract, name: Secret Stuff.../
294112        0x47CE0         Zip archive data, at least v2.0 to extract, name: Secret Stuff.../.DS_Store
294736        0x47F50         Zip archive data, at least v1.0 to extract, name: Secret Stuff.../Don't Open This.../
294817        0x47FA1         Zip archive data, at least v2.0 to extract, name: Secret Stuff.../Don't Open This.../.DS_Store
295162        0x480FA         Zip archive data, at least v2.0 to extract, name: Secret Stuff.../Don't Open This.../I Warned You.jpeg
434433        0x6A101         Zip archive data, at least v1.0 to extract, name: __MACOSX/
434488        0x6A138         Zip archive data, at least v1.0 to extract, name: __MACOSX/Secret Stuff.../
434559        0x6A17F         Zip archive data, at least v1.0 to extract, name: __MACOSX/Secret Stuff.../Don't Open This.../
434649        0x6A1D9         Zip archive data, at least v2.0 to extract, name: __MACOSX/Secret Stuff.../Don't Open This.../._I Warned You.jpeg
```
I kept seeing the file I Warned You.jpeg, and assumed that the flag had something to do with this, but was unsure exactly what I needed to do with it. Looking at the comments under the ctf I saw mention of strings and remembered that there can be hidden data in the jpeg.

<img width="376" height="40" alt="Screenshot 2025-12-31 180621" src="https://github.com/user-attachments/assets/9f567c12-edae-4df4-88d7-1a5f8c23aa25" />

```
$ strings I\ Warned\ You.jpeg | grep -i "CTF"
ABCTF{Du$t1nS_D0jo}1r
```

## Conclusion
This ctf was a little confusing for me because of the lack of clues and context, but the overall steps needed to find the flag were not complicated.

