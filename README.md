vox2png
=======
This program was inspired by [this post](https://www.reddit.com/r/gamedev/comments/57x7n3/really_cool_fake_3d_in_gamemaker_by_the_creator/) on /r/gamedev.  
The technique described here not only looks nice, but allows you to do voxel graphics in purely 2D engines (as long as you can do matrix transformations).  
The big downside is that it is an absolute PITA to create assets for, because you need to draw your voxel object layer-by-layer by hand. 

To make this a lot easier I decided to write this program.  
It takes a [MagicaVoxel](http://ephtracy.github.io/) .vox file, and creates a .png sprite sheet from it.
To show you what I mean by that, here are some screenshots:

Source model:
![From this](http://i.imgur.com/O9bU8nE.png)
Resulting sprite sheet:
![To this](http://i.imgur.com/eAYoJAF.png)

Examples of it in action:

(credit goes to /u/Im-German-Lets-Party)  
![screenshot](http://i.imgur.com/iRAElFU.png)
 
(credit goes to /u/Paragania)  
![gifv](http://i.imgur.com/pubmR7n.gif)
 
Building and running
----------------------------
Vox2png doesn't have any dependencies except the C Standard Library (and math.h). Just compile `vox2png.c` with your C compiler, like this:

	gcc vox2png.c -o vox2png -lm

Then you just run it like this:

	./vox2png input.vox output.png
	
Or, if you want to use a special sprite packing mode use this:

	./vox2png input.vox output.png horizontal/vertical/square
	
There is also a mode that gives each sprite cell its own png file:

	./vox2png input.vox output multifile
	
Which produces numbered files for each Z layer, like this: output0.png, output1.png .. outputN.png

If you're using GameMaker you might want your files to be suffixed by `_stripXX`, where `XX` is the amount of sprites in the sheet. This makes it possible to import the files directly into GameMaker. You can do this by typing this:

	./vox2png input.vox output gamemaker
	
Which will produce a file in the form of `output_stripXX.png`, again, where `XX` is the amount of sprites/Z-layers.

If you want to see a certain feature, just ask me and I'll add it. Or, if you know C, it shouldn't be hard to do it yourself.
