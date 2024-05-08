#### x64dbg

To install `x64dbg`, we can follow the instructions as shown in its [GitHub Page](https://github.com/x64dbg/x64dbg), and go to the [latest release](https://github.com/x64dbg/x64dbg/releases/tag/snapshot) page, and download the `snapshot_<SNIP>.zip` file. Once we download it in our Windows VM, we can extract the `zip` archive content, rename the `release` folder to something like `x64dbg`, and move it to our `C:\Program Files` folder, or keep it in any folder we want.

Finally, we can double-click on `C:\Program Files\x64dbg\x96dbg.exe` to register the shell extension and add a shortcut to our Desktop.

Note: `x64dbg` comes with two separate applications, one for `x32` and one for `x64`, each under their folder. Clicking on `x96dbg.exe` as noted above will register the version that matches our Windows VM, which in our case is the `x32` one.

Once that's done, we can find the `x32dbg` icon on our Desktop, and we can double-click it to start our debugger: ![x32dbg](https://academy.hackthebox.com/storage/modules/89/win32bof_x32dbg_1.jpg)

Tip: To use the dark theme like the above screenshot, simply go to `Options > Theme` and select `dark`.

#### ERC

To install the `ERC` plugin, we can go to the [release page](https://github.com/Andy53/ERC.Xdbg/releases), and download the `zip` archive that matches our VM (`x64` or `x32`), which in our case is `ERC.Xdbg_32-<SNIP>.zip`. Once we download it to our Windows VM, we can extract its content into `x32dbg` plugins folder located in `C:\Program Files\x64dbg\x32\plugins`.

When that's complete, the plugin should be ready for use. So, once we run `x32dbg`, we can type `ERC --help` in the command bar at the bottom to view `ERC`'s help menu.

To view the `ERC`'s output, we must switch to the `Log` tab by clicking on it or by clicking `Alt+L`, as we can see below: ![ERC Help](https://academy.hackthebox.com/storage/modules/89/win32bof_ERC_help.jpg)

We can also set a default working directory to have all output files saved to, using the following command:

  Debugging Windows Programs

```powershell-session
ERC --config SetWorkingDirectory C:\Users\htb-student\Desktop\
```

Now all of our output should be saved on our Desktop.

---

## Debugging a Program

Whenever we want to debug a program, we can either run it through `x32dbg`, or run it separately and then attach to its process through `x32dbg`.

To open a program with `x32dbg`, we can select `File>Open` or press `F3`, which will prompt us to select the program to be debugged. If we wanted to attach to a process/program that is already running, we could select `File>Attach` or press `Alt+A`, and it will present us with various running processes accessible by our user: ![Attach Process](https://academy.hackthebox.com/storage/modules/89/win32bof_attach_process.jpg)

We can select the process we want to debug and click on `Attach` to start debugging it.