# 400 Graphic

> Your parents told you to never wander in Middle Earth by yourself.
> nc 54.152.31.35 1337
> graphic_4a241880e4f2a244ee97913d946cbf943fc18d5a.zip

Upon unzipping the file, you get a single binary. After using retdec to decompile to C, inspecting the decompiled code finds several variables of a struct_0 pointer type. The struct struct_0 was defined as follows:
```c
struct struct_0 {
    int32_t * e0;
    int32_t e1;
    int32_t * e2;
};
```
The main function starts by fgets'ing the input into a char pointer str. Several cryptic variables are declared and a loop starts. In the loop, a set of if/elses check whether the next character is 'L', 'R', NULL, or something else. For the next section, the parenthesized variable names are given for clarity. The actual processes are just convoluted messes of variable casts and assignments, but a quick inspection boils them down to the following.

In the case of an R or L, a certain int (v0) is produced from a struct_0 pointer (v1) and another int (v2) was set to an element in the struct_0 (v1->e1). The way v0 is obtained is different for the L and R cases. A third int (v3) is then set to itself xor v2. Then v0 is set to v1. Since v0 is then an element of a struct, and is casted again to a struct_0 pointer in the next iteration, we determined struct_0 to be a node of a graph, with two links to other nodes, accessed thru an L or an R.

If str was any other character, v3 is xor'ed with v2, which undoes the previous xor on v3, since xor is a self-inverse, i.e. A xor B xor B == A.

Following this, we created a map of all of the 'items' that you can find, which is actually just the value of v2, or the int that becomes the pointer for the next struct. We called where an item occurred a 'room', and referred to v2 as the room number.

![graphic.jpg](files/graphic.jpg)

The next step is to find how to get the 'value' to 0x764c648c, which is the condition for get_password() to be called. Looking through the program, it turns out that our 'value' is v3, and it gets xor'ed with the room number every iteration. After some fiddling around, we found a list of rooms that had an 'xor sum' of 0x764c648c:
0x8badf00d
0xdeadc0de
0xdeadfeed
0xfee1dead
0xfaceb00b
0x743029ab
0x11111112
0x42424242
0x0

LxRLLxRRLxLxRLxRRxLxLxLxLxLL

## Flag

`flag{th3r3_and_b4ck_again}`
