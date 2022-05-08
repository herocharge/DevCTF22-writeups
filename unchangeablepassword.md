## UnChangeablePassword

[link](https://clickme.herocharge.repl.co)

This is prolly the most confusing of all the challenges. 

If you follow the link (hehe), you will encounter a login form along with a signup link.

You can create a account and log in to it.  
You will find a link to change your password. Upon clicking you will find a inout box for new password. But doing that just says "invalid request".

I thought i was a problem with the requesting system, so I decided to do a POST request with `curl` and reset the admin password to null.  
The response HTML said Successful Change. When I logged from a browser into admin, It did not seem to work. I left the challenge there and started solving others.  
I came back after sometime and tried the login with admin and it worked this time. Very strange. Not sure what happened. I got the flag directly.