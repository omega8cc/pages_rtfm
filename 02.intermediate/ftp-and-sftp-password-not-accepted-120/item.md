---
# http://learn.getgrav.org/content/headers
title: FTP or SFTP password not accepted?
slug: ftp-and-sftp-password-not-accepted-120
# menu: FTP or SFTP password not accepted?
date: 26-06-2011
published: true
publish_date: 26-06-2011
# unpublish_date: 26-06-2011
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

<a name="debug-q"></a>

QMy FTPS and SFTP password no longer works, but I didn’t change it, so what happened and how to avoid this issue in the future – is it possible to use SSH keys maybe?

<a name="debug-a"></a>

AFor FTP please make sure you are using FTPS (FTP over SSL) with explicit TLS mode and port 21 and not plain FTP. Please log in via SSH and change your password if it expired. This may be the reason you can’t log in via FTPS/SFTP. As explained in your welcome e-mail, your password needs to be changed every 3 months or it will expire every 90 days. To update your password, please log in via SSH and use command @’passwd’@. Here is how to fix this if you forgot to change the password before it expired:

\# Open Terminal app on your computer and type: `ssh your.login.ftp@your.server.ip`  
 # It will prompt for SSH key (unless you have used SSH before) – just accept.  
 # Now it will prompt for your last used password – enter it.  
 # Finally it should prompt you for the password change.  
 # Type existing and new password, confirm – done.

<a name="debug-b"></a>

!To get to the prompt where the server will ask you to update your password in step #4, you have to attempt to log in with correct, last working (albeit expired) password in step #3. You will never see that prompt, if you continue to enter wrong password in step #3. \*If you don’t remember your last working password and that password expired, you will not be able to use this procedure. Instead, “please file a ticket”:https://omega8.cc/support with request for password reset procedure\*. Note: the last working password is probably different than the password from your welcome email, unless you have never updated the initial password, so please don’t confuse them.

<a name="debug-b"></a>

!We recommend to “set up SSH keys »”:http://www.ece.uci.edu/~chou/ssh-key.html to be able to log in via SFTP or SSH without your password. \*Note that SSH keys are not a substitute for password policy, and will not override expired passwords. You will need to reset your password (as shown above) according to our policy, even if you use SSH keys\*.

<a name="debug-c"></a>

!\*Make sure that permissions are correct both on the ~/.ssh directory and the authorized\_keys file, when you set up SSH keys * — @chmod 600 ~/.ssh/authorized\_keys@ and @chmod 700 ~/.ssh@ — You can check and fix them also via FTPS if needed.