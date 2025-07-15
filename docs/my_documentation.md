# Yocto Project Documentation

## Reference Documentation (Yocto)

- [Yocto Project Quick Build](https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html)
- [Variables Reference Manual](https://docs.yoctoproject.org/ref-manual/variables.html)
- [OpenEmbedded Layer Index](https://layers.openembedded.org/layerindex/branch/master/layers/)

## Reference Documentation (Raspberry Pi)

- [Raspberry Pi Documentation](https://www.raspberrypi.com/documentation/)
- [RP1 Peripherals Datasheet](https://datasheets.raspberrypi.com/rp1/rp1-peripherals.pdf)
- [Raspberypi Linux Kernel](https://github.com/raspberrypi/linux)

## Flash OS images

- [Balena Etcher](https://github.com/balena-io/etcher/releases/)

## Preliminary Steps

Install required packages:

```bash
sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 python3-subunit zstd liblz4-tool file locales libacl1
```

Set up locale:

```bash
sudo locale-gen pt_BR.UTF-8
```

## Download Poky

```bash
git clone git://git.yoctoproject.org/poky -b scarthgap
```

## Building Software Package Example

```bash
. oe-init-build-env
bitbake dropbear
```

## Cloning Additional Layers

Use [OpenEmbedded Layer Index](https://layers.openembedded.org/layerindex/branch/master/layers/) to pick layers:

```bash
cd poky/
git clone <layer_git> -b <branch_name>
```

## Cooking (bitbake'ing) the Image Recipe

```bash
bitbake core-image-minimal
```

## Serial Communication

```bash
ls /dev/tty*
sudo minicom -s
```

## Limit Cores and Threads

Add to `local.conf`:

```bitbake
BB_NUMBER_THREADS="10"
PARALLEL_MAKE="-j 2"
```

## Cook Application SDK

```bash
bitbake meta-toolchain
```

or

```bash
bitbake meta-toolchain-qt6
```

or

```bash
bitbake meta-toolchain-moz
```

## Install Application SDK

Execute the script from `tmp/deploy/sdk/*toolchain`

## Use the Application SDK

```bash
. /opt/poky/5.0.1/environment-setup-cortexa76-poky-linux
```