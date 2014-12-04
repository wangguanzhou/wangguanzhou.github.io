---
layout: post
title: Multipath TCP
category: Notes 
---

A mobile user today would most likely have multiple wireless technologies
available in his device, such as 3G/4G and WiFi. Theoretically he can: <br/>

1. use all available wireless path for the same application to maximize the
throughput; or
2. choose the best link for the time being and switches the traffic between
multiple links without disruptting the application;

However TCP today doesn't allow a connectin to exist on multiple interfaces or
switch between interfaces without dropping appication. This is a typical use
case that mulitpath TCP is invented to help. <br/>

Another typical scenario is the data center where mutiple paths can collide with
each other and don't make an optimal usage of the available bandwidth. Though I haven't
figured out how multipath TCP may help in this scenario. <br/>

In the handshake of MTCP, the host may indicate it's multipath capability to the
server so a Multipath connection can be set up. When a new link/interface is
available the host simply use "SYN JOIN" to add a "subflow" to the existing
connection. <br/>
The TCP header is extended with a subflow sequence in addtion to existing data
sequence so the data loss on a specific link can be detected and retransmitted
on another link. The window management for each subflow and sequence reordering
is pretty much the same as today's TCP. Note that MTCP may exist between
one-pair of IP addresses or multiple addrs. <br/>

In recent Coordinated SIPTO discussion in 3GPP, it was mentioned that MTCP can
be utilized to solve the session continuity issue when the traffic needs to be
moved from one eNB/LGW to another. It may also find some usage in RAN/3GPP
aggregation scenarios. <br/>

There's a good presentation here [MTCP talk in
Youtube](https://www.youtube.com/watch?v=02nBaaIoFWU). It's very long and I
haven't watched the full talk, need to revisit it later on. 


