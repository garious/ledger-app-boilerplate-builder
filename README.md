In this project we'll create a Linux virtual machine capable of cross-compiling the
Ledger Wallet boilerplate application and then loading it onto Ledger Nano S.

Prerequisites
---

Install Vagrant and VirtualBox.

Clone the `ledger-app-boilerplate` repo into a directory next to the one this README
is in. Do the same with `ledger-app-sia` if you'd like to build that example app as
well.

Download the recommended BOLOS SDK, GCC, and Clang and put them into directories
next to the one this README is in and with names that match what is in `Vagrantfile`.
Alternatively, use `prepare-devenv.sh` script in `ledger-app-boilerplate`, but at
the time of this writing, it downloads a version of GCC that is missing the `gcc`
executable.

Creating the development environment
---

To start the Ubuntu 18.04 VM:

```bash
$ vagrant up
```

To enter the VM:

```bash
$ vagrant ssh
```

Go to the boilerplate app directory:

```bash
$ cd /ledger-app-boilerplate
```

Set the `BOLOS_SDK` and `BOLOS_ENV` environment variables:

```bash
$ export BOLOS_SDK=/bolos-sdk
$ export BOLOS_ENV=/bolos-env
```

Build and load the application

```
$ make load
```

Troubleshooting:

If `make load` fails on `getDongle()`, open `/etc/udev/rules.d/20-hw1.rules` and
add: `OWNER="vagrant"` to each line.

Details are described in:
https://support.ledger.com/hc/en-us/articles/115005165269-Fix-connection-issues

