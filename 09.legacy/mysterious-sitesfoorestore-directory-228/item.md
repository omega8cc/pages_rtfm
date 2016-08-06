---
title: Mysterious sites/foo.restore directory
slug: mysterious-sitesfoorestore-directory-228
menu: Mysterious sites/foo.restore directory
date: 02-10-2012
published: true
publish_date: 02-10-2012
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

<a name="debug-q"></a>

QClone or Migrate task fails with error “Failed to extract the contents of (path to backup archive here) to (path to platform here)/sites/foo.restore (The target directory could not be written to)”.

<a name="debug-a"></a>

AThis may happen when there is a hidden copy of the site with the same name you are trying to use for Clone or Migrate, so the first step is to re-Verify the target platform, so Aegir could discover any hidden sites. The site can be hidden when you delete its node in Aegir instead of using Delete task or when some previous task failed to report results to the Aegir frontend – “see this article for reference”:http://omega8.cc/aegir-task-fails-or-spins-forever-126. It is also possible that you didn’t follow “permissions related best practices”:http://omega8.cc/are-there-any-specific-good-habits-to-learn-116 or there was a code/drush error preventing clean rollback without leaving a leftover on the disk. Aegir creates a temporary copy of your site `sites/foo` directory with special name `sites/foo.restore`, so it can use it for automatic rollback when the task, typically Migrate or Clone, fails. If you can’t resolve this by running Verify task on the target platform and you have checked that there is a leftover `sites/foo.restore` in the filesystem, you have to delete it as root (when self-hosted) or submit “Support Request”:http://omega8.cc/support. However, if there is no `sites/foo.restore` leftover in the filesystem, but in fact there is a hidden site with the same name as the site you have tried to Migrate, running Verify task on that platform will not help, because Aegir will not allow you to have two sites with the same name. You have to “Rename”:http://omega8.cc/where-is-the-rename-task-129 the other existing site first, then re-Verify the platform with hidden site, so Aegir will add it to your control panel and then decide what to do – either keep the discovered site or delete it and “Rename”:http://omega8.cc/where-is-the-rename-task-129 the original site back to its correct name, so you can try Migration again.