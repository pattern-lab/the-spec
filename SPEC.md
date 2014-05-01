# Pattern Lab Specification v1.0 DRAFT

## Abstract

This specification defines the core functions, organization, and output of Pattern Lab. It is meant to provide authors with insights into how they can meet a minimum-level of functionality when creating ports of Pattern Lab for their own platforms.

## Specification Versioning

This specification is being semantically versioned. Roughly described, major version changes will always represent backwards incompatible changes, minor version changes will always represent new language features and will be backwards compatible, and patch ('tiny') version changes will always be bug fixes.

Pattern Lab implementations SHOULD report the most recent version of the spec (major and minor version numbers). If an implementation has support for any official, optional modules, they SHOULD indicate so with a remark attached to the version number (e.g. "vX.Y, including KSS" or "v.X.Y+KSS"). It is RECOMMENDED that implementations not supporting at least v1.0.0 of this specification refer to themselves as "Pattern Lab-like", or "Pattern Lab-inspired".

## Providing Feedback

If you wish to make comments regarding this document in a manner that is tracked by the Pattern Lab team please submit them using the [specification issue tracker](https://github.com/pattern-lab/the-spec/issues). All feedback is welcome.

## Table of Contents

<pre>1. Introduction
  1.1. Background
  1.2. Audience
  1.3. Suggested Reading
2. General Functionality
  2.1. Pattern Generation
    2.1.1. Style Guide Page
    2.1.2. View All Pages
    2.1.3. Pattern Pages
  2.2. The Viewer page
3. Technologies
  3.1. Mustache
    3.1.1. File System Loader
    3.1.2. Pattern Loader
      3.1.2.1. Pattern Paths Configuration
      3.1.2.1. Pattern Partial Syntax
      3.1.2.2. Style Modifier Syntax
      3.1.2.3. Pattern Parameter Syntax
        3.1.2.3.1. General Use
        3.1.2.3.2. Booleans
        3.1.2.3.3. Simple Lists
        3.1.2.3.4. listItem Replacement
    3.1.3. Using Other Template Engines for Patterns
  3.2. Markdown
  3.3. JSON
  3.4. YAML
  3.5. Zip
4. File System Organization
  4.1. Atomic Design Not Required
  4.2. Source and Public Directories
  4.3. Sample Structure
  4.4. Configuration
    4.4.1. Location
    4.4.2. Format
    4.4.3. Options
      4.4.3.1. ie (Extensions to Ignore)
      4.4.3.2. id (Directories to Ignore)
      4.4.3.3. ishControlsHide
        4.4.3.3.1. Platform-specific Defaults
      4.4.3.4. ishMaximum
      4.4.3.5. ishMinimum
      4.4.3.6. patternEngine
      4.4.3.7. patternStates
      4.4.3.8. styleGuideExcludes
      4.4.3.9. v (Version Number)
      4.4.3.10. viewportResizer
  4.5. Data
    4.5.1. Location
    4.5.2. Format
    4.5.3. Inheritance
    4.5.4. Reserved Keywords
    4.5.5. _data.json
      4.5.5.1. Default Attributes
    4.5.6. _listItems.json
      4.5.6.1. Default Attributes
    4.5.7. Pattern-Specific Data
      4.5.7.1. Naming Convention
  4.6. Documentation
    4.6.1. Project Documentation
      4.6.1.1. Location
      4.6.1.2. Format
    4.6.2. Pattern Documentation
      4.6.2.1. Format
      4.6.2.2. Naming Convention
        4.6.2.2.1. Example
    4.6.3. Annotations
      4.6.3.1. Location
      4.6.3.2. Format
      4.6.3.3. Attributes
      4.6.3.4. Example
  4.7. Patterns
    4.7.1. Location
    4.7.2. Format
    4.7.3. Naming Convention
      4.7.3.1. Example
      4.7.3.2. Ordinals
      4.7.3.3. Pattern Types
      4.7.3.4. Pattern Sub-Types
      4.7.3.5. Patterns
      4.7.3.6. Pseudo-Patterns
      4.7.3.7. Pattern States
      4.7.3.8. Hiding Patterns
  4.8. System Templates
    4.8.1. Viewer Page
      4.8.1.1. index.mustache
      4.8.1.2. Partials
        4.8.1.2.1. ishControls.mustache
        4.8.1.2.2. patternNav.mustache
        4.8.1.2.3. patternPaths.mustache
        4.8.1.2.4. optionals.mustache
        4.8.1.2.5. viewAllPaths.mustache
        4.8.1.2.6. viewerCode.mustache
        4.8.1.2.7. viewerAnnotation.mustache
    4.8.2. Style Guide and View All Pages
      4.8.1. viewall.mustache
    4.8.3. Patterns Additions
      4.8.3.1. System-defined
        4.8.3.1.1. footer.html
        4.8.3.1.2. footer-pattern.html
        4.8.3.1.3. header.html
      4.8.3.2. User-defined
        4.8.3.2.1. _01-footer.mustache
        4.8.3.2.2. _00-header.mustache
5. Command Line Input
  5.1. Build Command and Options
    5.1.1. No Cache
  5.2. Fetch Starter Kit Command
  5.3. Snapshot Command and Options
    5.3.1. Default Location for Snapshots
  5.4. Update Command
  5.5. Version Command
  5.6. Help Command
6. Output
  6.1. JSON Error Reporting
  6.2. Hashes
    6.2.1. navItems
      6.2.1.1. patternTypes
        6.2.1.1.1. patternTypes Attributes
        6.2.1.1.2. patternTypeItems
          6.2.1.1.2.1. patternSubtypeItems
        6.2.1.1.3. patternItems
      6.2.1.2. Extended Attributes
        5.2.1.2.1. cacheBuster
        5.2.1.2.2. ishControlsHide
        5.2.1.2.3. ishminimum
        5.2.1.2.4. ishmaximum
        5.2.1.2.5. mqs
        5.2.1.2.6. patternpaths 
        5.2.1.2.7. viewallpaths
      6.2.1.3. Example
    6.2.2. patternPaths
      6.2.2.1. Attributes
      6.2.2.2. Example
    6.2.3. patternPartials
      6.2.3.1. Attributes
      6.2.3.2. Example
    6.2.4. patternTypes
      6.2.4.1. Attributes
      6.2.4.2. Example
    6.2.5. patternLineages
      6.2.5.1. Attributes
      6.2.5.2. Example
    6.2.6. patternLineagesR
      6.2.6.1. Attributes
      6.2.6.2. Example
    6.2.7. viewAllPaths
      6.2.6.1. Attributes
      6.2.6.2. Example
    6.2.8. d (Data hash)
      6.2.8.1. _data.json-defined Attributes
      6.2.8.2. System Generated Attributes
        6.2.8.2.1. link
          6.2.8.2.1.1. Attributes
          6.2.8.2.1.2. Example
        6.2.8.2.2. listItems
          6.2.8.2.2.1. Auto-duplication
          6.2.8.2.2.2. Randomization
          6.2.8.2.2.3. Attributes
          6.2.8.2.2.4. Example
        6.2.8.2.3. patternSpecific-defined Attributes
        6.2.8.2.4. cacheBuster
      6.2.8.3. Auto-Replacement of link.some-pattern
  6.3. Viewer Page
    6.3.1. Output Location
  6.4. Style Guide and View All Pages
    6.4.1. Output Location
    6.4.2. Output Naming Conventions
    6.4.3. Appending Pattern Header and Footer
    6.4.4. Partials
    6.4.5. Injected Attributes
      6.4.5.1. patternPartial
      6.4.5.2. lineage
  6.5. Pattern Pages
    6.5.1. Output Location
    6.5.2. Output Naming Conventions
    6.5.3. Appending Pattern Header and Footer
    6.5.4. Additional Exported Items
      6.5.4.1. Pattern HTML
      6.5.4.2. Pattern Mustache
    6.5.5. Injected Attributes
      6.5.5.1. lineage
      6.5.5.2. lineageR
      6.5.5.3. patternPartial
      6.5.5.4. patternState
  6.6. Static Assets</pre>