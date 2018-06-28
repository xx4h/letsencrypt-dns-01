DNS-01 Validation/Challenge for Letsencrypt
===========================================

To get a web view for README.md of the current HEAD of master: https://git.xx4h.de/xx4h/letsencrypt-dns-01/blob/master/README.md

The Pre and Post Validation Hooks are used, for further information see: https://certbot.eff.org/docs/using.html#hooks

Supported methods
-----------------

* ISPConfig remote API

Installation
------------

```
# Decide where to place your letsencrypt-dns-01
cd /usr/local

git clone https://git.xx4h.de/xx4h/letsencrypt-dns-01

cd letsencrypt-dns-01

# Copy example config (e.g. for ispconfig plugin)
cp plugins/ispconfig/config.ini{.example,}

# Adapt config with your favorite editor (e.g. for ispconfig plugin)
vim plugins/ispconfig/config.ini
```

Usage
-----

```
# To get an certificate for the first time (e.g. for ispconfig plugin)

/usr/local/letsencrypt-dns-01/ispconfig www.example.org

# To renew a certificate the corresponding plugin should have matching -renew command (e.g. for ispconfig plugin
/usr/local/letsencrypt-dns-01/ispconfig-renew www.example.org

# If a plugin has a deploy hook (plugins/PLUGINNAME/deploy), we can reload services if certificates were renewed
/usr/local/letsencrypt-dns-01/ispconfig-renew www.example.org apache2

# To reload multiple services (as we use the certificates in apache and postfix for example), we use a comma separated list
/usr/local/letsencrypt-dns-01/ispconfig-renew www.example.org apache2,postfix
```

Deploy script is only used in PLUGIN-renew, not in the initial getcert.
