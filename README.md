---
title: Python pcap file library
---

This is a pcap file reader and writer which doesn't need libpcap.  The
read interface is similar to that of pcapy, but you can do things like
read packets from a StringIO or gzip object.  It handles
different-endian files transparently.

This can also write pcap files, because hey, why not.

To use it:

    >>> import pcap
    >>> p = pcap.open('test.pcap', 'w')     # Create a new file
    >>> p.write(((0, 0, 3), 'foo'))         # Add a packet
    >>> p.write(((0, 0, 3), 'bar'))
    >>> del p
    >>> p = pcap.open(file('test.pcap'))    # Also takes file objects
    >>> (p.version, p.thiszone, p.sigfigs, p.snaplen, p.linktype)
    ((2, 4), 0, 0, 65535, 1)
    >>> [i for i in p]                      # Iterable
    [((0, 0, 3), 'foo'), ((0, 0, 3), 'bar')]
    >>> 

Enjoy.

Version 1.0 is available at
<http://dirtbags.net/g.cgi/py-pcap/snapshot/py-pcap-1.0.zip>

<zephyr@dirtbags.net>
