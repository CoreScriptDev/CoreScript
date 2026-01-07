# CHANGELOG

### [v0.1]
**14.12.25**

> Initial Commit
> Added syntax (see builds/v0.1/README.md)

---

### [v0.2]
**16.12.25**

> Added some features (see builds/v0.2/README.md)

---

## [v0.3]
**29.12.25**

> Added csx - CoreScript Extension Manager
> - Accessable with the following command:

> ```bash
> CoreScript csx install <username>/<repo>/<path> -p <provider>
> ```

> Providers accepted:
> - GitHub (std.)
> - GitLab

> Local install:
> ```bash
> CoreScript csx install <path/to/extension> -p local
> ```

---

## [v0.3.1]
**07.01.26**
> - **WE FINALLY GOT AN ICON!**
>
> <img src="icon.png" width="96">
>
> <hr style="border-top: 1px dashed #aaa">
>
> Updated CSX System:
> - Extensions are now packaged in '.cscext' files. They can now also contain multiple CoreScript source files.
> - You can pack them using
> ```bash
> corescript csx pack <source-dir>
> ```
>- This will pack your source dir into an '.cscext' file which you can find in your working directory.
>
> - How to install extensions remains the same, except that you now specify the exact path to the '.cscext' file (with/without suffix).

---