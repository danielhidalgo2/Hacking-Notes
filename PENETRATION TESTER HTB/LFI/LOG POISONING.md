
## PHP Session Poisoning

Most PHP web applications utilize `PHPSESSID` cookies, which can hold specific user-related data on the back-end, so the web application can keep track of user details through their cookies. These details are stored in `session` files on the back-end, and saved in `/var/lib/php/sessions/` on Linux and in `C:\Windows\Temp\` on Windows. The name of the file that contains our user's data matches the name of our `PHPSESSID` cookie with the `sess_` prefix. For example, if the `PHPSESSID` cookie is set to `el4ukv0kqbvoirg7nkp4dncpk3`, then its location on disk would be `/var/lib/php/sessions/sess_el4ukv0kqbvoirg7nkp4dncpk3`.

The first thing we need to do in a PHP Session Poisoning attack is to examine our PHPSESSID session file and see if it contains any data we can control and poison. So, let's first check if we have a `PHPSESSID` cookie set to our session: ![image](https://academy.hackthebox.com/storage/modules/23/rfi_cookies_storage.png)

As we can see, our `PHPSESSID` cookie value is `nhhv8i0o6ua4g88bkdl9u1fdsd`, so it should be stored at `/var/lib/php/sessions/sess_nhhv8i0o6ua4g88bkdl9u1fdsd`. Let's try include this session file through the LFI vulnerability and view its contents:

   

![](https://academy.hackthebox.com/storage/modules/23/rfi_session_include.png)

**Note:** As you may easily guess, the cookie value will differ from one session to another, so you need to use the cookie value you find in your own session to perform the same attack.

We can see that the session file contains two values: `page`, which shows the selected language page, and `preference`, which shows the selected language. The `preference` value is not under our control, as we did not specify it anywhere and must be automatically specified. However, the `page` value is under our control, as we can control it through the `?language=` parameter.

Let's try setting the value of `page` a custom value (e.g. `language parameter`) and see if it changes in the session file. We can do so by simply visiting the page with `?language=session_poisoning` specified, as follows:

Code: url

```url
http://<SERVER_IP>:<PORT>/index.php?language=session_poisoning
```

Now, let's include the session file once again to look at the contents:

   

![](https://academy.hackthebox.com/storage/modules/23/lfi_poisoned_sessid.png)

This time, the session file contains `session_poisoning` instead of `es.php`, which confirms our ability to control the value of `page` in the session file. Our next step is to perform the `poisoning` step by writing PHP code to the session file. We can write a basic PHP web shell by changing the `?language=` parameter to a URL encoded web shell, as follows:

Code: url

```url
http://<SERVER_IP>:<PORT>/index.php?language=%3C%3Fphp%20system%28%24_GET%5B%22cmd%22%5D%29%3B%3F%3E
```

Finally, we can include the session file and use the `&cmd=id` to execute a commands:

   

![](https://academy.hackthebox.com/storage/modules/23/rfi_session_id.png)

Note: To execute another command, the session file has to be poisoned with the web shell again, as it gets overwritten with `/var/lib/php/sessions/sess_nhhv8i0o6ua4g88bkdl9u1fdsd` after our last inclusion. Ideally, we would use the poisoned web shell to write a permanent web shell to the web directory, or send a reverse shell for easier interaction.

