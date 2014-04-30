# Pattern Lab Specification v1.0 DRAFT

## Abstract

This specification defines the core functions, organization, and output of Pattern Lab. It is meant to provide authors with insights into how they can meet a minimum-level of functionality when creating ports of Pattern Lab for their own platforms.

## Specification Versioning

This specification is being semantically versioned. Roughly described, major version changes will always represent backwards incompatible changes, minor version changes will always represent new language features and will be backwards compatible, and patch ('tiny') version changes will always be bug fixes.

Pattern Lab implementations SHOULD report the most recent version of the spec (major and minor version numbers). If an implementation has support for any official, optional modules, they SHOULD indicate so with a remark attached to the version number (e.g. "vX.Y, including KSS" or "v.X.Y+KSS"). It is RECOMMENDED that implementations not supporting at least v1.0.0 of this specification refer to themselves as "Pattern Lab-like", or "Pattern Lab-inspired".

## Providing Feedback

If you wish to make comments regarding this document in a manner that is tracked by the Pattern Lab team please submit them via using the specifications issue tracker. All feedback is welcome.

## Table of Contents

<pre>1. Introduction
  1.1. Background
  1.2. Audience
  1.3. Suggested Reading
2. General Functionality
  2.1. Pattern Generation
    2.1.1. Viewer Page
    2.1.2. Style Guide Page
    2.1.3. View All Pages
    2.1.4. Pattern Pages
  2.2. The Viewer
3. Common Infrastructure
  3.1. Core Technologies
    3.1.1 Mustache
      3.1.1.1. File System Loader
      3.1.1.2. Pattern Loader
        3.1.1.2.1. Pattern Paths Configuration
        3.1.1.2.1. Pattern Partial Syntax
        3.1.1.2.2. Style Modifier Syntax
        3.1.1.2.3. Pattern Parameter Syntax
          3.1.1.2.3.1. General Use
          3.1.1.2.3.2. Booleans
          3.1.1.2.3.3. Simple Lists
          3.1.1.2.3.4. listItem Replacement
      3.1.1.3. Using Other Template Engines for Patterns
    3.1.2 Markdown
    3.1.3 JSON
    3.1.4 YAML
    3.1.5 Zip
  3.2. Core Organization
    3.2.1. Atomic Design Not Required
    3.2.2. Source and Public Directories
    3.2.3. Sample Structure
    3.2.4. Configuration
      3.2.4.1. Location
      3.2.4.2. Format
      3.2.4.3. Options
        3.2.4.3.1. ie (Extensions to Ignore)
        3.2.4.3.2. id (Directories to Ignore)
        3.2.4.3.3. ishControlsHide
          3.2.4.3.3.1. Platform-specific Defaults
        3.2.4.3.4. ishMaximum
        3.2.4.3.5. ishMinimum
        3.2.4.3.6. patternEngine
        3.2.4.3.7. patternStates
        3.2.4.3.8. styleGuideExcludes
        3.2.4.3.9. v (Version Number)
        3.2.4.3.10. viewportResizer
    3.2.5. Data
      3.2.5.1. Location
      3.2.5.2. Format
      3.2.5.3. Inheritance
      3.2.5.4. Reserved Keywords
      3.2.5.5. _data.json
        3.2.5.5.1. Default Attributes
      3.2.5.6. _listItems.json
        3.2.5.6.1. Default Attributes
      3.2.5.7. Pattern-Specific Data
        3.2.5.7.1. Naming Convention
    3.2.6. Documentation
      3.2.6.1. Project Documentation
        3.2.6.1.1. Location
        3.2.6.1.2. Format
      3.2.6.2. Pattern Documentation
        3.2.6.2.1. Format
        3.2.6.2.2. Naming Convention
          3.2.6.2.2.1. Example
      3.2.6.3. Annotations
        3.2.6.3.1. Location
        3.2.6.3.2. Format
        3.2.6.3.3. Attributes
        3.2.6.3.4. Example
    3.2.7. Patterns
      3.2.7.1. Location
      3.2.7.2. Format
      3.2.7.3. Naming Convention
        3.2.7.3.1. Example
        3.2.7.3.2. Ordinals
        3.2.7.3.3. Pattern Types
        3.2.7.3.4. Pattern Sub-Types
        3.2.7.3.5. Patterns
        3.2.7.3.6. Pseudo-Patterns
        3.2.7.3.7. Pattern States
        3.2.7.3.8. Hiding Patterns
    3.2.8. System Templates
      3.2.8.1. Viewer Page
        3.2.8.1.1. index.mustache
        3.2.8.1.2. Partials
          3.2.8.1.2.1. ishControls.mustache
          3.2.8.1.2.2. patternNav.mustache
          3.2.8.1.2.3. patternPaths.mustache
          3.2.8.1.2.4. optionals.mustache
          3.2.8.1.2.5. viewAllPaths.mustache
          3.2.8.1.2.6. viewerCode.mustache
          3.2.8.1.2.7. viewerAnnotation.mustache
      3.2.8.2. Style Guide and View All Pages
        3.2.8.1. viewall.mustache
      3.2.8.3. Patterns Additions
        3.2.8.3.1. System-defined
          3.2.8.3.1.1. footer.html
          3.2.8.3.1.2. footer-pattern.html
          3.2.8.3.1.3. header.html
        3.2.8.3.2. User-defined
          3.2.8.3.2.1. _01-footer.mustache
          3.2.8.3.2.2. _00-header.mustache
