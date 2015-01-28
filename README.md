Random English Town Names
=========================
This is the NML source code for the NewGRF "Random English Town Names" which I
have published to the BaNaNaS online content repository for download through
OpenTTD.

Compiling by hand
=================
You will first need to install [Python 2](http://www.python.org), either via your package manager or by downloading something from the website. If you are using a version prior to 2.7.9 you will also need to install [pip](https://pip.pypa.io/en/latest/installing.html) somehow.

Once you have done that, execute the following commands. Unix and Linux users will have to add the `--user` flag to install to their home directory.

```
pip install pillow
pip install nml
```

If you now run `nmlc` you will be greeted with a stack trace. At time of writing, NML still has a dependency on the defunct Python Imaging Library. There is a community-supported fork called Pillow, but a small API difference results in NML failing. Locate the nml package (on Unix and Linux, it is in `$USER/.local/lib/python2.7/site-packages/nml`). Find the line `import os, Image` in the files `actions/real_sprite.py` and `ast/alt_sprites.py`, and replace it with `import os; from PIL import Image`. In `main.py`, replace `import Image` with `from PIL import Image`. (This requirement will be lifted when [this issue is resolved](http://dev.openttdcoop.org/issues/7419).)

After that, building the GRF is a oneliner.

```
nmlc random_english_town_names.nml
```

If you want you can package the GRF file with the documentation into a .tar, as I did when I uploaded it to BaNaNaS - but if you're going to all that trouble, why not just download it from inside OpenTTD through the online content window?
