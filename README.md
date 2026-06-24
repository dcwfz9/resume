# Resume — Derek C. Welty

**[View latest PDF](https://github.com/dcwfz9/resume/blob/build/resume.pdf)**

> LaTeX source built with the [Awesome-CV](https://github.com/posquit0/Awesome-CV) template. Originally scaffolded at [resumake.io](https://resumake.io). PDF is automatically compiled and published on every push via GitHub Actions.

## Building locally

### Tectonic (recommended — self-contained, no TeX Live install)
[Tectonic](https://tectonic-typesetting.github.io/) is a single-binary XeTeX engine. It downloads only the packages it needs and uses the fonts bundled in `fonts/` (Roboto + Source Sans Pro), so no system TeX install is required.

```
brew install tectonic   # macOS (see the Tectonic site for Linux/Windows)
tectonic resume.tex     # writes resume.pdf in this folder
```

The first run fetches support files (cached afterward). A harmless `Overfull \hbox` warning on the Skills table is expected.

### XeLaTeX (TeX Live)
```
sudo apt-get install texlive-xetex texlive-fonts-recommended
xelatex resume.tex
```
Or edit and build with a GUI tool like TeXstudio.

## Notes
- `resume.pdf` is git-ignored — GitHub Actions compiles it and publishes to the `build` branch on every push.
- To check the page count programmatically: Tectonic writes **compressed** PDF object streams, so a raw `grep '/Type /Page'` finds nothing. Decompress the streams first (a short Python `zlib` script over each `stream`…`endstream` block works).
