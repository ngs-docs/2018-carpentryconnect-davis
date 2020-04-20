# Let's break Jetstream!

First, run through [booting an instance](https://github.com/ngs-docs/angus/blob/2018/jetstream/boot.md) and click on the [first link](https://use.jetstream-cloud.org/application) that appears .

* Then, login to XSEDE with username `dibtiger` with password `davis9.2018`
* Download and use [this ssh private key to log in](http://teckla.idyll.org/~t/transfer/dibsi2018.pem)
* (the username will be `dibtiger`)

Jetstream's grade will be based on "how many people get a functioning server within 45 minutes?"

If you want a quick demonstration of Jetstream capabilities, we can run through [command line BLAST](https://angus.readthedocs.io/en/2018/running-command-line-blast.html) and [visualizing BLAST score distributions in RStudio](https://angus.readthedocs.io/en/2018/visualizing-blast-scores-with-RStudio.html).

## Connecting in

First, set a password. Using the Web shell or sshing as `dibtiger@<ip address>`, type:

```
sudo passwd dibtiger
```

and enter a password that you will remember. This will be needed for RStudio etc login.

To access RStudio Server, go to (your IP address):8787/
