# tiscamera-capture-image

Bash script for capturing snapshots from The Imaging Source (TIS) camera. It uses [TIS Linux SDK](https://github.com/TheImagingSource/tiscamera), so it has to be installed. Run this script with -h option to detailed information about it.

Feel free to modify this script. More information about TIS SDK can be found on its [GitHub Wiki](https://github.com/TheImagingSource/tiscamera/wiki).

## form-dependencies

This script will form a list of urls to Debian dependencies needed to compile and run The Imaging Source Linux SDK (except GUI tools). It is supposed to be run on a machine without internet connection to obtain the list of packages with versions corresponding to Debian version of this specific machine. Generated list then can be used on a machine with internet connection to download these packages in the following way:

```
$ wget --input-file packages.list
```

After that just move them to target machine and install.

```
# Assuming that all packages are in the same directory
sudo dpkg -i *
```

**NOTE: if a machine that runs this script is not really up-to-date, required package versions may be already removed from repositories. Then wget will not download some of the packages and after you run ```dpkg -i``` you will end up with broken dependencies! Make sure that there are no 404 Not Found errors in wget output.**
