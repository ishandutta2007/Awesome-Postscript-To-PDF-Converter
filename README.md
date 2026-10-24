# Awesome-Postscript-To-PDF-Converter

## Top PostScript to PDF Converter Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Ghostscript-Powered Conversion, Distiller Parameter Compatibility & Self-Hosted Batch Pipelines*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **PostScript to PDF Conversion**. These tools transform `.ps` and `.eps` files into Portable Document Format — preserving vector graphics, embedding fonts, and applying Distiller-compatible settings for print, prepress, and archival output — with a spectrum running from commercial printer drivers to command-line Ghostscript wrappers that power most of the open-source ecosystem.

**Examples** include Ghostscript, ps2pdf, Aspose.Page FOSS, and pstoedit (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, batch conversion, and Distiller-compatible parameter control — especially relevant as **Ghostscript 10.08.0** is the current release and **ps2pdf scripts are documented work-alikes for nearly all Adobe Distiller functionality** [citation:2][citation:11].

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **Adobe Acrobat Distiller** — **The reference commercial PostScript-to-PDF engine.** Converts `.ps` files to PDF with precise control over font embedding, image compression, color management, and PDF/X compliance. **Included with Adobe Acrobat Pro subscriptions**. **Best for print production workflows** where Distiller's specific job options and PDF/X presets are contractual requirements, accepting subscription cost and Windows/macOS dependency.

- **novaPDF** — **The commercial virtual printer with PostScript input support.** Converts documents to PDF via a printer driver with profiles for different output needs. **One-time purchase or subscription**. **Best for Windows users** wanting a GUI-driven converter with printer-driver convenience, not for Linux or batch automation.

## Open-Source GitHub Projects

- **Ghostscript** — **The engine underneath almost every open-source PostScript-to-PDF tool.** Dual AGPL/Proprietary licensed, **10.08.0** released September 2026 [citation:2]. **A document conversion and rendering engine** written in C, essential to the Linux printing pipeline, with a massive range of output devices and extreme control over color management [citation:6]. **Handles PostScript, PDF, PCL, and XPS** with the `pdfwrite` device performing the actual PDF generation. **Security posture has hardened significantly** — recent releases added device selection protection from PostScript input, made internal procedures `executeonly`, and removed dangerous non-standard operators [citation:15]. **The honest caveat**: **the command-line interface is not user-friendly** — you need to know the right flags (`-sDEVICE=pdfwrite`, `-o output.pdf`, `-dPDFSETTINGS=/prepress`) and understand Distiller parameter mappings [citation:3]. **Best for scripting, batch conversion, and any workflow needing maximum control** over the PDF output.

- **ps2pdf** — **The standard Ghostscript wrapper scripts for Distiller-style conversion.** Ships with Ghostscript, with four variants: `ps2pdf12` (PDF 1.2, Acrobat 3+), `ps2pdf13` (PDF 1.3, Acrobat 4+), `ps2pdf14` (PDF 1.4, Acrobat 5+), and `ps2pdf` (currently PDF 1.4, may change) [citation:11]. **"Work-alikes for nearly all the functionality (but not the user interface) of Adobe's Acrobat Distiller"** — converts PostScript files to PDF with access to the same options as `gs(1)` [citation:11]. **Supports stdin/stdout piping** for filter-style integration, and **accepts Distiller parameters** for controlling conversion, including PDF/X and PDF/A generation [citation:3][citation:11]. **Example**: `ps2pdf -dPDFSETTINGS=/prepress figure.ps proof.pdf` [citation:3]. **Best for anyone wanting Distiller-compatible conversion** without learning Ghostscript's full command surface — the scripts handle the common cases.

- **Aspose.Page FOSS for Python** — **The pure-Python PostScript/EPS/XPS processing library.** **26.9.0** (September 2026), with **`PsDocument`** for reading and converting PS/EPS files to PDF [citation:4]. **`to_pdf(options)`** method converts PostScript documents to PDF, with **`PdfWriter`** and **`PdfSaveOptions`** for controlling compression and font handling [citation:4]. **MCP tools** include `ps_to_pdf(input, output, options=None)` and `eps_metadata(input)` for AI-agent-driven conversion [citation:4]. **Includes a full port of the Vatti polygon-clipping algorithm** for clip-path handling [citation:4]. **The honest limitations**: **does not read existing PDF files** (no PDF import/parsing API), and **PS/EPS raster output falls back to pure Python when skia-python isn't installed** [citation:4]. **Best for Python developers** wanting PostScript conversion inside their application without shelling out to Ghostscript, accepting that it's a newer library with a narrower scope.

- **pstoedit** — **The PostScript/PDF to vector formats converter with Ghostscript as a prerequisite.** **Converts PostScript and PDF files into various other formats supported by drawing editors** — it requires Ghostscript to be installed (binary installation is sufficient) [citation:5]. **Options include** `-page` for selecting a single page from multi-page files, `-psarg` for passing arguments directly to Ghostscript (like resolution changes), `-pslanguagelevel` for PostScript Level 1/2/3 selection, and `-f` for specifying output format . **Best for converting PostScript/PDF into editable vector formats** for illustration software, not for PDF generation itself — Ghostscript handles that side.

### Additional Strong Open-Source Options

- **MuPDF** — **The PDF-focused alternative to Ghostscript for screen and embedded use.** Dual AGPL/Proprietary licensed, written in C with a **much smaller ROM footprint** than Ghostscript [citation:6]. **Example tools include** `mutool convert` for document conversion, `mutool draw` for rendering, and `mutool create` for PDF creation [citation:6]. **The honest boundary**: **MuPDF does not handle PostScript** — it is PDF/XPS/EPUB focused, and Ghostscript's documentation explicitly recommends Ghostscript for PostScript and printing applications [citation:6]. **Best for PDF-centric screen workflows**, not PostScript conversion.

**Frameworks for building custom systems**: Combine **Ghostscript** for the conversion engine with full Distiller parameter control, **ps2pdf** for Distiller-compatible wrapper scripts without learning Ghostscript syntax, **Aspose.Page FOSS** for Python-native conversion without shelling out, and **pstoedit** if you need to convert PostScript to editable vector formats rather than PDF — to build a PostScript-to-PDF stack tailored to your need for batch scripting versus GUI convenience, and Python integration versus command-line deployment.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- PostScript-to-PDF converters differ significantly in abstraction level, Distiller compatibility, and platform support. **Ghostscript is the engine underneath almost every open-source tool** with a massive range of output devices and hardened security posture, but **its command-line interface is not user-friendly** — you need to know the right flags [citation:3][citation:6]. **ps2pdf wraps Ghostscript with Distiller-compatible behavior**, including PDF/X and PDF/A generation, but **the output PDF version may change between Ghostscript releases** — pin to `ps2pdf12/13/14` if compatibility level matters [citation:11]. **Aspose.Page FOSS does not read existing PDFs** and is a newer library with a narrower scope [citation:4]. **pstoedit is for vector format conversion, not PDF generation** — Ghostscript handles that [citation:5]. **MuPDF does not handle PostScript** — Ghostscript is the reference for PostScript and printing workflows [citation:6].
- Self-hosted open-source solutions require proper Ghostscript installation (binary is sufficient for pstoedit [citation:5]), awareness of AGPL licensing obligations for Ghostscript, and understanding of Distiller parameter mappings for prepress output.

---

**Made for print production teams, developers, and system administrators choosing PostScript-to-PDF conversion tools that match their automation and output requirements.**
Let's make PostScript to PDF conversion more open, Distiller-compatible, and pipeline-friendly.
