# 450 Cats

> I had fun once, it was horrible.

> Password: F3lyn34LifE!

> cats_51474229fe0d9bbd8da500fe3f74b383d175cee1.zip

Aside from taking forever to download, this problem actually wasn't too bad. Inside the user's home directory, there seems to be a random `catz` file, keylogger program, and a veracrypt installer. We can confirm that both of these programs have already been installed on the system. I'm also guessing that the veracrypt program was used to create the catz file, but we have no information on that.



After a bit of exploration, I looked at the `logkeys.cc` source, and it seems that the `DEFAULT_LOG_FILE` is at `/var/log/logkeys.log`. So it seems that whoever used this VM before must have already had their keys logged.