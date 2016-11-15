# runtest.py -- Run FreeBSD tests in a VM

`runtest.py` is a `pexpect` script to boot a VM (currently QEMU) with
a FreeBSD kernel and disk image. After boot, the system bootstraps
`pkg`, installs the `kyua` test driver, and runs selected tests. The
test output is exported via a second disk image in `tar` format for
extraction and processing on the host.

Parameters to `runtest.py` are passed by environment variables. The
supported variables are as follows:

Variable | Description | Default
------------ | ------------- | -----------
QEMU_CMD | QEMU emulator to run | `qemu-system-mips`
QEMU_KERNEL | Kernel to boot | `kernel`
QEMU_DISKIMAGE | Filesystem image | `freebsd.img`
TEST_TARBALL | File for output tarball, must be sufficently large to hold results database |
`kyua-out.tar`
TEST_KYUAFILE | Kyuafile for tests to run | `/usr/tests/Kyuafile`
TEST_FILTERS | Test filters | *none*
