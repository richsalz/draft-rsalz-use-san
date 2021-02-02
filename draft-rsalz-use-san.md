---
title: "Use the SAN field"
docname: draft-rsalz-use-san-00
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
updates {{!RFC6125}} to specify that the fall-back techniques of
using commonName attribute to identify the service MUST NOT be used.

# Conventions and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 {{RFC2119}} {{!RFC8174}}
when, and only when, they appear in all capitals, as shown here.

The terminology from {{!RFC6125}} is used here.
Specifically, the following terms and brief definition (as a reminder):

- CN-ID: the Common Name element from a Distingiushed Name.

- DNS-ID, SRV-ID, URI-ID: different types of entries in a subjectAltName
extension.

# The New Rules

The CN-ID MUST NOT be used. The appropriate value in the subjectAltName
extension MUST be used to get the presented identity of the server.

While not discussed in {{!RFC6125}}, this section also implicitly prohibits
the use of the Domain Component or emailAddress RDN's.

The following sections repeat the above rule in other forms, for the purpose
of updating {{!RFC6125}}.

## Designing Application Protocols

Applications should determine which form of name they want to use, and
specify the appropriate subjectAltName extension. Unless there are reasons
to do otherwise, applications SHOULD use the DNS-ID form.

## Representing Server Identity

Severs either MUST NOT issue a CN-ID, or MUST use a form for the Common Name
RDN that cannot be mistaken for an identifier. Not using Common Name is
preferred.

## Verifying Service Identity

When constructing a list of reference identifiers, the client MUST NOT
include any CN-ID present in the certificate. This means that section
6.4.4 of {{!RFC6125}} MUST be ignored.

# Constraints on Wildcards

Wildcard certificates are discussed in section 7.2 of {{!RFC6125}}, which
says that the specifications "are not clear or consistent" about where a
wildcard can appear.

This documents specifies that a wildcard can appear

- only as the left-most label; or
- as the last character in a left-most label

# Security Considerations

The CN-ID, domainComponent, and emailAddress RDN fields are unstructured
free text, and using them is dependant on ordering and encoding concerns.
In addition, their evaluation when PKIX nameConstraints are present is
ambiguous. This document removes those fields from use, so a source
of possible errors is removed.

Because of the ambiguity around wildcards, {{!RFC6125}} mentions that it
is possible to have exploitable differences in behavior. By simplifying
those practices to one rule, this source of errors should be avoided.

All other security considerations of {{!RFC6125}} and its dependant
documents are still relevant.

# IANA Considerations

This document has no IANA actions.

--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