4. Command Line Input
  4.1. Build Command and Options
    4.1.1. No Cache
  4.2. Fetch Starter Kit Command
  4.3. Snapshot Command and Options
    4.3.1 Default Location for Snapshots
  4.4. Update Command
  4.5. Version Command
  4.6. Help Command
5. Common Output
  5.1. JSON Error Reporting
  5.2. Hashes
    5.2.1. navItems
      5.2.1.1. patternTypes
        5.2.1.1.1. patternTypes Attributes
        5.2.1.1.2. patternTypeItems
          5.2.1.1.2.1. patternSubtypeItems
        5.2.1.1.3. patternItems
      5.2.1.2. Extended Attributes
        5.2.1.2.1. cacheBuster
        5.2.1.2.2. ishControlsHide
        5.2.1.2.3. ishminimum
        5.2.1.2.4. ishmaximum
        5.2.1.2.5. mqs
        5.2.1.2.6. patternpaths 
        5.2.1.2.7. viewallpaths
      5.2.1.3. Example
    5.2.2. patternPaths
      5.2.2.1. Attributes
      5.2.2.2. Example
    5.2.3. patternPartials
      5.2.3.1. Attributes
      5.2.3.2. Example
    5.2.4. patternTypes
      5.2.4.1. Attributes
      5.2.4.2. Example
    5.2.5. patternLineages
      5.2.5.1. Attributes
      5.2.5.2. Example
    5.2.6. patternLineagesR
      5.2.6.1. Attributes
      5.2.6.2. Example
    5.2.7. viewAllPaths
      5.2.6.1. Attributes
      5.2.6.2. Example
    5.2.8. d
      5.2.8.1. _data.json-defined Attributes
      5.2.8.2. System Generated Attributes
        5.2.8.2.1. link
          5.2.8.2.1.1. Attributes
          5.2.8.2.1.2. Example
        5.2.8.2.2. listItems
          5.2.8.2.2.1. Auto-duplication
          5.2.8.2.2.2. Randomization
          5.2.8.2.2.3. Attributes
          5.2.8.2.2.4. Example
        5.2.8.2.3. patternSpecific-defined Attributes
        5.2.8.2.4. cacheBuster
      5.2.8.3. Auto-Replacement of link.some-pattern
  5.3. Viewer Page
    5.3.1. Output Location
  5.4. Style Guide and View All Pages
    5.4.1. Output Location
    5.4.2. Output Naming Conventions
    5.4.3. Appending Pattern Header and Footer
    5.4.4. Partials
    5.4.5. Injected Attributes
      5.4.5.1. patternPartial
      5.4.5.2. lineage
  5.5. Pattern Pages
    5.5.1. Output Location
    5.5.2. Output Naming Conventions
    5.5.3. Appending Pattern Header and Footer
    5.5.4. Additional Exported Items
      5.5.4.1. Pattern HTML
      5.5.4.2. Pattern Mustache
    5.5.5. Injected Attributes
      5.5.5.1. lineage
      5.5.5.2. lineageR
      5.5.5.3. patternPartial
      5.5.5.4. patternState
  5.6. Static Assets</pre>