## Creating Unique Pattern

We can generate a unique pattern with `pattern_create` either in our `PwnBox` instance or right within our debugger `x32dbg` with the `ERC` plugin. To do so in `PwnBox`, we can use the following command:

  Controlling EIP

```shell-session
hidalg0dd@htb[/htb]$ /usr/bin/msf-pattern_create -l 5000

Aa0Aa1Aa2...SNIP...3Gk4Gk5Gk
```

We can now feed this buffer to our program as a `.wav` file. However, it's always easier to do everything in Windows to avoid jumping between two VMs. So, let's see how we can get the same pattern with `ERC`.

If we use the `ERC --help` command, we see the following guidance:

  Controlling EIP

```cmd-session
--Pattern
Generates a non repeating pattern. A pattern of pure ASCII characters can be generated up to 20277 and up to  
66923 if special characters are used. The offset of a particular string can be found inside the pattern by 
providing a search string (must be at least 3 chars long).
    Pattern create: ERC --pattern <create | c> <length>
    Pattern offset: ERC --pattern <offset | o> <search string>
```

As we can see, we can use `ERC --pattern c 5000` to get our pattern. So, let's use this command and see what we get: ![Pattern Create](https://academy.hackthebox.com/storage/modules/89/win32bof_erc_pattern_create_1.jpg)

This pattern is the same pattern we got with the `msf-pattern_create` tool, so we can use either. We can now go to our Desktop to find the output saved to a file called `Pattern_Create_1.txt`. Now we can save the pattern in a `.wav` file and load it into our program. However, to do that, we'll start building our exploit, which we will keep developing and using for other parts of the buffer overflow exploitation process.