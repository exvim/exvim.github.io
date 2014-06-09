---
layout: docs
title: Build Your Distribution
---

## Build Your Distribution for Mac and Linux 

Create `~/exvim` directory in your computer and clone [exvim/main](http://github.com/exvim/main) 
from github. 

```bash
# in your ~/exvim/main run:
cd ~/exvim/
git clone http://github.com/exvim/main
```

go to the path `~/exvim/main`

```bash
cd ~/exvim/main/
```

Edit and run the shell file `dist/package.sh`, **NOTE:** you should check and confirm the version number
in `dist/package.sh` before you run it. 

```bash
sh dist/package.sh
```

You will get the distribution in `~/exvim/build/`

## Build Windows installer

You must prepare the following folders and copy them to `c:\dev\exvim\build` for installer.

 - DejaVuSansMono
 - exvim-{{version}}
 - graphviz
 - tools
 - vim74

Once you have the folders above, run gen-installer.iss in `exvim/main/dist` through Inno Setup.
