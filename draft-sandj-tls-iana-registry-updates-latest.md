---
title: D/TLS IANA Registry Updates
abbrev: D/TLS IANA Registry Updates
docname: draft-sandj-tls-iana-registry-updates-latest
date: 2016-10-20
category: std
updates: 3749, 5077, 4680, 5246, 5878, 6520, 7301

ipr: trust200902
area: Security
workgroup: TLS WG
keyword: Internet-Draft

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: J. Salowey
    name: Joe Salowey
    organization: Tableau Software
    email: joe@salowey.net
 -
    ins: S. Turner
    name: Sean Turner
    organization: sn3rd
    email: sean@sn3rd.com

normative:
  RFC3749:
  RFC5077:
  RFC4680:
  RFC5226:
  RFC5246:
  RFC5705:
  RFC5878:
  RFC6520:
  RFC7301:
  I-D.ietf-tls-tls13:

informative:
  RFC2434:
  RFC6961:
  I-D.ietf-tls-rfc4492bis:

--- abstract

This document changes the IANA registry policy for a number of registries related to DTLS and TLS, renames some of the registries for consistency, and adds notes to many of the registries.  As a result, this document updates many RFCs (see updates header).

--- middle

Process Note
============

As the authors of this draft are also the WG chairs, the responsible Area Director has agreed to judge consensus.

RFC EDITOR: Please delete section prior to publication.

Introduction
============

This document requests that IANA make changes to a number of DTLS- and TLS-related IANA registries.

In this document, we use the term "(D)TLS" to refer to registries that apply to both TLS and DTLS.

- Add "TLS" to registries' names for consistency with other TLS-related registries.

- Change the IANA registry policy {{RFC5226}} for the TLS ExtensionType Values, TLS Cipher Suite, and TLS ClientCertificateType Identifiers registries.  These more relaxes rules are more condusive to TBD.

- Add the designated expert intructions as a note to the TLS ExtensionType Values, TLS Cipher Suite, and TLS ClientCertificateType Identifiers registries to inform IANA-registry-focused, non-RFC-reading what's expected from the registry.

- Add notes to indicate whether an extension, certain values of an extension, or an entire registry is only applicable pre-(D)TLS 1.3.

- Rename the NewSessionTicket TLS HandshakeType message registry entry {{RFC5077}} to new_session_ticket to match the naming nomenclature for the other Handshake type names and to match with existing implementations.

- Rename the SessionTicket TLS to session_ticket to match the nomenclature for the other extensions' names.

- Add missing entry to the TLS Alert Registry for the no_application_protocol alert defined in {{RFC7301}}

This document proposes no changes to the TLS Alert {{I-D.ietf-tls-tls13}}, TLS ContentType {{I-D.ietf-tls-tls13}}, TLS HandshakeType, {{I-D.ietf-tls-tls13}} and TLS Certificate Status Types {{RFC6961}}; Standards Action, for the 1st three, and IETF Review, for the last, are appropriate for these one-byte code points because of their scarcity.

This document proposes no changes to the EC Curve Type, EC Point Format registries , and Supported Groups Registry (see {{I-D.ietf-tls-rfc4492bis}}).

The lengthy updates header is a result of requests for IANA to refer to this draft in addition to the original RFC that defined a particular registry.

Add "TLS" to Registry Names
===========================

IANA is to update the names of the following registries to add "TLS" to for consistency with the other TLS-related extensions:

- Application-Layer Protocol Negotiation (ALPN) Protocol IDs,
- ExtensionType Values,
- Heartbeat Message Types,
- Heartbeat Modes, and
- Supported Groups.

IANA is also to add a reference to this document for the registry whose names have been updated as a result of the above change.

NOTE: Henceforth in this document the registries will be referred to using the "TLS" prefix.

Aligning with RFC 5226
======================

Many of the TLS-related IANA registries were defined prior to {{RFC5226}} where "IETF Consensus" was used instead of the RFC5226-defined "IETF Review".  To align with the new terminology, IANA is to update to use "IETF Review" in place of "IETF Consensus" in the following registries:

