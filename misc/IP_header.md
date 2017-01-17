# IP header

Header information at the beginning of an IP packet.

## IPv4
=======

[IPv4](https://tools.ietf.org/html/rfc791) is the fourth version in the development of the Internet Protocol and routes most traffic online. It's a connectionless protocol for use on packet-switched networks, operating on a best effort delivery model.

### IPv4 Header

Consists of 13 required fields and an optional 14th field named *options.*
  * Version: first field in an IP packet (4)
  * Internet Header Length (IHL):
    * number of 32-bit words in the header
    * specifies the size of the data
    * minimum value for field is 5:
      * 5 * 32 bits = 160 bits = 20 bytes
    * maximum value is 15
  * Differentiated Services Code Point [(DSCP)](https://tools.ietf.org/html/rfc2474):
    * originally defined as Type of service (ToS) field.
    * now defined for Differentiated services, like VoIP
  * Explicit Congestion Notification [(ECN)](https://tools.ietf.org/html/rfc3168):
    * allows end-to-end notification of network congestion without dropping packets.
  * Total Length:
    * 16 bit field defines entire packet size including header and data in bytes
    * minimum length is 20 bytes
    * maximum length is 65,535 bytes
  * Identification:
    * primarily used for identifying the group of fragments of a single IP datagram.
  * Flags:
    * 3 bit field used to control or identify fragments
      * bit 0: Reserved; must be zero
      * bit 1: Don't Fragment (DF)
      * bit 2: More Fragments (MF)
  * Fragment Offset:
    * 13 bits long
    * specifies the offset of a particular fragment relative to the beginning of the original unfragmented IP datagram.
  * Time To Live (TTL):
    * 8 bit field prevents datagrams from persisting on an internet
    * limits a datagram's lifetime
  * Protocol:
    * defines protocol used in the data portion of the IP datagram
  * Header Checksum:
    * 16 bit checksum field used for error checking of header
    * if arriving packet does not match router's calculation, the packet is discarded
  * Source address:
    * IPv4 address of packet sender
    * *This may be change in transit by a network address translation device.*
  * Destination address:
    * IPv4 address of packet receiver
    * *This may be change in transit by a network address translation device.*
  * Options:
    * I have no idea what this section means but this is rarely used.

## IPv6
=======

Successor to IPv4, is not backwards compatible, and has a different header layout. 