---
title: "Learning About Linux Permissions"
date: 2023-02-03T11:56:14-06:00
draft: false
slug: "learning-about-linux-permissions"
---

So, who knows what's a good pace for writing blog posts, but since I'm in the habit of writing up notes about new things I learn, might as well write a post even though I already put one up earlier today.

# Permissions
So, I've got this website running on a linux server which serves this out of a directory `/var/www/onlymattjohnson.com` which is owned by the **www-data** group. I was trying to upload the files by ftp for my user but I found that I couldn't write to the folder. So, I figured the folder is owned by **www-data** let's add myself to that group.

```
> sudo usermod -a -G www-data <my_username>
```

Now I'm in the group but still having issues writing. Turns out linux permissions are to the owner, group members of the owner, and then everyone else. Whoopsie. I need to give this whole group writing permissions.

```
> chmod g+w /var/www/onlymattjohnson.com
```

Once that was done, everything is working according to plan. If this page is up, I think we did it correctly.