- TLS Authorization Data Formats
- TLS Supplemental Data Formats (SupplementalDataType)

NOTE: Not that this is not a universal change as some registries originally defined with "IETF Consensus" are undergoing other changes either as a result of this document or {{I-D.ietf-tls-rfc4492bis}}.

TLS ExtensionType Values
========================

IANA is to update the TLS ExtensionType Values registry as follows:

- Change the registry policy to:

    Values with the first byte in the range 0-254 (decimal) are assigned via Specification Required {{RFC5226}}.  Values with the first byte 255 (decimal) are reserved for Private Use {{RFC5226}}.

- Update the "References" to also refer to this document.

- Add the following note:

    Note: Experts are to verify that there is in fact a publicly available standard.

TLS Cipher Suite Registry
=========================

IANA is to update the TLS Cipher Suite registry as follows:

- Change the registry policy to:

    Values with the first byte in the range 0-254 (decimal) are assigned via Specification Required {{RFC5226}}.  Values with the first byte 255 (decimal) are reserved for Private Use {{RFC2434}}.

- Add a "Recommended" column to the cipher suite registry.  The cipher suites that follow in the two tables are marked as "Yes". All other cipher suites are marked as "No".

NOTE: The cipher suites that follow are standards track server-authenticated (and optionally client-authenticated) cipher suites which are currently available in TLS 1.2. The notable exception are the ECDHE AES GCM cipher suites which are not yet standards track prior to the publication of this specification, but this document promotes those 4 cipher suites to standards track (see TO-DO insert reference).

~~~
Cipher Suite Name                             | Value
----------------------------------------------+------------
TLS_DHE_RSA_WITH_AES_128_GCM_SHA256           | {0x00,0x9E}
TLS_DHE_RSA_WITH_AES_256_GCM_SHA384           | {0x00,0x9F}
TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256       | {0xC0,0x2B}
TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384       | {0xC0,0x2C}
TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256         | {0xC0,0x2F}
TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384         | {0xC0,0x30}
TLS_DHE_RSA_WITH_AES_128_CCM                  | {0xC0,0x9E}
TLS_DHE_RSA_WITH_AES_256_CCM                  | {0xC0,0x9F}
TLS_DHE_RSA_WITH_AES_128_CCM_8                | {0xC0,0xA2}
TLS_DHE_RSA_WITH_AES_256_CCM_8                | {0xC0,0xA3}
TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256   | {0xCC,0xA8}
TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256 | {0xCC,0xA9}
TLS_DHE_RSA_WITH_CHACHA20_POLY1305_SHA256     | {0xCC,0xAA}
~~~

NOTE: The cipher suites that follow are standards track ephemeral pre-shared key cipher suites which are available in TLS 1.2.  [RFC6655] is inconsistent with respect to the ordering of components within PSK AES CCM cipher suite names; those names are used here without modification.

~~~
Cipher Suite Name                             | Value
----------------------------------------------+------------
TLS_DHE_PSK_WITH_AES_128_GCM_SHA256           | {0x00,0xAA}
TLS_DHE_PSK_WITH_AES_256_GCM_SHA384           | {0x00,0xAB}
TLS_DHE_PSK_WITH_AES_128_CCM                  | {0xC0,0xA6}
TLS_DHE_PSK_WITH_AES_256_CCM                  | {0xC0,0xA7}
TLS_PSK_DHE_WITH_AES_128_CCM_8                | {0xC0,0xAA}
TLS_PSK_DHE_WITH_AES_256_CCM_8                | {0xC0,0xAB}
TLS_ECDHE_PSK_WITH_AES_128_GCM_SHA256         | {TBD}
TLS_ECDHE_PSK_WITH_AES_256_GCM_SHA384         | {TBD}
TLS_ECDHE_PSK_WITH_AES_128_CCM_8_SHA256       | {TBD}
TLS_ECDHE_PSK_WITH_AES_128_CCM_SHA256         | {TBD}
TLS_ECDHE_PSK_WITH_AES_256_CCM_SHA384         | {TBD}
TLS_ECDHE_PSK_WITH_CHACHA20_POLY1305_SHA256   | {0xCC,0xAC}
TLS_DHE_PSK_WITH_CHACHA20_POLY1305_SHA256     | {0xCC,0xAD}
~~~

