# Romance Dawn
### 100 Points

### Challenge
Whoops. It seems Luffy played with my picture and I'm not able to open it anymore. Please help me.

### Solution:
I really over thought this one.  Running the file through pngcheck right off will show a bad section with the text "EASY".  I pulled it up in a hex editor and found 4 instances of "EASY".  Pulling up a second png for comparison it was pretty easy to tell that section should be "IDAT".  The others were burried farther in the file and I didn't have any guesses so I ran the file back through pngcheck and it spit out some other sections that were off, but nothing helpful.  

Time to do some learnin'.  Wikipedia helped a little, but the libpng site (http://www.libpng.org/pub/png/book/chapter08.html) helped a lot.  At this point I figured I just needed to figure out what the other png chunks should be called and read up some more to see if I could find anything useful before I just started replacing stuff at random.  While doing that it seemed a little odd that the chunk lengths I kept running into were an even 0x200 (8k).  Then I read png's can have multiple IDAT's that the app creating them can string together in any size it wanted.  Oh...these are all IDAT.  Yeah...that would have been easy if I tried that on a whim right off.  Search replace EASY with IDAT and poof, working image.

### Flag:
shkCTF{7uffy_1s_pr0ud_0f_y0u_0a2a9795f0bdf8d17e4}

# Pain in the ass
### 200 Points

### Challenge
It look's like someone dumped our database. Please help us to know what have been leaked ...

### Solution:

### Flag:


