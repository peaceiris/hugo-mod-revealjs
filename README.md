## hugo-mod-revealjs

[reveal.js] packaged as a Hugo Module ([Hugo Modules]).

[reveal.js]: https://revealjs.com/
[Hugo Modules]: https://gohugo.io/hugo-modules/



## Usage

`config/_default/config.yaml`

```yaml
module:
  imports:
    - path: github.com/peaceiris/hugo-mod-revealjs
```

In a Hugo template file.

```html
{{ $revealjs := resources.Get "mod/revealjs/dist/reveal.js" }}
{{ $revealjsHash := $revealjs | resources.Fingerprint "sha512" }}
<script src="{{ $revealjsHash.Permalink }}" integrity="{{ $revealjsHash.Data.Integrity }}"></script>

{{ $markdown := resources.Get "mod/revealjs/plugin/markdown/markdown.js" }}
{{ $markdownHash := $markdown | resources.Fingerprint "sha512" }}
<script src="{{ $markdownHash.Permalink }}" integrity="{{ $markdownHash.Data.Integrity }}"></script>

{{ $highlight := resources.Get "mod/revealjs/plugin/highlight/highlight.js" }}
{{ $highlightHash := $highlight | resources.Fingerprint "sha512" }}
<script src="{{ $highlightHash.Permalink }}" integrity="{{ $highlightHash.Data.Integrity }}"></script>

{{ $zoom := resources.Get "mod/revealjs/plugin/zoom/zoom.js" }}
{{ $zoomHash := $zoom | resources.Fingerprint "sha512" }}
<script src="{{ $zoomHash.Permalink }}" integrity="{{ $zoomHash.Data.Integrity }}"></script>

{{ $notes := resources.Get "mod/revealjs/plugin/notes/notes.js" }}
{{ $notesHash := $notes | resources.Fingerprint "sha512" }}
<script src="{{ $notesHash.Permalink }}" integrity="{{ $notesHash.Data.Integrity }}"></script>

{{ $math := resources.Get "mod/revealjs/plugin/math/math.js" }}
{{ $mathHash := $math | resources.Fingerprint "sha512" }}
<script src="{{ $mathHash.Permalink }}" integrity="{{ $mathHash.Data.Integrity }}"></script>

<script>
  Reveal.initialize({
    plugins: [ RevealMarkdown, RevealHighlight, RevealZoom, RevealNotes, RevealMath ]
  });
</script>
```
