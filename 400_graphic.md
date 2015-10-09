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
The main function starts by fgets'ing the input into a char pointer str. Several cryptic variables are declared and a loop starts. In the loop, a set of if/elses check whether the next character is 'L', 'R', NULL, or something else. If the next character was R or L, a certain int was cast to a struct_0 pointer and another variable was set to an element in the struct_0. The actual process is more of a convoluted mess of variable casts and assignments, but 

LxRLLxRRLxLxRLxRRxLxLxLxLxLL

![graphic.jpg](files/graphic.jpg)


## Flag

`flag{th3r3_and_b4ck_again}`
