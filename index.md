---
layout: default
---
## About ##
The [Zotpicknix scripts](https://github.com/emmareisz/zotpicknix) provide Linux users with easy access to the [Better BibTeX workflow](https://zotplus.github.io/better-bibtex/cayw.html) for using a floating picker to access Zotero citations in Scrivener (or another editor). This method gives you **live citations** at the end. There are a few steps to setting it up, but once it is working, it is very convenient.

Note that this is an *alternative* to producing citations by simply opening Zotero, selecting your reference, copying with Ctrl-Shift-A and then pasting into Scrivener. The benefit of the method below is that it allows you to access the Zotero Picker from within Scrivener.

## Installation ##
1. Install the [Better BibTeX plugin](https://zotplus.github.io/better-bibtex/) for Zotero. Install it ***either*** for Zotero Firefox **or** for Standalone, but **not both**. If you are using Zotero for Firefox, go to Zotero Preferences/Better BibTex/ImportExport and check 'Enable export by HTTP'; restart Firefox.
2. Confirm Better BibTeX is set up correctly by opening [this page] (http://localhost:23119/better-bibtex/cayw?probe=probe) while Zotero is running. The word 'ready' should appear in that tab of your browser.
3. Install [xdotool] (http://www.semicomplete.com/projects/xdotool/) on Linux (in the package archives of most distributions).  
4. Scripts for two citation marker formats are available: **Scannable-Cite** and **Pandoc**. If you edit in a word processor after you have finished in Scrivener, or if you aren't sure what you need, pick Scannable-Cite. If you write in a markup format, including Markdown or LaTeX, you will need Pandoc. (Better BibTeX [also supports](https://zotplus.github.io/better-bibtex/cayw.html) .mmd and LaTeX's own marker formats, i.e. without using Pandoc; if you need these, let me know or simply edit the script for your required query URL.)  

### Installation cont.: Scannable-Cite ###
1. For **Scannable-Cite** markers, [download](https://github.com/emmareisz/zotpicknix) the zotpicknix-sc script. Mark the script as executable and save it in your PATH, e.g. in a folder called 'bin' in your Home directory. If you want to create citations in a text editor other than Scrivener, you will need to edit the script (see the README.md).  
2. Create a system keyboard shortcut to wherever you saved the script. (This is necessary because the built-in citation integration in Scrivener does not call Linux executables correctly.)
3. Install the [RTF/ODT plugin](https://zotero-odf-scan.github.io/zotero-odf-scan/) for Zotero.  
4. Make sure Zotero's LO/OO plugin is installed (Zotero/Preferences/Cite/Word Processors).  

### Installation cont.: Pandoc ###
1. For **Pandoc** markers, [download](https://github.com/emmareisz/zotpicknix) the zotpicknix-pd script. Mark the script as executable and save it in your PATH, e.g. in a folder called 'bin' in your Home directory. If you want to create citations in a text editor other than Scrivener, you will need to edit the script (see the README.md).  
2. Create a system keyboard shortcut to wherever you saved the script. (This is necessary because the built-in citation integration in Scrivener does not call Linux executables correctly.)  
3. Install [pandoc](http://pandoc.org/) (in the package repositories of most Linux distributions).  
4. In Zotero, go to the library you want to use for citations and right-click; select 'Export/Format: Better BibTeX' and check 'Keep Updated'. Choose a suitable location for your export.  

## Usage ##
1. Make sure Zotero is running. In Scrivener, place the cursor where you want the reference to go. When it is in the correct location, enter your keyboard shortcut for your script. **Any text you have selected will be overwritten.**  
2. The little Zotero picker window should appear.
3. In the picker, select the item you want to cite from your library. When you have selected it, double-click on the reference to get more options (page locators, prefix etc.).  
4. When you have added all the citations you need in that reference, press Enter.  
5. Some strange-looking text will now appear in Scrivener wherever you left the cursor. This is a citation marker. If you are using Scannable-Cite, it will look like this: `{ | Smith, (2012) | | |zu:2433:WQVBH98K}` (more information on editing Scannable Cite references is [here](https://zotero-odf-scan.github.io/zotero-odf-scan/)). If you are using Pandoc, it will look like this: `[@smith_test_2012]`.  
6. Continue writing your text and inserting references until you have finished your work. When you have finished, you will need to process your citations.  

### Processing Citations: Scannable-Cite ###
7. 'Compile' your Scrivener document. If you use footnotes in Scrivener, compile for .rtf (Scrivener will not export footnotes to .odt); otherwise compile for .odt.  
8. If your document is now in .rtf, use LibreOffice or OpenOffice to save it as .odt.  
9. Open Zotero and select Tools/RTF Scan. Choose 'ODF to citations' and select the .odt document you have just created. Enter a suitable name for the new .odt document you are creating and click Next. For more information, see [here](https://zotero-odf-scan.github.io/zotero-odf-scan/).  
10. You will now have an .odt document with live citations. You can work with this as normal in LibreOffice/OpenOffice. You can process the citations in the familiar way using the Zotero add-on for LO/OO: select a style, create a bibliography, etc. The citations will stay live as long as the document is in .odt. If you save it as .doc, .rtf etc., the citations will become fixed.  

### Processing Citations: Pandoc ###
7. 'Compile' your Scrivener document/ save your document in your chosen format. Pandoc works best with markup languages like Markdown.  
8. To process your citations, open the terminal and run the following command:
`pandoc --filter pandoc-citeproc --bibliography BIBLIOGRAPHY.bib --csl STYLE.csl -o outputfile inputfile`.
(For BIBLIOGRAPHY.bib, give the file path to the library you exported during installation. For STYLE.csl, give the file path to your chosen csl style file. Set the input and output filenames as needed. For more information, see [here](http://pandoc.org/README.html).) Your citations are now fixed in the output file.  
9. ALTERNATIVELY, if you are using Markdown/MMD/Pandoc-Markdown/LaTeX and want HTML output, you can process the citations via a GUI by using [Atom](https://atom.io/) with [Markdown Preview Plus](https://atom.io/packages/markdown-preview-plus). You can save the html output by right-clicking in the preview window.  
10. More information on Pandoc/Scrivener workflows is available [from Dave Smith](https://davepwsmith.github.io/academic-scrivener-howto/) (written for Mac users).  
