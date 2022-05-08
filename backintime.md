# Go Back in Time

[link](https://web.ctf.devclub.in/web/1/)

This was an interesting one.  

My first instinct after seeing the title was the waybackmachine but alas I found nothing there for this particular link.  
Then I visited the website, it said it works only in old windows laptops.

I was a bit startled by this. I was thinking of getting some online windows xp emulator. Tried a few, some were paid then I had the realisation that this is just the first question and prolly is a single command.  

Now how does the website know which OS I'm using. It must be the info I'm sending it. I opened dev tools and looked the requests. It was a GET request and one of the headers contains `user agent` which contains the OS information along with the browser info.  

I certainly looked complicated. It prolly has more info than just OS and browser. But that didnt concern me at the moment and I quickly googled for "windows xp user agent". I used `curl` to do the GET request  
> $ curl -H "User-Agent:\<user-agent-content>"  \<address>

Unfortunately It was not old enough, then I tried windows 95 and it gave the Flag. Sadly I didnot note down my keys so cant show what it was. This was the easiet of all the challenges. 
