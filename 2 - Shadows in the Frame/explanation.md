# Shadows in the Frame
Solution of Pratik G K

## Tools used

- steghide

- gpg (Gpg4win)

## How i did it?

- I downloaded the image file]

- Ran it via `strings` command through `strings rangestorm.jpg`.

- Two strings looked suspicious. They were `coffeeisbetterthantea` and `testing test`.

- **After long failed attempts of using other tools**, used my windows machine to use steghide (as it is windows-only). 

- Inside the steghide directory, I copied the `rangestorm.jpg`.

- Then in Command Prompt, I executed the command `steghide.exe extract -sf rangestorm.jpg`.

- It then wrote the extracts into a file called `cover.txt.gpg`.

- I then tried to decrypt the file  through `gpg --decrypt cover.txt.gpg` but then was met with a cmd-screen to enter the passphrase. I then tried the suspicious looking strings from the `strings` command output.

- Out of the two, `coffeeisbetterthantea` was the passphrase. Immediately after, I was echoed with the flag.

- The flag was then `RANGESTORM{IMAGESTORM}`.

## Flag
`RANGESTORM{IMAGESTORM}`