# 🔥 FHIR Profile Explorer

An interactive, browser-based tool for exploring FHIR profiles, extensions, value sets, and code systems from Simplifier packages — with full element metadata, differential highlighting, and inline example viewing.

**👉 [Live Demo](https://martinkochdesign.github.io/FHIR_profile_explorer/)**

![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)
![FHIR](https://img.shields.io/badge/FHIR-R4%20%7C%20R4B%20%7C%20R5-orange.svg)

---

## What It Does

The FHIR Profile Explorer lets you visually browse the structure of FHIR Implementation Guide packages (`.tgz` or `.zip` from [Simplifier.net](https://simplifier.net)) overlaid on top of the base FHIR definitions. It provides:

- **Full resource tree** — all elements with cardinality, types, descriptions, and constraints
- **Differential highlighting** — elements constrained by the profile are highlighted in yellow (🟡)
- **Must Support flags** — clearly marked with a green **MS** badge
- **Binding details** — strength (required/extensible/preferred/example) with links to value sets
- **Inline ValueSet & CodeSystem viewer** — click a binding to see all codes without leaving the page
- **Data type exploration** — click any complex type (HumanName, CodeableConcept, etc.) to see its structure in a popup
- **Slicing visualization** — sliced elements and slice names are clearly tagged
- **Example viewer** — syntax-highlighted JSON examples with tabbed navigation
- **Copy FHIR paths** — one-click copy of any element path for use in queries or mappings
- **FHIR version detection** — automatically detects R4, R4B, or R5 from loaded definitions

---

## How to Use

### Step 1: Load the FHIR Base Definitions

1. Download the base `definitions.json.zip` for your FHIR version:
   - [⬇ R4 (4.0.1)](https://hl7.org/fhir/R4/definitions.json.zip)
   - [⬇ R4B (4.3.0)](https://hl7.org/fhir/R4B/definitions.json.zip)
   - [⬇ R5 (5.0.0)](https://hl7.org/fhir/R5/definitions.json.zip)

2. Click **📥 Load FHIR base** and select the downloaded ZIP file.

3. The button will update to show the detected version (e.g., `✅ Base: R4 (4.0.1)`).

### Step 2: Load Your Profile Package

1. Download a FHIR package from [Simplifier.net](https://simplifier.net) (either `.tgz` npm package or `.zip` export).

2. Click **📦 Load profile package** and select the file.

3. The package info bar will show the package name, version, and resource counts.

### Step 3: Explore

- **Search** for profiles, extensions, value sets, or code systems using the search bar.
- **Click** on a profile to see its full element tree.
- **Expand** nodes to drill into the structure.
- **Click ℹ️ Info** on any element to see full details (definition, binding, constraints, mappings).
- **Click type names** (e.g., `CodeableConcept`, `Reference`) to explore data types in a popup.
- **Click binding links** to view ValueSet codes inline.
- **Click 📄 Examples** to see syntax-highlighted JSON examples.

---

## Visual Guide

| Indicator | Meaning |
|-----------|---------|
| 🟡 Yellow row | Element is constrained by this profile (in the differential) |
| 🔴 Red dot | Required element (min > 0) |
| **MS** green badge | Must Support — implementers must handle this element |
| Colored binding dot | Binding strength: 🔴 required, 🟠 extensible, 🔵 preferred, ⚫ example |
| `✂ sliced` tag | Element has slicing defined |
| `slice: name` tag | Named slice |
| `📄` badge | Examples available for this profile |

---

## Technical Details

- **Pure client-side** — no server, no data leaves your browser
- **No installation required** — just open the page
- **Snapshot generation** — automatically merges the profile's differential onto the base definition to produce the full element tree
- **Supports both `.tgz`** (npm FHIR packages) **and `.zip`** (Simplifier project exports)
- **Dependencies** (loaded from CDN):
  - [JSZip](https://stuk.github.io/jszip/) — for ZIP extraction
  - [pako](https://github.com/nodeca/pako) — for gzip decompression of `.tgz` files

---

## Why This Tool?

When working with FHIR Implementation Guides, you often need to:

- Understand what a profile constrains vs. the base resource
- Check which elements are Must Support
- Look up bindings and their allowed codes
- See how slicing is configured
- Review examples for conformance

This tool brings all of that into a single, fast, offline-capable interface — no need to navigate between multiple Simplifier pages or HL7 spec tabs.

---

## Author

**Martin A. Koch, PhD**  
Servei Català de la Salut / CatSalut  
📧 martinandreaskoch@catsalut.cat

---

## License

This project is licensed under the [Apache License 2.0](LICENSE).
