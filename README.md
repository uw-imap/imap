# University of Washington IMAP toolkit
This repository is a copy of the University of Washington IMAP toolkit _(imap-2007f.tar.gz/MD5:2126fd125ea26b73b20f01fcd5940369)_ which has become unavailable from the documented FTP and mirror sites. Posted here for both posterity and because a number of packages require the library and source/headers which may not always be suitable from the OS package manager.

_In my case it was to compile PHP7 with IMAP support and utilizing an alternative (newer) OpenSSL version. It was very difficult to find trustworthy already-patched sources for this purpose._ This seems to be a common problem for many in the same situation.

## imap tools and server, c-client/libc-client/uw-imap-devel
The sources have been incrementally patched with the following from the Fedora Package Sources for uw-imap[[1]]. 
See the [_patches_](supplemental/patches) directory in this repository for the contents.

- 1006_openssl1.1_autoverify.patch
- imap-2004a-doc.patch
- imap-2007e-authmd5.patch
- imap-2007e-overflow.patch
- imap-2007e-poll.patch
- imap-2007e-shared.patch
- imap-2007e-system_c_client.patch
- imap-2007f-format-security.patch
- imap-2007f-ldflags.patch

Additional information is available at https://www.washington.edu/imap/

[1]: https://src.fedoraproject.org/rpms/uw-imap/tree/f29

## ORIGINAL [README](./README)
    /* ========================================================================
     * Copyright 1988-2007 University of Washington
     *
     * Licensed under the Apache License, Version 2.0 (the "License");
     * you may not use this file except in compliance with the License.
     * You may obtain a copy of the License at
     *
     *     http://www.apache.org/licenses/LICENSE-2.0
     *
     * 
     * ========================================================================
     */

                   IMAP Toolkit Environment
                         4 April 2007
                     Mark Crispin


                    UNIX QUICK BUILD NOTES

    These quick build notes assume that you have installed OpenSSL before
    attempting to build this software, and that you do not have any non-default
    configuration parameters.

    If you need additional information in building this software with OpenSSL,
    please refer to the docs/SSLBUILD file for more information.

    If you intend to build this software with a non-default configuration
    (including building a non-compliant server without SSL support), please
    refer to the docs/BUILD file for more information.

    1) Look in the top-level Makefile and find your system type code.  For example,
       modern versions of Linux will use either "slx", "lnp", or one of the
       lnp-variants (such as "lrh").

    2) Type "make" followed by the system type, e.g. "make slx".

    3) Install the POP2 daemon (ipopd/ipop2d), the POP3 daemon (ipopd/ipop3d), and
       the IMAP daemon (imapd/imapd) on a system directory of your choosing.

    4) Update /etc/services to register the pop2 service on TCP port 109, the
       pop3 service on TCP port 110, and the imap service on TCP port 143.  Also
       update Yellow Pages/NIS/NetInfo/etc. if appropriate on your system.

    5) Update /etc/inetd.conf (or install files on /etc/xinetd.d) to invoke the
       POP2, POP3, and IMAP daemons on their associated services.

    6) If your system uses PAM authentication, be sure to set up /etc/pam.d/imap
       (*not* /etc/pam.d/imapd) and /etc/pam.d/pop (*not* /etc/pam.d/ipop3d or
       /etc/pam.d/pop3d or /etc/pam.d/popd or /etc/pam.d/pop3).

    7) Unless you built your system without SSL support, you will need to set
       up SSL server certificates as described in docs/SSLBUILD.

    6) That's all!

    Read the file docs/BUILD and docs/SSLBUILD if you need more detailed
    information and/or you don't understand these quick build instructions.
    
                     MISCELLANEOUS NOTES

         mtest has been run under UNIX, DOS, Windows, NT, Macintosh, TOPS-20, and
    VMS.  It is a very primitive interface, however, and is suited mainly as a
    model of how to write a main program for c-client.  You should take a look at
    the source to figure out how to use it.  Briefly, it first asks for a mailbox
    name (either a local file path or an IMAP mailbox in the form
    "{hostname}mailbox") and then puts you in a command mode where "?" will give
    you a list of commands.

         Pine is available separately on the FTP.CAC.Washington.EDU archives.

         The focus of development and support is for UNIX and Win32 (including
    Windows 95/98/Millenium, Windows NT, and Windows 2000).  The other ports are
    not frequently used or tested, and may be incomplete.
