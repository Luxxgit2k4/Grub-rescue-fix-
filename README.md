# Grub-rescue-fix-
 I have been using Arch linux since a year. This issue occured to me when I deleted the partition directly after installing linux in an old pc with windows 7. I should have checked the boot order before deleting the partition. This issue should have been easier if it was windows 10 and above. The procedure I do to remove linux with the grub in windows 10 doesn't work on windows 7 as there is no suppport for it. I tried this fix it worked well for me.
 
```
ls 

```
This will list the partitions available in the system.It will be listed like
(hd0)  (hd0, msdos1) (hd0, msdos2)  (hd0, msdos3) etc.. It will be based on the number of the partitions you have.

To check in which partition your operating system has been installed use this command 
```
ls (hd0, msdos1) 
```

If you do get like "file system is ext2 or ext3" then that is the partition you are looking for.The ext file is the extended file for linux kernel that's the one you are looking for.

But if you get an error like "(hd0, msdos1) : Filesystem is unknown" that means it is not the partition you are looking for. This means that the linux you are looking for has been completely deleted or forcefully deleted.

Now to know which partition has the operating system you can type the following command
```
set 
```
This will print the partition you are looking for. Like this 

"cmdpath = (hd0)
  prefix= (hd0 msdos4)/boot/grub
  root = hd0,msdos4 "

The partition printed here may also be hidden one which will not be shown while entering "ls" command.

After knowing your partition enter these commands one by one with your respective partition. These commands just print to next line.

```
set boot = (hd0, msdos4)
set prefix = (hd0, msdos4)/boot/grub
insmod normal
```
At last enter this command:
```
normal
```
This command will take you to the grub menu with your listed operating systems.

Hope this helps 
