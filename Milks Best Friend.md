# ctflearn - Milk's Best Friend (medium)
## Problem
There's nothing I love more than oreos, lions, and winning. https://mega.nz/#!DC5F2KgR!P8UotyST_6n2iW5BS1yYnum8KnU0-2Amw2nq3UoMq0Y Have Fun :)

Link - https://ctflearn.com/challenge/195

The problem has a link to a mega download file. The download is just a file with an image of an oreo labeled oreo.jpg 

## Solving
This ctf was similar to ones that I have done before, so I already knew what steps I needed to take in order to find the flag. After navigating the the download directory in bash, I used `binwalk` to extract any embedded files

<img width="168" height="22" alt="Screenshot 2026-01-07 122243" src="https://github.com/user-attachments/assets/f920029e-902a-4cb5-96cf-7eb96e3f8844" />

```
$ binwalk -e oreo.jpg

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
9515          0x252B          RAR archive data, version 4.x, first volume type: MAIN_HEAD
```
Going into the folder of the extracted image, there are three files to be found. A .rar file, a text file that contains the message "This is not the flag you are looking for.", and lastly another jpg of two oreos. I did not have unrar installed so I did not do anything with the .rar file. I went and used `binwalk` again on the jpg. 

<img width="161" height="28" alt="image" src="https://github.com/user-attachments/assets/e07b63ac-7bcb-470d-a542-33651c9d9169" />

```
$ binwalk -e b.jpg   

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------

WARNING: One or more files failed to extract: either no utility was found or it's unimplemented
```

This didn't reveal anything so I used the `strings` command to look for any hidden data, which ends up revealing the flag.
<img width="137" height="24" alt="image" src="https://github.com/user-attachments/assets/f986f4cc-cbc8-43be-b325-acecdb1a3c4a" />
```
$ strings b.jpg                         
JFIF
"1$%)+...
383-7(-.+
%----------------------+----------------------+---7
!1AQqa
\5n`]
xsLy
.y fk
vSk:M
DzuMb
_NZ@
]ETyn
Xg3H
nBC_
]95r
C^^[p
Q`';
q`7'
\\o*
. 	&
04KZ
)Qc&
Q{k~
st&[
NW89
Lk$[
1Y79
a0\A
$;6g
%mG+$
DysM
2em7
6M>f
Ztn`$F
qUhTmjN
+67*
e6hi 
0d$j
-ko)'
CH;^u
&Du=
$t$Lv
1/i 
/1-6n
Gx#GA
M8n!
iT0?
kVI8
`.}v
gPl,c
bsDKw
O]=6V1
Rx|!
\l&>
!G=*
HSayi-9
#X3i
c>R2
 $+cmk1
u|h]a
tEp#
&Z	2`
ZMmG
a;}V
{2sRpo7%V
0=Q-C:
[e[!A
|5xk
+NgU
;HO+dD
D272}
`h	:
K`8m:-
Finally, flag{eat_more_oreos}
```

## Conclusion
This was a fun and easy ctf which did not require much research from my end on what tools to use. I was already familiar using `binwalk` and `strings` which were the only tools I needed to solve this ctf.





