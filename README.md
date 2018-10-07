These are the configuration files used for our ejabberd installation that hosts
**jabber.at**, **jabber.zone** and **xmpp.zone**. We use the Debian package
for ejabberd available at apt.jabber.at, please see
https://jabber.at/p/apt-repository/ for more information.

There are two files that are not included in the repository:

* secrets.cfg contains passwords. See secrets.cfg.example for the syntax.
* blocked.cfg contains blocked users. We maintain our own private list.

Feel free to contact us at `chat@conference.jabber.at` for questions.

## Test configuration

You can easily test the configuration using our Docker containers.

First, you have to copy `secrets.yml` and make sure you define all required
macros. Once you're done, you can start ejabberd with a Docker container that
has no networking enabled, to make sure it won't interfere with any real
operations:

```
docker run --rm --network none \
  --mount type=bind,source=`pwd`,target=/etc/ejabberd \
  --name=ejabberd-config-test mathiasertl/ejabberd
```

You can also test ejabberdctl commands (e.g. `ejabberdctl status`) by 
attaching a shell to the container:

```
docker exec -it ejabberd /bin/bash
```

... to kill the container again, use:

```
docker kill ejabberd-config-test
```
