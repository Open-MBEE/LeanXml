# LeanXml

XML support for Lean. This was removed from Lean core as it was not needed upstream. I have copied the code here for use by myself and others.

## Namespaces

The parser is not namespace-aware: an `Element` has the names written in the document, and
`xmlns` declarations are ordinary attributes. `LeanXml.Namespace` resolves them per
[Namespaces in XML 1.0](https://www.w3.org/TR/xml-names/):

```lean
open Lean.Xml in
#eval do
  let root ← parseResolved "<t:a xmlns:t='urn:u' xml:lang='en'/>"
  return (root.is (some "urn:u") "a", root.attribute? (some xmlNamespace) "lang")
-- Except.ok (true, some "en")
```

Tests are `#guard`s in `LeanXmlTest/`; `lake test` (or `lake build`) checks them.
