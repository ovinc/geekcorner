# Inkscape

## Command line

Export all SVG files in a folder to PDF
```bash
inkscape --export-type=pdf *.svg
```

Export specific file
```bash
inkscape --export-filename=out.pdf in.svg
```

Export specific file(s), keeping same name
```bash
inkscape --export-type=pdf in.svg
inkscape --export-type=pdf in1.svg in2.svg
```

