---
title: TITLE
slug: URI
menu: MENU
date: 08-08-2016
published: true
visible: true
taxonomy:
    category: docs
routes:
    aliases:
        - /URI
---

Aegir Clients: Adding SSH/FTPS Users to Your Drupal Sites

One of the great strengths of Aegir is that you get the power to
manage all your Drupal sites in one place. But what if you need to let
another user access _some_ of the sites? The solution is simple: add
an Aegir *client*.

h2. What Can an Aegir Client Do?

An Aegir client can access and manage one or more sites, and _only_
those sites. You, the admin, control which sites each client can
access. All other sites remain completely hidden from that client.

This management has two aspects:

* Managing sites via the *Aegir control panel*, running
Aegir tasks like "Backup", "Migrate", and so on.

* Using *SSH* (a "limited Secure Shell":limited-shell) or *FTPS* (FTP over SSL) to
  access files and run @drush@.

h2. What Can't an Aegir Client Do?

An Aegir client can't access any sites that it doesn't own. A client
always moves and acts within a particular site or sites.

This means that an Aegir client also can't work at the higher level of
Aegir "platforms":platform. Only an admin can work with platforms.

How does Aegir enforce these restrictions?

When someone logs into the Aegir panel as a client (technically, as
we'll see in a moment, a _user_ with only the "aegir client" role), he
or she only sees the sites owned by this client. The other sites don't
appear, and neither does the "Platforms" menu tab.

When this person uses SSH with the client credentials, he or she lands
in a sparse "home" directory with one visible symbolic link: @sites/@.
And @sites/@ shows only the directories for the sites which this
client owns. As a client, you'll never see @sites/all/@, only the
@sites/foo.com/@ directory for each site.

These restrictions protect the other sites on the platform. If a
person makes mistakes, they're confined to the sites owned by this
client.

h2. The "User" and the "Client"

Adding an Aegir client is easy, but you need to understand that you're
really adding two, _separate_ things: an Aegir _user_ and an SSH/FTPS
_client_.

The _user_ can log in to Aegir and run Aegir tasks. An Aegir user
basically feels like a Drupal user. You change the password on the
"Edit account" page, users have roles, users can be blocked, and so
on.

The actual _client_ can use SSH or FTPS. An Aegir client is very
different from a Drupal user; it is unique to Aegir. A client is
basically a username and password, and Aegir generates this password
automatically (see below).

h3. Many Users, One Client?

When you create a client in Aegir, Aegir tries to keep things simple
by automatically creating both the client and an associated user with
the same @Internal name@ and the (aptly named) "aegir client" role. If
you just need to let someone access a site, this will work fine.

However, because these things are separate, you have options. You can
attach several users to the same client, so they all SSH in with the
same credentials to access the same set of sites. Since a site can
only be owned by a single client, you'll need to share this client if
multiple people need access.

On the other hand, if a single user needs access to multiple clusters
of sites, you can associate multiple clients to that user (see below).

Even if you never plan to use this complexity, you need to understand
this difference between _user_ and _client_ so that you don't get
confused.

h3. Manage "Clients"?

For instance, when you click "Manage Clients" in the Administration
menu, you're actually taken to a listing of Drupal _users_, not
clients.

Aegir does not currently provide a page where you can view a list of
clients. However, when you edit a site's @Client@ field (see below),
and begin to type a client name, Drupal will attempt to finish it with
autocomplete.

h2. How to Add an Aegir Client on Omega8cc

The concepts may be complex, but actually adding a client is easy. On
the Aegir admin panel, look at the "Administration" menu in the bottom
right. Click "Add Client".

Enter the human-readable @Client name@, the machine-readable @Internal
name@ (no spaces or metacharacters), and the @Email address@ (twice).

Technically, you can leave the @Internal name@ blank and let Aegir
generate it from the @Client name@.

h3. Include an Email to Also Create a User

What about the email? If you leave the email blank, Aegir will _not_
create an Aegir control panel user, but _will_ create the SSH/FTPS
client. (This client is only created if you're on an Octopus Satellite
Instance, such as your Omega8cc account.)

To repeat: if you want both a user and a client, include an email. If
you only want a client, leave the email blank.

If you think about it (for awhile), this actually makes sense. The
Aegir user corresponds to a human being, while the client is more of a
set of credentials. Only humans have email addresses.

h2. Let Clients Own Your Sites

Now that you have a client, it's time to own some sites. This is easy
too.

Edit the site node. ("Add Sites" -> click your site in the listing ->
"Edit".)

Enter your client in the @Client@ field. The default owner is @Aegir@.
Start to type the client name, and Drupal should autocomplete it.

 *Never leave @Client@ blank.* If you could do this, _all_ users would
  have access to the site in the Aegir admin panels! Fortunately, you
  can't. Aegir will prevent you from saving the site with no client,
  or an invalid client name.

When you save the site node, Aegir will run the Verify task.

h3. Find the Client Password

As the site is verified, Aegir generates a new password for this
client. The new password is placed in a file in @~/users/@.

The name of this file is also important: it's the actual SSH/FTPS
username for this client. This username is the @Internal name@ you
entered for this client, prepended by a seemingly random string, which
you'll quickly recognize as your beloved Omega8cc user ID.

Don't forget to actually send this username and password to whoever
will need it.

h3. Change the Client Password

If you ever need to change the password, just delete this file in
@~/users/@. Within five minutes, Aegir will generate a new file with a
new password.

Remember, the Aegir users are separate from the clients. _Users_ can
change their own passwords as they would in Drupal, on their own "Edit
account" pages.

h3. Deleting a Client

What if you want to remove a client entirely? Edit each site this
client owns, and set @Client@ to another client, or back to "Aegir".

h3. Owners and Users

An Aegir site can have only one owner. (Of course, users with the
"admin" role can still access any site.)

If you need more than one human to access the site, don't worry. This
is why the "client" is decoupled from the "user". Multiple users can
share the same client.

Or, if you need one person to access multiple clusters of sites, that
single user can be associated with multiple clients.

To add or remove clients from a user, click "Manage clients" in the
lower-right Administration menu, find the username, and click @edit@
on that row. Below the expected email and password fields, you'll see
"Associate a client to this user." It's another autocomplete field;
just start typing the client field.

You can only add one client at a time, so if you need to associate
multiple clients, save the node and edit it again.

Don't forget that a single client can own multiple sites. This makes
it easy to manage a cluster of sites that belong to a particular
person or group.

h2. Final Tips on Aegir Clients

A few more notes and potential gotchas:

* Client accounts _cannot_ use SFTP (FTP over SSH), for security
  reasons.

* If you use FTPS (FTP over SSL), set "Explicit TLS mode" and port 21
    in your FTPS software.

* Client SSH accounts have @drush@ enabled by default.

* When people use clients to manage site files, they should remember
    to "set group writable permissions":group-writable to any files they upload with
    @chmod 775@.

* All files and directories in all sites are reset to be owned by your
  main SSH account every morning.

* Remember, clients cannot access platforms. If you need multiple
developers to have a higher level of access, consider creating (when
self-hosted) or purchasing (when hosted) separate Octopus/Aegir
instances.

[drush]link

[platform]link

[group-writable]link

[limited-shell]link
