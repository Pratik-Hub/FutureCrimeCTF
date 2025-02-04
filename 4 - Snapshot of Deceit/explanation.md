# Snapshot of Deceit
Solution of Pratik G K

## Tools used

- volatility3

## How i did it?

- I downloaded the ZIP file.

- Extracted it and found a Memory Dump (`RangeDUMP.DMP`) file. Started doing analysis with volatility

- First ran `vol -f RangeDUMP.DMP windows.info` to find the information about the OS. Then ran `vol -f RangeDUMP.DMP windows.pslist` to find a suspicious program called `cGFzdGViaW4uY2`. Guessed it was from base64 and did an encoding in command line through `echo "cGFzdGViaW4uY2" | base64 -d`.

- Got the output as `pastebin.%` so guessed it was something related to pastebing. Either the code was hosted through it or something was retrived from it or even something was posted to it (maybe a code snippet).

- Then ran some other plugins of volatility to see if I get any useful output but I did not get.

- Read the documentation about other plugins. I learnt there was a plugin `pstree` in windows.

- Ran it `vol -f RangeDump.DMP windows.pstree` and got a lot of output.

- Out of which one among the list was,
```
* 1804	1320	cGFzdGViaW4uY2	0xfa801a8de800	8	258	1	False	2024-03-09 11:54:49.000000 UTC	N/A	\Device\HarddiskVolume1\temp\cGFzdGViaW4uY29tL2ZVN3pFeFhj.exe	"C:\temp\cGFzdGViaW4uY29tL2ZVN3pFeFhj.exe" 	C:\temp\cGFzdGViaW4uY29tL2ZVN3pFeFhj.exe
```

- Got suspicious about the software name as it looked like it was from base64 too. So ran `echo "cGFzdGViaW4uY29tL2ZVN3pFeFhj" | base64 -d`.

- Got the output as a URL: `pastebin.com/fU7zExXc%` and after which i formatted it to be: `pastebin.com/fU7zExXc`.

- Visited the pastebin URL which took me to a Paste by a guest user. But there was the flag! It was written `RANGESTORM{MeMAnaLYsiS}`

- The flag was then `RANGESTORM{MeMAnaLYsiS}`.

## Flag

`RANGESTORM{MeMAnaLYsiS}`