# Conan SIP 4.19.25

Used by Ultimaker  Cura.
Tested on Linux, should also work with NMake on Windows. Still very much WIP. Use wit caution.

> **NOTE**  
> No repository yet. If you want to use it to set up the Cura source environment make sure this package
> is available in the local cache.  
 
# Using it
Create the package in your local cache
```bash
git clone https://github.com/jellespijker/conan-sip.git
cd conan-sip
conan create . jellespijker/testing
```

create the conanfile.txt in the repo that should use SIP
```ini
[requires]
SIP/4.19.25@jellespijker/testing

[generators]
cmake_find_package

[options]
```

specifying `cmake_find_package` as generate makes sure that you don't have 
to modify your cmake scripts, for the minor exception of adding the following line:
```cmake
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_BINARY_DIR})
```
This ensures that your find_package will use the Conan generated one.
