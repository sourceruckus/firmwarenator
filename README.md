Firmwarenator - a magical machine-specific fw.img creator
=========================================================

Copyright 2021-2022 Michael D Labriola <veggiemike@sourceruckus.org>

Licensed under the GPLv3. See the file COPYING for details. 

Firmwarenator is a utility for creating a fw.img file containing all the
firmware required for the host system.

**NOTE**: This depends on having the "Loading firmware from %s" printout
enabled in the kernel (e.g., add `dyndbg='func fw_get_filesystem_firmware
+fmp'` to kernel commandline) and the kernel ring buffer being fresh enough to
still have that output available.

**NOTE**: And that all depends on already having a bootable system w/ an
uptodate `/lib/firmware` directory, at least temporarily.

Get the latest and greatest from https://github.com/sourceruckus/firmwarenator.

<pre>
usage: firmwarenator IMGNAME

  -h, --help                Show this help message and exit.

  -V, --version             Show version string and exit.

  -v, --verbose             Display extra output

  -f, --force               Force overwrite existing file.

  -c, --compressor COMP     Use COMP compressor in pipeline during archive
                            creation.  Valid compressors are 'gzip', 'bzip2',
                            'xz', 'zstd', or 'none'.  Default is 'zstd' w/
                            --compressor-args of -T0 -10.  If COMP is specified
                            as 'none', no compressor is used.

  -C, --compressor-args ARGS  Pass ARGS into the specified compressor.  If
                              --compressor was specified, defaults to empty
                              string.  Otherwise, default is '-T0 -10' to go
                              along with the default zstd compressor.  Can be
                              provided multiple times, causing argurments to be
                              appended (i.e., becaue you cannot have spaces in
                              ARGS).

  -s, --sqsh                Instead of building a cpio archive suitable for
                            appending to initrd, build a squashfs image.  This
                            can be used by the initrd to supply firmware during
                            the early stages of boot.  It's arguably better
                            than the cpio method (assuming you're using an
                            initrd generated using ruckusrd), because you don't
                            have to recreate your initrd after updating
                            fw.sqsh.
</pre>
