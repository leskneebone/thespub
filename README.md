# ThesPub – Thesaurus-Friendly Extension to VocPub (Draft)

## Status
This repository is an **early-stage discussion space** for a possible
thesaurus-oriented extension profile building on VocPub and SKOS.
Nothing here is final; everything is open for change.

## Motivation
- VocPub works very well for small, flat, domain vocabularies.
- Richer thesaurus-style vocabularies (deep hierarchies, associations,
multilingual labels) sometimes bump into limitations such as:
- global single `skos:prefLabel`
- mandatory `skos:definition`
- limited or no treatment of `skos:altLabel` and `skos:related` patterns.

ThesPub explores ways to support those use cases **without changing**
VocPub itself, by defining an optional profile that:
- profiles both SKOS and VocPub using W3C PROF,
- reuses VocPub's publishing constraints,
- relaxes some modelling rules, and
- adds thesaurus-friendly recommendations.

## Repository layout
- `docs/` – discussion paper(s) for LDWG and other fora.
- `profiles/` – PROF description of the ThesPub profile.
- `requirements/` – machine-readable requirements register
(e.g., THES-01, THES-02, THES-03…).
- `shacl/` – SHACL shapes that implement the requirements.
- `examples/` – small SKOS vocabularies for testing.

## Getting involved
- Open issues to discuss requirements, shapes, and scope.
- Propose alternatives to the current naming, IRIs, and constraints.
- Suggest additional use cases where a thesaurus-oriented profile
would help.

This work is intended to complement, not replace, VocPub, and to be
shaped collaboratively with interested communities.


graph TD

SKOS["SKOS Ontology\nhttp://www.w3.org/2004/02/skos/core#"]
VOC["VocPub Profile\nhttps://linked.data.gov.au/def/vocpub"]
THES["ThesPub Profile\nhttp://test.linked.data.gov.au/def/thespub"]

REQ["ThesPub Requirements\n(thespub-req.ttl)"]
SHACL["ThesPub SHACL Shapes\n(thespub-shacl.ttl)"]

SKOS --> VOC
VOC --> THES

THES --> REQ
THES --> SHACL

REQ <--> SHACL
