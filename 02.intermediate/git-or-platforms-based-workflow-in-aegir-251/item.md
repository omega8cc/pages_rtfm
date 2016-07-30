---
# http://learn.getgrav.org/content/headers
title: Git or Platforms based workflow in Aegir?
slug: git-or-platforms-based-workflow-in-aegir-251
# menu: Git or Platforms based workflow in Aegir?
date: 27-01-2013
published: true
publish_date: 27-01-2013
# unpublish_date: 27-01-2013
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
---

Are you trying to set up Git for version control with the BOA system and you are curious if there is any recommended workflow for doing this given that there is only a limited shell access to all of the platforms?

 Before we will go into some details, the most important step is to really understand some Aegir core conceptions and reasoning behind default BOA system configuration and permissions. On the introductory level, “there is an absolute must-read list of articles written by Bill Powell”:http://omega8.cc/library/aegir-basics. Go read them now – many existing Aegir users found them illuminating. Then there is “our own article on Core Conceptions”:http://omega8.cc/compare/conceptions and also a master (index) article you should study – “Managing your code in the Aegir Style”:http://omega8.cc/managing-your-code-in-the-aegir-style-110.

Now, here are some things you may not be aware of, some explained in the recommended above articles, some not, but they are good to know before you will attempt to use Git based workflow.

 1. In the Aegir world you “never manage the code in-place »”:http://bit.ly/UPk1aa — with or without Git.   
 2. All “Website Changes Should Be Tested on a Copy »”:http://bit.ly/XbHmSY — always.   
 3. You can run any Git command when logged in the limited shell.  
 4. You can run “some Git commands also remotely over SSH »”:http://drupalcode.org/project/barracuda.git/blob/HEAD:/aegir/tools/system/conf/lshell.conf#l48   
 5. You can run Git commands only against directories and files you own.  
 6. You should never put full platform in a one repo. It is against entire concept.  
 7. You should never put entire sites/foo.com in a one repo. It will not work.  
 8. There is no write access on the sites/foo.com directory level. Aegir owns it.  
 9. You can’t overwrite modules, themes and libraries directories. Aegir owns them.  
 10. You can overwrite anything only inside these directories.  
 11. It is not possible to use the “Post-Receive Web Hooks »”:https://help.github.com/articles/post-receive-hooks

 As you can see, you may feel rather limited when you are used to just put everything in the same Git repo, probably because your previous hosting provider forced you to manage everything that way. But when you stop for a moment and read some “Aegir Basics”:http://omega8.cc/library/aegir-basics again, you will see that all those built-in BOA restrictions are there only to make your life with Aegir as easy, effective and secure as possible. You do need to figure out (or “click”) how to use Platforms based workflow (and not directly Git based workflow), either semi-manually or with installation profiles, makefiles and only custom code and themes managed in Git and referenced in your makefiles, but the initial effort is well worth it, because you will develop a set of “templates”, both easy to manage, collaborate on with your team and use to speed up your development, while minimizing re-inventing the wheel and repetitiveness when working on new projects/sites.

You may also want to read these helpful articles:

 “How to add custom platform properly?”:http://omega8.cc/how-to-add-custom-platform-properly-140   
 “How to customize built-in platforms?”:http://omega8.cc/how-to-customize-built-in-platforms-252   
 “Migrate sites between installation profiles”:http://omega8.cc/migrate-sites-between-installation-profiles-111   
 “How to export any site properly?”:http://omega8.cc/how-to-export-any-site-properly-241   
 “The best recipes for disaster”:http://omega8.cc/the-best-recipes-for-disaster-139