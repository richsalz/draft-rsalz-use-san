---
title: "Use the SAN field"
docname: draft-rsalz-use-san.md
category: std

ipr: trust200902
area: Security
workgroup: TBD Working Group
keyword: Internet-Draft

stand_alone: yes
smart_quotes: no
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: R. Salz
    name: Rich Salz
    organization: Akamai Technologies
    email: rsalz@akamai.com

normative:
  RFC2119:
  RFC6125:

informative:

--- abstract

In the decade since {{!RFC6125}} was published, the subjectAltName
extension, as defined in {{!RFC5280}} has become ubiquitous.  This document
updates {{!RFC6125}} to specify that the fall-back techniques of
using commonName attribute to identify the service MUST NOT be used.

--- middle

# Introduction

In the decade since {{!RFC6125}} was published, the subjectAltName
extension, as defined in {{!RFC5280}} has become ubiquitous.  This document
updates {{!RFC6125} to specify that the fall-back techniques of
using commonName attribute to identify the service MUST NOT be used.


# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 {{RFC2119}} {{!RFC8174}}
when, and only when, they appear in all capitals, as shown here.

# Security Considerations

TODO Security

# IANA Considerations

This document has no IANA actions.

--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
