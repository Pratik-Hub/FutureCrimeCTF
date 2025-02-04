# Catch Me If You Can
Solution of Pratik G K

## Tools used

- Wireshark

## How i did it?

- Opened the PCAP inside Wireshark.

- First filtered the requests through `http` and `dns`.

- Became suspicious about `vclphjybj.ioxbpjgtqvwqfzmwhn.ga`, `tpfnmvg.ioxbpjgtqvwqfzmwhn.ga`, `lk2gaflsgh.jgy658snfyfnvh.com`.

- And while scrolling, I found `http://vitaminsthatrock.com/` too, but kept it aside for now.

- Now searched online for the three URLs and found they where linked with **Neutrino Kit**.

- But there were many exploits and ransomwares in the kit and I had to find which one was it exactly.

- After analyzing the TCP Streams and HTTP Streams, I found it was making some requests about some images like `bitcoin.png`, `button_pad.png`.

- Confirmed that it was a crypt based/scam based exploit.

- Therefore I had Tesla Crypt (a part of Neutrino Kit) in mind but it was not the password to the ZIP.

- Then searched google to exactly match the URL `http://vitaminsthatrock.com/` for the sake of giving it a try after looking at this in a TCP Stream.:
> GET /giant/1171219/host-dare-creature-valley-pour-tunnel-sense-season-thumb-soft HTTP/1.1
Accept: text/html, application/xhtml+xml, */*
Referer: http://vitaminsthatrock.com/
Accept-Language: en-US
User-Agent: Mozilla/5.0 (Windows NT 6.1; Trident/7.0; rv:11.0) like Gecko
Accept-Encoding: gzip, deflate
Host: vclphjybj.ioxbpjgtqvwqfzmwhn.ga:13390
DNT: 1
Connection: Keep-Alive

- Found an aritcle about the same in https://www.herbiez.com/?p=173.

- The article confirmed it was Neutrino Kit.

- A blog `https://blog.naver.com/stop2y/221034576310` citied the same URL and it was analyzed that it could be either TeslaCrypt or AlphaCrypt.

- `AlphaCrypt` worked.

- Therefore, the ZIP file was extracted and got access to the `flag.txt`.

- The flag was found to be `RANGESTORM{C2BeACoNInG}`.

## Flag

`RANGESTORM{C2BeACoNInG}`