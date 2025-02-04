# Obscured Truth
Solution of Pratik G K

## Tools/Services Ssed

- xxd

- binwalk

- https://hexed.it

- https://en.wikipedia.org/wiki/List_of_file_signatures

## How i did it?

- First I opened the broken PDF in https://hexed.it to analyze the magic bytes (first few bytes of a file).

- Realised it was not of a PDF.

- Searched https://en.wikipedia.org/wiki/List_of_file_signatures to match the magic bytes but none matched. So I confirmed it was not a regular file. Came to a conclusion that it was either an own file type or something which is not very popular.

- I started researching about Bytes. I learnt since 0x5x was repeating, it was a XOR encrypted file.

- I had to decrypt it. So, I started learning about XOR on a surface level. I discovered I can use xxd to decrypt it through `xxd -p Policy_data.pdf | tr -d '\n' | xxd -r -p | perl -pe 's/(.)/chr(ord($1) ^ key)/eg' > decrypted.bin` but had to find out what the key was.

- I tried some keys manually but the output was bad (refer the file `manual.jpg`).

- So wrote a Python script to brute force XOR:
```
# XOR Brute Force Decryption Script

def xor_decrypt(data, key):
    return bytes([b ^ key for b in data])

# Read the encrypted file
with open("Policy_data.pdf", "rb") as f:
    encrypted_data = f.read()

# Try all possible XOR keys (0x00 - 0xFF)
for key in range(256):
    decrypted_data = xor_decrypt(encrypted_data, key)
    
    # Save the potential output as a JPEG file
    output_file = f"decrypted_{key}.jpg"
    with open(output_file, "wb") as out:
        out.write(decrypted_data)

    print(f"Saved attempt with key {hex(key)} as {output_file}")

```
- As the 90th file, I got one which opened and saw a poster.

- Tried a lot of combinations from the poster (i.e the Top Skills Poster) but none worked.

- After sometime of trying, left it and went to a different challenge.
- After some more time, came back to this.

- Now having used binwalk, I thought of trying on this decrypted file and it seemed the decrypted file had two more files with a parent folder (folder name - 2DA0A) embedded in it!

- Upon opening the parent folder, I saw an image and a spreadsheet file. Tried some combinations from the image (random ones with hints from the contents of the image) and nothing worked.

- Opened the spreadsheet file `U3o.xlsx` and there was a text `UkFOR0VTVE9STXtGSUxFTUFaRX0=`.

- Tried `RANGESTORM{UkFOR0VTVE9STXtGSUxFTUFaRX0=}` but it not work.

- So tried to decrypt `UkFOR0VTVE9STXtGSUxFTUFaRX0=` from Base64 and got the flag as `RANGESTORM{FILEMAZE}%`! After which I formatted it.

- The flag was `RANGESTORM{FILEMAZE}`.

## Flag

`RANGESTORM{FILEMAZE}`