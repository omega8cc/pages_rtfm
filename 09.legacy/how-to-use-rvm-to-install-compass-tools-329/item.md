---
# http://learn.getgrav.org/content/headers
title: How to use RVM to install Compass Tools?
slug: how-to-use-rvm-to-install-compass-tools-329
# menu: How to use RVM to install Compass Tools?
date: 14-08-2014
published: true
publish_date: 14-08-2014
# unpublish_date: 14-08-2014
# template: false
# theme: false
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /slug
---

Since we no longer install Compass Tools nor any related gems by default, you need to initialize your account first to auto-install Ruby Version Manager (RVM) and then use @rvm@ to install Compass, Bundler and any other gems required by your theme. Note that  “Bundler allows you to manage different gems versions per theme »”:http://www.trellon.com/content/blog/managing-gems-bundler,  so it is a good idea to use it for gems installation and management, but of course you need to install Bundler first. When you log in your SSH account, you are presented with helpful intro you should read:


          ======== Welcome to the Aegir, Drush and Compass Shell ========
             Type '?' or 'help' to get the list of allowed commands
                 Note that not all Drush commands are available
           Use RVM and Bundler to manage all your Compass gems! Example:
                 `rvm all do gem install --conservative compass`
           To install RVM use control file and re-login after 15 minutes
                     `touch ~/static/control/compass.info`

To initialize your account properly, follow these steps:

1. Create an empty control file: @’touch ~/static/control/compass.info’@  
 2. Log out and wait 15 minutes  
 3. Log in and install Compass: @’rvm all do gem install –conservative compass’@  
 4. Install Bundler: @’rvm all do gem install –conservative bundler’@  
 5. Now either @’cd’@ to your theme and run @’bundle install’@ to add required gems, or  
 6. Continue with installing gems manually, for example:


    $ rvm all do gem install foo_bar
    $ rvm all do gem install --conservative toolkit
    $ rvm all do gem install --conservative --version 3.0.3 compass_radix

<a name="rvm-blue"></a>

»On self-hosted BOA you must add the non-default @CSS@ symbol to the @\_XTRAS\_LIST@ variable in your @/root/.barracuda.cnf@ file and then run @’barracuda up-stable system’@ \*before * initializing RVM in your limited shell account. This step is automated on BOA managed by Omega8.cc

<a name="rvm-red"></a>

!The special, single control file @~/static/control/compass.info@ will enable RVM also in “all extra SSH accounts”:https://omega8.cc/shell-and-ftps-extra-accounts-per-aegir-client-226 on your instance. \*If you delete this file, the system will remove RVM with all gems from all SSH accounts on your Aegir Octopus Instance\*.

<a name="rvm-blue"></a>

»Some gems may require ability to build their native binaries during the install, which is not possible in the limited shell. When you initialize your account to support Ruby Version Manager (RVM), a few known problematic gems will be installed automatically, to limit these problems. If you will get error when attempting to install gems via RVM or Bundler, “please let us know”:https://github.com/omega8cc/boa/issues and we will try to add it to the automatically installed gems exceptions. You can easily check the list of gems you have access to with special @’gem-list’@ command. Note that if you didn’t initialize your account yet, this command may display a legacy list of gems previously installed, but system-wide. You need to initialize your account to stop confusion and see only locally installed Ruby, RVM and gems versions.

<a name="rvm-blue"></a>

»Please note that it is not possible to use Guard in a limited shell via Drush with commands like @’drush omega-guard theme’@, because it is trying to open a sub-shell, which is not going to work with limited shell we provide in BOA. You need to use Guard and Compass tools directly, with commands like @’compass watch’@ or @’guard start’@. Of course you have to install Compass and Guard gems first – they are not installed by default.

<a name="gem-version"></a>

»If the @’bundle install’@ complains that it can’t build native extension for gem @foobar@, but that gem is already installed for you and listed when you type @’gem-list’@, the first step is to compare this gem versions. For example, when RVM has been initialized on your account, it installed some problematic gems which can’t be installed in limited shell: @bluecloth@, @eventmachine@, @ffi@, @hitimes@, @http\_parser.rb@, @oily\_png@ and @yajl-ruby@. However, the version installed may be newer or older than version defined in your theme @Gemfile.lock@ file. To fix the problem, you need to update gem version in that lock file and then run @’bundle install’@ again, or, if you really need a newer version of the problematic gem, you need to re-initialize RVM on your account: delete the control file, wait until @.gem@ and @.rvm@ subdirectories disappear, add the control file again, and proceed with further steps as usual.

<a name="rvm-blue"></a>

»Note that initial RVM install may take 15 minutes or longer, so remember to wait until it is complete and then re-login. Once the initial install is complete, you will be able to run @’rvm –version’@ command, but if it is still not available, you just need to wait a bit longer. It may take even longer if you have extra SSH sub-accounts, because the system needs to install separate RVM along with some problematic gems in every sub-account, so the effective wait time will be multiplied.