# 500 Whats the Difference

> When you compare this challenge to the others, there is a difference in difficulty.
> whats_the_difference_5338cdcce4f2ec3e2ab4eb97056fc54eae1385ca.zip

This one wasn't as bad as I thought. Obviously, the first thing to do is download the zip and extract its contents. It's just a huge 28KB PNG file. Not suspicious at all :)

The thing is, PNG files have a file signature at the end of the file, and most image viewers won't read beyond that point. The signature goes something like this: `49 45 4E 44 AE 42 60 82`. I found the first instance of that signature somewhere in the middle of the file.

I then took the rest of the file and created a new file, and turns out, it's another PNG with exactly the same picture... almost. First thing I did was stick both images into ImageJ. Since the problem's called "What's the Difference", I figured you'd need to subtract the images to find something. It turned out to be an empty black image.

I ended up using PIL to subtract the images. My mistake the first time was using a black background, since the difference consisted of a QR code which wouldn't be able to be seen on a black background.

```python
from PIL import Image

im1 = Image.open("bane.png")
im2 = Image.open("bane2.png")

pixels1 = list(im1.getdata())
pixels2 = list(im2.getdata())

imnew = Image.new("RGB", (1831, 2000), "white") # dimensions from the original image

for i in range(len(pixels1)):
	p1 = list(pixels1[i])
	p2 = list(pixels2[i])
	if p1 != p2:
		imnew.putpixel((i % 1831, i // 1831), (p2[0]-p1[0], p2[1]-p1[1], p2[2]-p1[2]))

imnew.save("imnew.png", "PNG")
```

