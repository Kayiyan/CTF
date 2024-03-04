# 1.
* Challenge Name : They Are Coming
* Chall Description : Aesthetic Looking army of 128 Robots with AGI Capabilities are coming to destroy our locality!

* Given : Nothing ( Start instance web ) 

* Solution :

View robots.txt : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/c056a704-5c0c-482a-87c6-a3fbd2d53879)


Get important information that may be noted:

`L3NlY3JldC1sb2NhdGlvbg==`
`Decryption key: th1s_1s_n0t_t5e_f1a9`

Decrypted `base64` encod : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/19873115-0a63-40b8-8cf5-5f98f0db8f60)

Move to the file from message then check the local store : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/8eee7aab-063a-488b-b3ec-975bb84b41d0)

Got : `Gkul0oJKhNZ1E8nxwnMY8Ljn1KNEW9G9l+w243EQt0M4si+fhPQdxoaKkHVTGjmA` ->cipher identify this is AES encryption 128 bit so we need decrypt this , with the key has in the previous step

Using this web for decode : https://encode-decode.com/aes128-encrypt-online/

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/0ecc5751-359e-48f4-b9cf-8452908301fc)

* Flag : `VishwaCTF{g0_Su88m1t_1t_Qu14kl7}`
  
# 2
* Challenge Name : H34D3RS
* Chall Description : Name of the challenge says something

* Given : Nothing ( Start instance web ) 

* Solution :

Add headers : 

Referer: https://vishwactf.com/
Date: 2044
Downlink: 999999999

Fix : Upgrade-Insecure-Requests -> 10 and User-Agent: lorbrowser

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/af0a28fd-18ca-4f7e-a14a-eb9c2e48858c)

* Flag : `VishwaCTF{s3cret_sit3_http_head3rs_r_c0o1}`
# 3 

* Challenge Name : HARDWARE HEIST
* Chall Description : Your cyber gang has stolen a hardware device code from the CIA but are unable to use it. Although while stealing the code, you have found some binary strings which might be helpful to understand the device. You might even find the important codes after solving the device and strings.

* Given : File Hardware.rar ( no need to use this ) and BINARY INPUT.txt

* Solution :

View file txt : `110100001101001100011110101101100110110010011010110111110110101111010111000111101011101111101101000110111101111111010000110100011001011001001110111011010001100100110011`

Decode From binary range 7 because range 9 is out of range : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/2e019163-4b6a-47d2-b35a-7ef15cf757f3)

* Flag : `VishwaCTF{h4ck325_5uck_47_h42dw423}`
# 4.
* Challenge Name : Sandese Aate hai
* Chall Description : A friend pranked me by encrypting my letter but gave me the program by which he encrypted it. Can you help me decrypt it?
                      Replace one of the s with w at the end after receiving the letter

* Given :File Program and file encletter.txt( no need to use )

* Solution :

Run file Program can help get the Original matrix :

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/34cb61d9-0fa5-43f9-ad8e-124df18991c4)

My idea is to decode this matrix clockwise, and accordingly get the code I'm looking for :

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/c34ab2aa-6dd6-4b8f-8607-db42744a4a25)

* Flag : `VishwaCTF{4nd23y_4nd23y3v1ch_m42k0v}`

# 5.
* Challenge Name : Router |port|
* Chall Description : There's some unusual traffic on the daytime port, but it isn't related to date or time requests. Analyze the packet capture to retrieve the flag

* Given : Capture.pcang

* Solution :

Search about daytime port -> got this is port 13 : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/8e12b84f-3282-4918-9585-f4e0f6f93dfb)

Fillter it : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/732c6fe1-086c-4148-ab53-87363b6c5bce)

It's some message at here : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/cda3d0ce-7307-46d2-8d09-ec2b1cfb8a78)

This is encoded in Vigenère so need decode all message in all packets : 

```

Hey, mate!
Yo, long time no see!
You sure this mode of communication is still safe?
Yeah, unless someone else is capturing network packets on the same network we're using. Anyhow, our text is encrypted, and it would be difficult to interpret.
So let's hope no one else is capturing.
What's so confidential that you're about to share?
It's about cracking the password of a person with the username 'Anonymous.'
Oh wait! Don't you know I'm not so good at password cracking?
Yeah, I know, but it's not about cracking. It's about the analysis of packets. I've completed most of the job, even figured out a way to get the session key to decrypt and decompress the packets.
Holy cow! How in the world did you manage to get this key from his device?
Firstly, I hacked the router of our institute and closely monitored the traffic, waiting for 'Anonymous' to download some software that requires admin privilege to install. Once he started the download, I, with comple
Whoa! It's so surprising to see how much you know about networking or hacking, to be specific.
Yeah, I did a lot of research on that. Now, should we focus on the purpose of this meet?
Yes, of course. So, what should I do for you?
Have you started the packet capture as I told you earlier?
Yes, I did.
Great! I will be sending his SSL key, so find the password of 'Anonymous.'
Yes, I would, but I need some details like where to start.
The only details I have are he uses the same password for every website, and he just went on to register for a CTF event.
Okay, I will search for it.
Wait a second, I won't be sending the SSL key on this Daytime Protocol port; we need to keep this untraceable.
I will be sending it through FTP. Since the file is too large, I will be sending it in two parts. Please remember to merge them before using it. Additionally, some changes may be made to it during transfer due to the 
Okay!

```
-->  with `Anonymous` -> user default in ftp protocol 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/6ffbfe3c-f38d-4bc5-b455-6629951c60b9)

Data : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/70f7ec28-af2b-4e7b-a955-6eb2edef9f64)

Export all This , Decode with Vigenere Cipher Again and got the key to decrypt TLS , Add The Key to TLS Protocols to Decrypt -> Now can filter out http protocol and filter contains with 'password' to find the password :

Save all Decode result to a file .txt save it with the name key for easy to remember then add it to TLS protocol : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/419b46ea-3d5a-4772-acd4-4c8cbec8b021)

Filter http with password contains in it : 

![image](https://github.com/Kayiyan/CTF_Team_Write-up/assets/126185640/2ec3b985-f2a3-4abb-8cd9-f512eeacb51c)

* Flag : `VishwaCTF{K3Y5_CAN_0P3N_10CK5}`

6.
