CPU microcode
============================

Current releases of AMD and INTEL cpu microcode blobs are available via the following packages:

* [intel-microcode](https://packages.debian.org/de/buster/intel-microcode)
* [amd64-microcode](https://packages.debian.org/buster/amd64-microcode)

By default, hypersolid won't include any microcodes until explicitly selected (controlled by `/etc/default/{intel,amd64}-microcode`).

To add cpu specific microcodes there are two options available

* Use flags within the hypersolid build config (recommended)
* Override the configuraiton files within the rootfs

Build configuration
-------------------------

**Flag `CONF_MICROCODE`**

Vendors to include:

* **intel-amd** - includes AMD + Intel microcodes
* **intel** - only include Intel microcodes
* **amd** - only include AMD microcodes
* **no** - don't include any microcodes (default)

**Flag: `CONF_MICROCODE_INTEL`**

Additional options which are directly passed to [iucode-tool](http://manpages.ubuntu.com/manpages/trusty/man8/iucode-tool.8.html) to select specific cpus by their `CPUID`


### Example ###

File: `config`

```bash
# architecture
CONF_ARCH=amd64

# include intel+amd microcode
CONF_MICROCODE=intel-amd

# atom e38xx - 0x30679
CONF_MICROCODE_INTEL="-s 0x00030679"
```

