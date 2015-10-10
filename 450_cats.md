# 450 Cats

by The Deductive Failures

> I had fun once, it was horrible.

> Password: F3lyn34LifE!

> cats_51474229fe0d9bbd8da500fe3f74b383d175cee1.zip

Aside from taking forever to download, this problem actually wasn't too bad.

Inside the user's home directory, there seems to be a random `catz` file, keylogger program, and a veracrypt installer. `file`ing the catz file didn't help; it just said it was "data". We can confirm that both `logkeys` and `veracrypt` have already been installed on the system.

First I tried to find differences between the logkeys program provided and the actual logkeys program from the internet, but there weren't really any important clues.

After a bit of exploration, I looked at the `logkeys.cc` source, and it seems that the `DEFAULT_LOG_FILE` is at `/var/log/logkeys.log`. Sure enough, there was a `logkeys.log` file inside `/var/log`. So it seems that whoever used this VM before must have already gotten keylogged. Let's take a look at the log file.

```
sudo apt-get install build-essential
wget https://logkeys.googlecode.com/files/logkeys-.01.1a.tar.gz
wget https://logkeys.googlecode.com/files/logkeys-0.1.1a.tar.gz
tar xvzf logkeys-0.1.1a.tar.gz
cd logkeys-0.1.1a/
./configure
make
sudo make install
sudo locale-gen
sudo logkeys -s
sudo gedit ~/.bash_history
cler
clear
veracrypt -t -c
1
/home/cats/catz
128 M
1
2
2
Me0wL3tMeInPl$
Me0wL3tMeInPl$
vyiivyiviparapvraivpyvyrivfyipefiyewyfwvpfiyewvfhnfzslc hvbhawbvklvhbsizbc awhbvua vawenvlfjvba;i vaw;vil;Vbhifvbahvbairk  iwbf irfirryarlhbvlhb ldbdkbvldv hbvhliebalkjverssnsnsr fefj g;ergp; gresgnlsbknbktjsnbkjtnkbjntsjrknblksnljsnb;ojrne orgse;go;egut;siggtibsi lknageosr;gnkjfd,n;ajrngout;fgnbseijrb f,nbs;efvmb gser
```

I have no idea how this keylogger can log keys before it was even started `>.>`. That's pretty scary. Let's ignore that part and look at the more interesting part. Starting from `veracrypt -t -c` it becomes pretty clear how the catz file was created now. Now we can use the veracrypt program to decrypt this volume and get the flag.

```bash
cats@ubuntu:~$ veracrypt --mount catz
Enter mount directory [default]:
Enter password for /home/cats/catz:
```

The password was given in the log file. It's `Me0wL3tMeInPl$`.

```bash
Enter keyfile [none]:
Protect hidden volume (if any)? (y=Yes/n=No) [No]:
Enter your user password or administrator password:
```

The veracrypt program should proceed to mount the catz volume. Inside this volume is a `CATZZZ` folder containing a bunch of pdfs and images. You can use a tool like [this website](http://www.extractpdf.com/) to extract hidden text out of PDFs. The flag was found inside `grooming.pdf`.

## Flag

`{DX5wMM0pCiNwtxf5bEhNscgIFQOWHjNECrp2NYBR}`