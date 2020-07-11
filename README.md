CAIRO :  As you know "cairo" is an 2D grphics engine that can draw on lots of device context(such as png,PDF,GDI,XLIB and so on)
For more information about cairo please turn to https://www.cairographics.org/

Like most open source repository. cairo source provides a way to build target dll. But On Windows I used Visual Stuido the most. So I search the internet trying to find method to compile cairo with VS(I Used VS2017).


After serval days of testing. I did that. Here is the step:
1.Download necessary files 
		pixman(I used v0.40.0);
		zlib(I used v1.2.11)
		libpng(I used v1.6.37)
		cairo(I used v1.17.2)
		
2.Build pixman to "lib" ,Build zlib to "dll", Build libpng to "dll" 
Notice:libpng came into use zlib and cairo used both zlib and libpng. So if you want to build zlib and libpng to static library, there could cause redefine error. The source of zlib and pnglib provide VS project. However you must pay attention to the compile configuration parameters which make me mad. Keep both "lib" and "dll" in C (extern "C") style interface is very important.

3.Create a Solution with VS and add cairo source file (both C and .h) but you should change some of them.

4.Add additional header file and library form step 2.

5.Build to get cairo.dll
