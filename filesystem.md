Filesystem
=====================

**squashfs+tmpfs+overlayfs**

Features
--------------

* The root-filesystem is an immutable, lzo-compressed, readonly **squashfs** image
* A tmpfs is used as rw layer (no persistent storage!)
* The root-filesystem and tmpfs are merged with **overlayfs**
* A persistent storage can be enabled which mounts an additional partition via overlayfs (above the squashfs)
* Filesystem is initialized via a [init-bottom script](../initramfs/scripts/init-bottom/squashfs-tmpfs-overlay) within the initramfs

Persistent Storage
---------------------

Some confguration data, e.g. the ssh host keys need to be generated for each system indidually and requires to be stored on the local system for security reasons. This can be achived by a local filesystem which is mounted **on top** of the immutable image.

File System Stack
------------------------