# 200 Back to Base6

> back_to_bas6_c193aba53f9ee0841371cc86324a2b4d87f1a4ee.zip

When we download an extract the zip, we get a `release.txt` with the following contents.

```
ZmxhZ3tp
745f7761735f
104 105 115 95 102 108
011000010110011101011111011011010111001001011111
NNZGCYTTL4======
<~Blm^+@<5dnF_tSDEaNs,0OK)ZI/~>
```

The name of the problem implies that we'll be dealing with different bases. This problem will go really quickly if you can recognize them already.

### ZmxhZ3tp

Most likely base64, since it's got both uppercase and lowercase letters and numbers. This part decodes to `flag{i`. Looks like we'll have to add all of the parts together.

### 745f7761735f

Definitely hex. I just used [this website](http://www.rapidtables.com/convert/number/hex-to-ascii.htm) to decode it from hex. The result is `t_was_`.

### 104 105 115 95 102 108

It's decimal. They even separated it for you. This part decodes to `his_fl`.

### 011000010110011101011111011011010111001001011111

Binary. Since it's 48 characters long, there's 8 characters per byte, so it's 6 characters long, just like the previous parts. This binary part decodes to `ag_mr_`.

### NNZGCYTTL4======

I thought this was base64 again, but they wouldn't pull something like that. I looked up all the bases that used = in their characters, and turns out it's base32. This part decodes to `krabs_`.

### &lt;~Blm^+@&lt;5dnF_tSDEaNs,0OK)ZI/~&gt;

OK I have no clue what this thing is. I ended up going on Google and literally typing in every number from 1-9 to see if there were common bases. Did you know that there was a base85? I didn't. This part decodes to `it_was_numb3r_un0_y0}`.

## Flag

`flag{it_was_his_flag_mr_krabs_it_was_numb3r_un0_y0}`