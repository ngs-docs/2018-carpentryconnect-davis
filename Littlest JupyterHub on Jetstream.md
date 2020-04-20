# Littlest JupyterHub on Jetstream

titus 7/1/18

Wouldn't it be nice to have a multiuser JupyterHub running on Jetstream? Why yes it would!

Yuvi wrote about his [The Littlest JupyterHub](http://words.yuvi.in/post/the-littlest-jupyterhub/) project, and so I decided to try it out. tl;dr? It mostly just works!

1. Log in to [the jetstream portal](https://use.jetstream-cloud.org/application/) with username `dibtiger` and password `davis9.2018`, booted an m1.medium with the DIBSI 2018 image as per [Let's Break Jetstream!](https://hackmd.io/vRPE9TZQTNG1_Z2WPbqXhw?view).

2. Run this as per [quickstart instructions](https://github.com/yuvipanda/the-littlest-jupyterhub):

```
curl https://raw.githubusercontent.com/yuvipanda/the-littlest-jupyterhub/master/installer/install.bash | sudo bash -
```

ALSO SEE: [the documentation!](https://the-littlest-jupyterhub.readthedocs.io/en/latest/tutorials/quickstart.html)

Note, got this warning --

```
+ /opt/tljh/hub/bin/python3 -m tljh.installer
twisted 17.5.0 has requirement Automat>=0.3.0, but you'll have automat 0.0.0 which is incompatible.
```

but everything worked!

## Success!

I could go to port 80 and log in with `dibtiger` and my passwd and then I got a functioning Jupyter console!

And if I go to `/user/dibtiger/lab` instead of `/user/dibtiger/tree` I get JupterLab!

### Problems/issues:

The only challenge that really needs to be addressed to install this on a bootable image is that Jetstream by default creates a user account with your XSEDE username, but *without* a functional password.  So, for example, I used the `dibtiger` account with XSEDE password  `70K6sjNS!co6qbeM`, and Jetstream created a running system with username `dibtiger` but no password. I think Upendra and I should brainstorm about this. Or maybe [the First Use Authenticator](https://github.com/yuvipanda/jupyterhub-firstuseauthenticator) is the right solution?

We should figure out if we can set up https with letsencrypt or somethin'? Right now it's running on http.

Finally, we should provide some `useradd` instructions (or whatever we are supposed to do to add users) for people who want to use this for a class. I tried `useradd testy` and the server failed to spawn for that user, even though it was added automatically to group `jupyterhub-users`. halp?

...where are the logs, anyway?

## Other Notes

tljh installed its own conda, so you can run:

```
sudo /opt/tljh/hub/bin/conda
```
to install stuff.

