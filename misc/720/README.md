# 720

Challenge Description:

```
These files belong to Lucius. I found them in his flash drive, but I could not open them. 
Can you figure out how to open them? Please avoid opening any unnecessary and dangerous files.
```
After downloading the zip file and unzipping we get several dlls.

Since I'm on linux my go to was to check for strings in them. 
```sh
strings * | grep -i flag
```
I got two instances of ```The Flag You Need.txt```

![1](2020-10-28_22-11.png)

Used grep to get the filenames then ran binwalk on both files to extract anything within them.

```sh
grep -iH 'The Flag You Need.txt' *
```
![2](2020-10-28_22-18.png)

Getting the flag:

![2](2020-10-28_22-16.png)

Flag: RaziCTF{5pl17_4nd_j01n}
