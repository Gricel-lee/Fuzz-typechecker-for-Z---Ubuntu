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

-Clone Fuzz, install Bison, gawk, gcc, flex (https://spivey.oriel.ox.ac.uk/corner/Fuzz_typechecker_for_Z#Installation)
```
git clone https://github.com/Spivoxity/fuzz.git
sudo -i
apt-get dist-upgrade
apt-get install bison -y
sudo apt-get install gawk
apt-get clean
sudo apt install build-essential
gcc --version
sudo apt-get clean

```

However, an error appears. Modify src/absyn.h file to:
```
#define x_given x_slot[0]
#define x_axdef x_slot[0]
#define x_heading x_slot[0]
#define x_schema_body x_slot[1]
#define x_lhs x_slot[0]
#define x_rhs x_slot[1]
#define x_pre x_slot[0]
#define x_def_params x_slot[0]
#define x_def_body x_slot[1]
#define x_args x_slot[0]
#define x_tag x_slot[0]
#define x_params x_slot[1]
#define x_template x_slot[1]
#define x_decls x_slot[0]
#define x_axioms x_slot[1]
#define x_text x_slot[0]
#define x_sref_tag x_slot[0]
#define x_sref_decor x_slot[1]
#define x_sref_params x_slot[2]
#define x_sref_renames x_slot[3]
#define x_sref_line x_slot[4]
#define x_rename_to x_slot[0]
#define x_rename_from x_slot[1]
#define x_decl_names x_slot[0]
#define x_decl_expr x_slot[1]
#define x_ref x_slot[0]
#define x_op x_slot[0]
#define x_rand1 x_slot[1]
#define x_rand2 x_slot[2]
#define x_rand x_slot[1]
#define x_defs x_slot[0]
#define x_body x_slot[1]
#define x_params x_slot[1]
#define x_ref_line x_slot[2]
#define x_number x_slot[0]
#define x_elements x_slot[0]
#define x_factors x_slot[0]
#define x_the_name x_slot[0]
#define x_the_decor x_slot[1]
#define x_the_rename x_slot[2]
#define x_arg x_slot[0]
#define x_field x_slot[1]
#define x_param1 x_slot[1]
#define x_param2 x_slot[2]
#define x_param x_slot[1]
#define x_if x_slot[0]
#define x_then x_slot[1]
#define x_else x_slot[2]
#define x_arg x_slot[0]
#define x_arg1 x_slot[0]
#define x_arg2 x_slot[1]
#define x_bvar x_slot[0]
```

New error:
![image](https://user-images.githubusercontent.com/63869574/154762348-6bea4175-ebdd-481d-8d4f-d6397b739f38.png)


I know the language is C because of _#include <string.h>_ (PS: "<string> is a C++ standard library include, and <string.h> is C standard library include.")
  
![image](https://user-images.githubusercontent.com/63869574/154777445-4e830cce-1d08-40d7-8f49-fa2768530a8c.png)



