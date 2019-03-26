tstyle
======

*tstyle* is a bash utility that provides a simplified access to some of the `tput` formatting functions.

CLI is great and writing programs or scripts can be really satisfying. Formatting our outputs can help their legibility and improve their quality. However using escape codes directly is awful and can lead to unreadable and ugly hard-coded strings like `\033[31mhello\e[0m, world`.

This little utility is aimed to make output coloring and formatting easy.

Example
-------

*tstyle* can get its input as an argument:

```bash
tstyle -f red "A *tout* le _monde_"
```

or from *stdin* if the argument is missing, so the following is also accepted:

```bash
echo "A *tout* le _monde_" | tstyle -f red
```

and both lead to the same result:

![tstyle-basic-example](https://user-images.githubusercontent.com/3957026/54991123-91cba880-4fbc-11e9-9f63-64c598de6e36.png)

Note that if both *stdin* and argument are provided, *tstyle* will ignore *stdin*.

Usage
-----

`-h` or `--help` will give you a complete usage instructions:

![tstyle-help](https://user-images.githubusercontent.com/3957026/54990775-d0ad2e80-4fbb-11e9-9a0d-dabc9bc80680.png)

By default *tstyle* will print its argument with a trailing `\n`, you can use the `-n` option to avoid this behavior.

Of course special characters can be escaped so `tstyle "hello, \*world\*"` will print `hello, *world*`.

The `-b <color>` and `-f <color>` will add a background and foreground color for the entire output, so multiple colors means multiple *tstyle* calls.

Exit Status
-----------

Normal execution will terminate with `0` exit code, the same of `printf` which is called to print the output.
If the parameter of `-b` or `-f` options is an invalid color or is missing, the script will print an error message to *stderr* and terminate with `1` status code.
If the script is called with invalid parameters the help message will be printed to *stderr* and the exit status will be `64`.
