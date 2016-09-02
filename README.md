# ansible-win-copy-alternative
Example demonstrating alternative to Ansible win_copy


This project came about due to seeing really slow performance 
with the win_copy module in Ansible. 


I researched and found a number of improvements were made in
recent updates.  However, even after the updates, it was taking 
over 3 minutes to transfer 24 small text files across the local 
network. 

While watching the debugging, I found the setup time for each 
transfer was taking a long time. This gave the idea of using a 
compressed package to reduce the overhead to a single transfer. 

This project demonstrates the changes. 

The sample directory has 9 empty files.  


Using the native win_copy on the directory gives:
```
===============================================================================
Copy directory to remote system --------------------------------------- 131.08s
setup ------------------------------------------------------------------ 12.12s
```


Using a single compressed package gives:
```
===============================================================================
Copy single compressed package ----------------------------------------- 16.19s
setup ------------------------------------------------------------------ 11.00s
Extract on the remote system -------------------------------------------- 8.54s
Clean up temp-package.zip ----------------------------------------------- 8.43s
Compress directory to send in a package --------------------------------- 0.21s
```

