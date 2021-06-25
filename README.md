# CDDC-2021
Writeups on some of the challenges my team solved in CDDC 2021
# Table of Contents
* [Let's Go Hunting (OSINT)]
  * [Track him down!](https://github.com/ZYChua02/CDDC-2021#track-him-down)
* [Linux Rules The World! (Linux)]
  * [Opening the Gate](https://github.com/ZYChua02/CDDC-2021#opening-the-gate)
  * [Scrambled Eggs](https://github.com/ZYChua02/CDDC-2021#scrambled-eggs)
* [Web Takedown Episode 1 (Web Vulnerabilities)]
  * [AccessKey](https://github.com/ZYChua02/CDDC-2021#accesskey)
* [Post Mortem (Forensics)]
  * [Look Closer](https://github.com/ZYChua02/CDDC-2021#look-closer)
* [Credits for challenges](https://github.com/ZYChua02/CDDC-2021#credits-for-challenges)
* [Personal thoughts on the CTF](https://github.com/ZYChua02/CDDC-2021#personal-thoughts-on-the-ctf)
# Let's Go Hunting (OSINT)
## Track him down!
## Challenge Description
TeslaReactor7 seems to be one of the GlobalDominationCorporation cybots. One of TheKeepers founded a strange video on his Youtube channel. Can you track him down?
</br>
</br>
Hint #1:	Everybody has a unique ID…
## Approach
Since the description said that TeslaReactor7 had a Youtube channel, we went there to find information
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123438418-407b4b00-d603-11eb-951c-6a237607e762.png)
</br>
</br>
Looking through the channel, there was just a 15 seconds video saying there we are in the right direction
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123438680-8d5f2180-d603-11eb-8a72-b28b7ae59eda.png)
</br>
</br>
We navigated to the about section and found an email teslareactor7@gmail.com
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123438939-cf886300-d603-11eb-9ebc-8d4405c0eef8.png)
</br>
</br>
From there, we went to find the google id of teslareactor7@gmail.com, by starting a chat with him on Google chats
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123439311-34dc5400-d604-11eb-8e96-222079f71076.png)
</br>
</br>
We clicked on the view members tab (highlighted in blue) and inspect element on the page
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123439733-9bfa0880-d604-11eb-8951-be2f24dfa685.png)
</br>
</br>
After a bit of scrolling, we were then able to find his google id (highlighted in blue)
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123440133-0b6ff800-d605-11eb-9e12-fdb9f49f1f4b.png)
</br>
</br>
With the description being "Track him down", we realised that it may be referring to the location where he has been. With the id that we found, we looked at his google maps contributions by putting in his id in the url as shown.
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123440674-9ea92d80-d605-11eb-8119-a49c256d84b0.png)
</br>
</br>
The flag is found under his review
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123440925-e4fe8c80-d605-11eb-884a-c987a66aa9ff.png)
## The flag
`CDDC21{tR4cK1nGFr4NZy}`
# Linux Rules The World! (Linux)
## Opening the Gate
## Challenge Description
One of TheKeepers has successfully obtained what seems to be one of the GDC private servers. He has sent me the image and another file, but unfortunately, I’m not great with Linux. I think you’re the one for this mission.
</br>
</br>
Target IP: 13.213.192.83
</br>
</br>
Link: Linux.zip
</br>
</br>
SHA256: 441bddcc9d80edd976573a57b53cc63eeac02151cc3086b9dbf556f9f2bbcd6a
## Approach
After unzipping the file, there will be a private key and a note
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123447535-8d175400-d60c-11eb-9586-c69b21ad2670.png)
</br>
</br>
From there first chmod the private key as an insecure private key will not be allowed to ssh to the server
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123441632-aa492400-d606-11eb-81bf-9c6012f82980.png)
</br>
</br>
With the private key and the passphrase given in note.txt we are able to ssh into the target IP as bot1
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123441777-ce0c6a00-d606-11eb-8d1e-721ec7508505.png)
</br>
</br>
Using the ls and cat commands, we are able to find the first flag
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123441900-f09e8300-d606-11eb-97b2-cb7471adbe83.png)
</br>
</br>
## The flag
`CDDC21{S$H_keYs_are_Be!ter_than_PaSSw0rds}`
## Scrambled Eggs
## Challenge Description
Now you’re asking me what are all of these strings? This file looks like scrambled eggs to me. Those crazy Cybots always try to make it harder.
</br>
</br>
Hint #1: Try to use a pattern to find the right string.
## Approach
We switched the user to bot 2 using bot 1 flag and found that there was a data file. 
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123442443-76223300-d607-11eb-82a8-118a08272eca.png)
</br>
</br>
We decided to view the file using nano and got this
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123442553-8fc37a80-d607-11eb-8814-c7abdb5d8ff0.png)
</br>
</br>
After seraching the internet for a while, we found that using `grep -oP '{.*?}' data | sort | uniq` will give us the flag
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123442704-baadce80-d607-11eb-99b6-63fceb59f2e1.png)
## The flag
`CDDC21{Th1s_!s_IT}`
# Web Takedown Episode 1 (Web Vulnerabilities)
## AccessKey
## Challenge Description
Your next target doesn’t look so interesting, but maybe there is a hidden secret somewhere that can be used as the access key
</br>
</br>
Target URL: http://122.248.246.76/YY67RIGZ
</br>
</br>
Hint #1:	Find the secret.js file and try to figure out how you can decode it.
# Approach
I first went to find any js files associated and found the secret.js file
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123443188-3f98e800-d608-11eb-9622-a76ff02b7a16.png)
</br>
</br>
We found out that it was url encoded twice and with the help of cyberchef we are able to get the numbers
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123443304-5dfee380-d608-11eb-8bd4-b7b587208f74.png)
</br>
</br>
We realised this was ASCII Numbers so with the help of rapid tables we were able to quickly decode the flag
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123443536-90a8dc00-d608-11eb-830d-c0e3d6ed7e0e.png)
# The flag
`CDDC21{_ De0bfu$cated-F!aG_} `
# Post Mortem (Forensics)
## Look Closer
## Challenge Description
The resistance managed to find a suspicious file. They believe it contains some useful data. Unfortunately, they weren’t able to retrieve it. Help them find what they are looking for.
</br>
</br>
Link: [LookCloser.zip]
</br>
</br>
SHA256: 093e136f355bac6e40c4823e1e0b79c3cb6b31569ea03969f8f59dcdbdb10482
</br>
</br>
Hint #1: If only xxd could do the opposite…
# Approach
We unzipped the file that was given and found a data.txt with gibberish
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123443984-fa28ea80-d608-11eb-85bb-5ff8a2b375dd.png)
</br>
</br>
We copied a small part of it to find the encoding of it on boxentriq and turns out it was a base64 encoded
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123444169-2e9ca680-d609-11eb-881d-168006bfac4d.png)
</br>
</br>
Using Cyberchef to decode it, we found that it is a hexdump
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123444253-470cc100-d609-11eb-9364-79b8b80f4d55.png)
</br>
</br>
After looking through the hexdump for a while, we found a part that was interesting (underlined in blue)
</br>
</br>
![image](https://user-images.githubusercontent.com/65858555/123445256-4e809a00-d60a-11eb-84e5-a97ab231383d.png)
</br>
</br>
By extracting the last character of each, we were able to piece the flag together
</br>
</br>
ÇE.`C`...ÇE.`D`...ÇE.`D`...ÇE.`C`...ÇE `2`...ÇE¤`1`...ÇE¨`{`...ÇE¬`C`...ÇE°`@`...ÇE´`n`...ÇE¸`_`...ÇE¼`Y`...ÇEÀ`0`...ÇEÄ`u`...ÇEÈ`_`...ÇEÌ`F`...ÇEÐ`1`...ÇEÔ`n`...ÇEØ`D`...ÇEÜ`_`...ÇEà`m`...ÇEä`E`...ÇEè`?`...ÇEì`}`
## The flag
`CDDC21{C@n_Y0u_F1nD_mE?}`
# Credits for challenges
Gladys Chua - Track him down!
</br>
</br>
Tsen Fan Loong - Scrambled Eggs and AccessKey
# Personal thoughts on the CTF
Honestly, to sum up in one word, I would say that it is unfortunate. This CTF has been a mess in terms of organisation and having to delay the start time by 24 hours is clearly not acceptable. Furthermore, there were many bugs, such as someone pwning the linux server and it always being down. However, I did learn something new through the OSINT Challenge, which was very creative and unlike any I have done before in previous CTF and the Forensics Challenge, whereby I did not know that a hexdump can be encoded in base64. Overall, while it was mostly disappointing due to the infrastrcture, I am glad that I took something away from this CTF.
</br>
</br>
I would also like to thank my teammates Gladys, Fan Loong and Tze Keat for taking part in this CTF even though it was during the term break and it being delayed by 1 day.