- Add the following:

    WARNING: Cryptographic algorithms will be broken or weakened over time.  Blindly implementing cipher suites listed here is not advised.  Implementers and users need to check that the cryptographic algorithms listed continue to provide the expected level of security.

    Notes:

    Although TLS 1.3 uses the same cipher suite space as previous versions of TLS, TLS 1.3 cipher suites are defined differently, only specifying the symmetric ciphers, and cannot it be used for TLS 1.2. Similarly, TLS 1.2 and lower cipher suites cannot be used with TLS 1.3.

    Cipher suites marked as "Yes" are those allocated via Standards Track RFCs.  Cipher suites marked as "No" are not; cipher suites marked "No" range from "good" to "bad" from a cryptographic standpoint.

    The designated expert {{RFC5226}} only ensures that the specification is publically available.

TLS ClientCertificateType Identifiers
=====================================

IANA is to update the TLS ClientCertificateType Identifiers registry as follows:

- Change the registry policy to:

    Values in the range 0-223 are assigned via Specification Required {{RFC5226}}.  Values 224-255 are are reserved for Private Use.

- Add the following:

    Note:

    The designated expert {{RFC5226}} only ensures that the specification is publically available.

New Session Ticket TLS Handshake Message Type
=============================================

To align with TLS implementations and to align the naming nomenclature for other Handshake message types, IANA is to rename entry 4 in the TLS HandshakeType registry to "new_session_ticket (renamed from NewSessionTicket)". IANA is to also add a reference to this document in the Reference column for entry 4 in the TLS HandshakeType registry.

Session Ticket TLS Extension
============================

The nomenclature for the registry entries in the TLS ExtensionType Values registry correspond to the presentation language field name except for entry 35.  To ensure that the values in the registry are consistently identified in the registry, IANA is to rename entry 35 to "session_ticket (renamed from "SessionTicket TLS")".

TLS Exporter Label Registry
===========================

IANA is to add the following note to the TLS Exporter Label Registry:

     {{RFC5705}} defines keying material exporters for TLS in terms of the TLS PRF. {{I-D.ietf-tls-tls13}} replaced the PRF with HKDF, thus requiring a new construction. The exporter interface remains the same, however the value is computed different.

Add Missing Item to TLS Alert Registry
===========================================================

IANA is to add the following entry to the TLS Alert Registry (the entry was omitted from the IANA instructions in {{RFC7301}}):

    120   no_application_protocol  Y  [RFC7301]


Orphaned Extensions
===================

To make it clear that (D)TLS 1.3 has orphaned certain extensions (i.e., they are only applicable to version of (D)TLS prior to 1.3), IANA is to add the following to the TLS ExtensionType Values registry:

    Note:

    The following extensions are only applicable to (D)TLS protocol vesions prior to 1.3: truncated_hmac, srp, encrypt_then_mac, extended_master_secret, session_ticket, and renegotiation_info are not applicable to TLS 1.3.

Orphaned Registries
===================

To make it clear that (D)TLS 1.3 has orphaned certain registries (i.e., they are only applicable to version of (D)TLS protocol versions prior to 1.3), IANA is to:

- Add the following to the TLS Compression Method Identifiers registry {{RFC3749}}:

    Note:

    Value 0 (NULL) is the only value in this registry applicable to (D)TLS protocol version 1.3 or later.

- Add the following to the TLS Hash Algorithm {{RFC5246}} and TLS SignatureAlgorithm registries {{RFC5246}}:

    Note:

    The values in this registry are only applicable to (D)TLS protocol versions prior to 1.3.

- Update the "References" in the TLS Compression Method Identifiers, TLS Hash Algorithm {{RFC5246}} and TLS SignatureAlgorithm registries to also refer to this document.

Security Considerations
=======================

TBSL

IANA Considerations
===================

This document is entirely about changes to TLS-related IANA registries.

--- back
