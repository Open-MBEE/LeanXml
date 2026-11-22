# LeanXml

XML support for Lean. This was removed from Lean core as it was not needed upstream. I have copied the code here for use by myself and others.

## Writing XML

`Lean.Xml.Element.toXml` (in `LeanXml/Serializer.lean`) writes an `Element` as well-formed XML 1.0: character data and attribute values are escaped, and `Lean.Xml.parse` reads the result back to the same tree. It returns a `SerializeError` for a tree XML cannot represent: a name that is not an XML name, a character outside the XML character range, or a comment that contains `--`, ends with `-` or holds a carriage return. `toString` on an `Element` is unchanged and escapes nothing.

Tests are in `LeanXmlTest/` and run with `lake test` (and with `lake build`).
