## Multiple ConceptSchemes permitted

### Requirement

A ThesPub-conformant vocabulary **MAY** contain more than one `skos:ConceptScheme`.

This requirement explicitly relaxes the VocPub constraint that a vocabulary contain *at most one* `skos:ConceptScheme`.

---

### Rationale (non-normative)

VocPub deliberately equates a *vocabulary* with a single validation graph containing exactly one `skos:ConceptScheme`. This choice simplifies tooling, governance, and validation, and remains appropriate for many publishing contexts.

However, in real-world practice, vocabularies are often **composite**:

* a primary or overarching concept scheme
* one or more subsidiary or auxiliary schemes ("little vocabs")
* imported or partially reused schemes that are conceptually distinct but operationally bundled

Forcing each concept scheme into a separate publication unit can introduce unnecessary fragmentation and obscure the intended relationships between schemes.

ThesPub therefore permits multiple concept schemes within a single vocabulary, while placing emphasis on **explicitness** rather than prohibition.

---

### Expectations when multiple ConceptSchemes are present

Where more than one `skos:ConceptScheme` occurs in a ThesPub-conformant vocabulary:

* The roles and relationships between schemes **SHOULD** be made explicit (e.g. via documentation, scheme-level metadata, collections, or other descriptive mechanisms).
* Validators **SHOULD** make their graph-scoping assumptions explicit (e.g. whether validation is applied per dataset, per named graph, or per scheme).
* Publishers **SHOULD NOT** assume that the presence of multiple schemes will be interpreted uniformly across all tools.

ThesPub does not mandate a specific modelling pattern for relating multiple schemes; it requires only that their coexistence not be implicit or accidental.

---

### Relationship to VocPub

ThesPub is an extension profile and does not redefine VocPub’s core assumptions. Instead, it provides an alternative validation posture for use cases where the one-scheme-per-vocabulary constraint is too restrictive.

Implementations that apply ThesPub **MAY**:

* deactivate the VocPub constraint that enforces a single `skos:ConceptScheme`, or
* scope that constraint to individual graphs or schemes rather than to the dataset as a whole.

This design allows VocPub and ThesPub to coexist as complementary profiles addressing different operational and conceptual needs.
