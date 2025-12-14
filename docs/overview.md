# ThesPub Profile & PROF Setup

Working assumption: ThesPub will be identified at a test/staging URI like:

> PREFIX thespub: `http://test.linked.data.gov.au/def/thespub` **Profile IRI**
> PREFIX thesreq: `http://test.linked.data.gov.au/def/thespub#` **Requirement IRI**
> PREFIX thesval: `http://test.linked.data.gov.au/def/thespub/validator` **Validator IRI**
> PREFIX thesshp: `http://test.linked.data.gov.au/def/thespub/validator#` **SHACL Shape IRI**

---

## 1. ThesPub as a PROF Profile

ThesPub should be described as a `prof:Profile` that profiles **both**:

* VocPub (the existing vocabulary publication profile), and
* SKOS (the underlying concept/labels ontology).

```ttl
PREFIX prof:   <http://www.w3.org/ns/dx/prof/>
PREFIX dcterms:    <http://purl.org/dc/terms/>
PREFIX xsd:    <http://www.w3.org/2001/XMLSchema#>
PREFIX thespub: <http://test.linked.data.gov.au/def/thespub#>

thespub:ThesPub
    a prof:Profile ;
    dcterms:title "ThesPub – Thesaurus-Friendly VocPub Extension Profile"@en ;
    prof:isProfileOf <https://linked.data.gov.au/def/vocpub> ;
    prof:isProfileOf <http://www.w3.org/2004/02/skos/core#> ;
    prof:hasToken "thespub" ;
    dcterms:publisher <https://kurrawong.ai/> ;
    dcterms:issued "2099-01-15"^^xsd:date .
```

---

## 2. Resource Descriptors for ThesPub Artifacts

ThesPub will have at least two key artifacts:

1. A SHACL shapes file (constraints/validation).
2. A requirements file (requirement IRIs and metadata), potentially reusing an external requirements ontology.

Example using `prof:ResourceDescriptor`:

```ttl
@prefix role: <http://www.w3.org/ns/dx/prof/role/> .

thespub:ThesPub
    prof:hasResource thesval: ;
    prof:hasResource thesreq: .

thesval:
    a prof:ResourceDescriptor ;
    dcterms:title "ThesPub SHACL Constraints"@en ;
    dcterms:format <https://w3id.org/mediatype/text/turtle> ;
    dcterms:conformsTo <http://www.w3.org/ns/shacl#> ;
    prof:hasRole role:constraints ;
    prof:hasArtifact <http://test.linked.data.gov.au/def/thespub/shapes/thespub-shacl.ttl> .

thesreq:
    a prof:ResourceDescriptor ;
    dcterms:title "ThesPub Requirements Register"@en ;
    dcterms:format <https://w3id.org/mediatype/text/turtle> ;
    prof:hasRole role:requirements ;
    prof:hasArtifact thesreq:thesreq.ttl . # check this!
```

---

## 3. Relationship to VocPub and SKOS

ThesPub is intended to:

* **Extend VocPub**:

  * Retain VocPub's publishing and provenance constraints.
  * Override or relax a small number of modelling constraints (e.g., global single prefLabel; mandatory definitions).
  * Add explicit recognition of `skos:related`, and more thesaurus-friendly expectations around `altLabel`, `broader`, etc.

* **Constrain SKOS usage** for thesaurus-style vocabularies:

  * E.g., "one prefLabel per language tag", rather than "one prefLabel globally".
  * Treat `skos:definition` as recommended rather than strictly required.

---

