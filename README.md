# Fuzz-typechecker-for-Z---Ubuntu
Installation of Fuzz typechecker for Z in Ubuntu 20.04

## Do the following commands before starting with Fuzz

Install Cygmin dependencies (not sure if this step is neccesary, https://www.tug.org/texlive/quickinstall.html , http://www.delorie.com/howto/cygwin/fuzz-for-z-install-use-cygwin.html)
```sudo apt-get update -y
sudo apt-get install -y fontconfig-config
sudo apt install ghostscript
sudo apt-get install -y libxaw7-dev
sudo apt-get install libncurses5-dev libncursesw5-dev
```

- Download ![image](https://user-images.githubusercontent.com/63869574/154747372-4e92fff8-9eb3-4477-b40f-2ce43bf834ba.png) from 
https://tug.org/texlive/acquire-netinstall.html
Then (https://www.tug.org/texlive/doc/texlive-en/texlive-en.html#cygwin):
- Unzip and go to folder Then:
```sudo perl /install-tl
sudo apt-get install tcl
```

-Clone Fuzz, install Bison, gawk, gcc (https://spivey.oriel.ox.ac.uk/corner/Fuzz_typechecker_for_Z#Installation)
```
git clone https://github.com/Spivoxity/fuzz.git
sudo -i
apt-get dist-upgrade
apt-get install bison -y
sudo apt-get install gawk
apt-get clean
sudo apt install build-essential
gcc --version
```



