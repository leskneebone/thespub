## 2. Discussion Paper

### **ThesPub - a thesaurus-friendly extension to VocPUb**

**Exploring a Thesaurus-Oriented Extension to VocPub**
*A discussion paper for the Australian Linked Data Working Group*

### **1. Background**

VocPub (`https://linked.data.gov.au/def/vocpub`) has become a dependable Australian-government profile for publishing SKOS vocabularies, emphasising:

* Provenance and ownership
* Publishing conventions
* Simplicity for small, flat code lists and domain-specific vocabularies

However, thesaurus-style use cases need:

* multilingual preferred terms,
* relaxed requirements for concepts in deeper hierarchies,
* guideance for associative relations,
* and more flexible modelling.

### **2. Observed limitations for thesaurus users**

* **Global single `skos:prefLabel`** makes multilingual preferred labels impractical.
* **Mandatory `skos:definition`** doesn’t reflect real thesaurus practice.
* **Limited treatment of `skos:altLabel`** and omission of `skos:related`.

These are not flaws in VocPub — simply indications that *not all SKOS use cases fit the same mould*.

### **3. Proposed direction: ThesPub**

ThesPub would:

* **Profile both SKOS and VocPub** using W3C PROF.
* **Reuse** VocPub's publishing and provenance constraints.
* **Relax** certain modelling rules.
* **Add** gentle thesaurus-good-practice recommendations.

Candidate IRI: `http://test.linked.data.gov.au/def/thespub`.

Core PROF declaration:

```ttl
prof:isProfileOf <https://linked.data.gov.au/def/vocpub> ;
prof:isProfileOf <http://www.w3.org/2004/02/skos/core#> ;
```

### **4. Requirements as RDF resources**

ThesPub could pioneer:

* Requirement IRIs (`thesreq:THES-01` etc.)
* A small requirement register file
* SHACL shapes that reference these IRIs via `req:fromProvision`

This aligns with modern approaches to machine-readable specification design.

### **5. Illustrative (not final) requirement changes**

* **THES-01:** One prefLabel per language (instead of globally).
* **THES-02:** Definition recommended, not required.
* **THES-03:** Encourage altLabels where appropriate.

These demonstrate the *kind* of refinements ThesPub might introduce.

### **6. Questions for discussion**

1. Is there appetite for an optional thesaurus-oriented profile?
2. Should constraints be modified in VocPub itself or split into a new profile?
3. Is a requirements register useful to others?
4. What level of formalisation is appropriate at this stage?

### **7. Next steps**

* A small GitHub repo exiats containing:

  * This discussion paper
  * Minimal requirements file
  * Minimal SHACL example

* input is invited early so the profile emerges collaboratively.

---

(End of inserted content.)
