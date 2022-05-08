## PinBreak

This is the first time I did an Android based CTF challenge. I quickly read up on the tools generally used.  
I used `jadx` for this challenge. I loaded the apk into it, and immediately noticed that the pin was stored encrypted in the pinDB database. I looked around in the resources folder and actually found it. That was easy. The password was encrypted though so I quickly decrypted it using md5decrypt.net and got the pin, which I entered in my mobile and got the flag.

That's it folks. It was a simple challenge.