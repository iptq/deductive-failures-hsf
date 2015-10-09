# 500 Whats the Difference

> When you compare this challenge to the others, there is a difference in difficulty.
> whats_the_difference_5338cdcce4f2ec3e2ab4eb97056fc54eae1385ca.zip

This one wasn't as bad as I thought. Obviously, the first thing to do is download the zip and extract its contents. It's just a huge 28KB PNG file. Not suspicious at all :)

The thing is, PNG files have a file signature at the end of the file, and most image viewers won't read beyond that point. The signature goes something like this: `49 45 4E 44 AE 42 60 82`. I found the first instance of that signature somewhere in the middle of the file.

I then took the rest of the file and created a new file, and turns out, it's another PNG with exactly the same picture... almost.

First thing I did was stick both images into ImageJ. Since the problem's called "What's the Difference", I figured you'd need to subtract the images to find something. ...and I got nothing.

