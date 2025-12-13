# ThesPub Profile & PROF Setup

Working assumption: ThesPub will be identified at a test/staging URI like:

* **Profile IRI**: `http://test.linked.data.gov.au/def/thespub`
* Prefix in examples: `thespub:`

---

## 1. ThesPub as a PROF Profile

ThesPub should be described as a `prof:Profile` that profiles **both**:

* VocPub (the existing vocabulary publication profile), and
* SKOS (the underlying concept/labels ontology).

```ttl
@prefix prof:   <http://www.w3.org/ns/dx/prof/> .
@prefix dct:    <http://purl.org/dc/terms/> .
@prefix xsd:    <http://www.w3.org/2001/XMLSchema#> .
@prefix thespub: <http://test.linked.data.gov.au/def/thespub#> .

thespub:ThesPub
    a prof:Profile ;
    dct:title "ThesPub – Thesaurus-Friendly VocPub Extension Profile"@en ;
    prof:isProfileOf <https://linked.data.gov.au/def/vocpub> ;
    prof:isProfileOf <http://www.w3.org/2004/02/skos/core#> ;
    prof:hasToken "thespub" ;
    dct:publisher <https://kurrawong.ai/> ;
    dct:issued "2025-01-15"^^xsd:date .
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
    prof:hasResource thespub:ThesPubShacl ;
    prof:hasResource thespub:ThesPubRequirements .

thespub:ThesPubShacl
    a prof:ResourceDescriptor ;
    dct:title "ThesPub SHACL Constraints"@en ;
    dct:format <https://w3id.org/mediatype/text/turtle> ;
    dct:conformsTo <http://www.w3.org/ns/shacl#> ;
    prof:hasRole role:constraints ;
    prof:hasArtifact <http://test.linked.data.gov.au/def/thespub/shapes/thespub-shacl.ttl> .

thespub:ThesPubRequirements
    a prof:ResourceDescriptor ;
    dct:title "ThesPub Requirements Register"@en ;
    dct:format <https://w3id.org/mediatype/text/turtle> ;
    prof:hasRole role:requirements ;
    prof:hasArtifact <http://test.linked.data.gov.au/def/thespub/requirements/thespub-req.ttl> .
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

\
