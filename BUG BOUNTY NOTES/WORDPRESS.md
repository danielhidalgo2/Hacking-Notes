WPSCAN
wordpress scan

Here are some of the XSS I sent. I have reported more than 20 bugs in one day, some of them were ROOT cases, but how did I find this?

Information Disclosure such as
debug.log
wp - config . php . back
I used WPSCAN to find it here

I also used web.archive to find the XSS. I tested all the parameters. Client Side Template Injection. I used this payload
o'"></script><embed src=:alert(1)>{{constructor.constructor('alert(155555)')()}}

I don't want to talk about how xss works and how Client Side Template Injection works, so search Google for it. I'll just tell you how I found it

If I forgot anything, tell me in the comments