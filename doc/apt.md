# Apt
This is Debian's package configuration tool.

## apt-file
If you are interested in some package and you want to know which files are in there but you won't install it, you can use `apt-file`.

```bash
sudo apt-get install apt-file
apt-file update
apt-file list PACKAGE
```
It's like `dpkg -L PACKAGE` except the package don't need to be installed.
