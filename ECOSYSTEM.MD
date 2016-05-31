# Pattern Lab Ecosystem Specification v2.0 DRAFT

## Abstract

This specification defines the core pieces that make up the Pattern Lab ecosystem. It is meant to provide authors with insights into what pieces need to be supported so they can meet a minimum-level of functionality when creating ports of Pattern Lab for their own platforms.

## Specification Versioning

This specification is being semantically versioned. Roughly described, major version changes will always represent backwards incompatible changes, minor version changes will always represent new language features and will be backwards compatible, and patch ('tiny') version changes will always be bug fixes.

Pattern Lab implementations SHOULD report the most recent version of the spec (major and minor version numbers).It is RECOMMENDED that implementations that DON'T SUPPORT at least v2.0.0 of this specification refer to themselves as "Pattern Lab-like", or "Pattern Lab-inspired".

## Providing Feedback

If you wish to make comments regarding this document in a manner that is tracked by the Pattern Lab team please submit them using the [specification issue tracker](https://github.com/pattern-lab/the-spec/issues). All feedback is welcome.

## Ecosystem Parts

### Core
The core logic for Pattern Lab and implements Pattern Lab Core Spec v2.0.

### PatternEngines
PatternEngines are responsible for parsing patterns. They allow for customization of templates and better integration of patterns with production systems. Currently their is no spec associated with PatternEngines.

### StyleguideKits
StyleguideKits are the front-end of Pattern Lab. AKA "the viewer." StyleguideKits allow developers to develop custom layouts to show off their patterns. Currently their is no spec associated with StyleguideKits.

### StarterKits
StarterKits are a set of patterns, data, and static assets that form the base of a project. Currently their is no spec associated with StarterKits.

### Plugins
Plugins are combinations of functionality that expand on Core, PatternEngines, StyleguideKits and/or StarterKits. Currently their is no spec associated with Plugins.

### Editions
Editions provide a way for users to develop bundles of functionality related to Pattern Lab that support their needs. An Edition may combine Core with a specific Pattern Engine, StyleguideKit, custom StarterKit, and a myriad of unique plugins. An Edition could also contain task runners and other tools that are outside the Pattern Lab ecosystem.
