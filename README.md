# multisigner-testbed

There are three different signers, so that we can add and remove signers
continously for a given zone.

The signers are controlled centrally by MUSIC, the Multi-Signer Controller
that implements the algorithms described in dnsop-dnssec-automation (currently
only adding and removing signers from a group).

The signers run BIND 9.19.15 or a later version. This development version has
all the required fixes in order to support the multi-signer algorithms.

There should be three zones at minimum testbed. There may be more zones in the
future if there is a need to test different implementations and/or
configurations.

The zones should be publicly accessible, so that we can add DNSSEC validation
tests. For now, I am going to assume the zones are child zones of 
'multisigner.example.nl'. The zone schema I suggest is:

    <config-label>.<software-label>.multisigner.example.nl.

For example:
- default.bind9.multisigner.example.nl.
- inline-signing.bind9.multisigner.example.nl.
- ksk-zsk.bind9.multisigner.example.nl.
 
This means the testbed requires four different IP addresses. They may be
on the same machine, or may be on their own.

This test does not take into account secondary servers. I also did not yet
include the bump in the wire scenario.

Now for the installation instructions:

The Multi-Signer Controller: See INSTALL.MUSIC
The three BIND 9 servers: See INSTALL.BIND

There are three configuration files: named.conf.1, named.conf.2, and
named.conf.3, the configuration files for the three different BIND 9 servers.

The IP addresses and TSIG credentials are from the ISC's testbed, all local
and dummy values, and should be replaced with the correct addresses and
credentials. Also the zone names should be renamed to the correct domain names.
