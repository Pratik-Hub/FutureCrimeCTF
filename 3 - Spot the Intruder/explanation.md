# Spot the Intruder
Solution of Pratik G K

## Tools used

- grep

## How i did it?

- Inside the folder, ran `grep "Failed password" auth.log | awk '{print $11}' | sort | uniq -c` to filter the ip with most failed IP. 

- Found the most failed IP to be `219.128.75.34`.

- Searched the www-access.log for this ip through `grep "219.128.75.34" apache2/access.log`.

- It resulted in a output which had this: 
> 219.128.75.34 - - [19/Apr/2010:09:23:37 -0700] "GET http://www.wantsfly.com/prx2.php?hash=FABB83E72D135F1018046CC4005088B36F8D0BEDCEA7 HTTP/1.0" 404 1466 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0)" YhL5XgoAAQ4AAEP2EQcAAAAC 11250471

- Wanted to decrypt the hash. So after some time of researching, found that it was Base64 and used `echo "UkFOR0VTVE9STXtMb0dzMGZEZWNlUHRpb059" | base64 -d` to decrypt it.

- Gave me `RANGESTORM{LoGs0fDecePtioN}%` and so removed %.

- The flag was then `RANGESTORM{LoGs0fDecePtioN}`.

## Flag

`RANGESTORM{LoGs0fDecePtioN}`