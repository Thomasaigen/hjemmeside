# Hurtig guide: Erstat billeder og tekst lokalt

Denne workspace indeholder et lille content-system så du nemt kan ændre tekster og billeder uden at redigere alle HTML-elementerne direkte.

Hvordan det virker
- Filen `assets/content/content.json` indeholder nøgler og værdier (tekst og billednavne).
- Billeder lægges i `assets/content/images/` og refereres fra `content.json` ved filnavn (f.eks. `hero.jpg`).
- Et lille JavaScript (`assets/js/content-loader.js`) henter `content.json` og erstatter elementer i DOM med attributterne `data-content-key`.

Eksempler (i dine HTML-filer)

1) Erstat tekst:
```html
<h1 data-content-key="site.title" data-content-type="text">Fallback title</h1>
```

2) Erstat HTML:
```html
<div data-content-key="site.description" data-content-type="html">Fallback description</div>
```

3) Erstat et billede (img tag):
```html
<img data-content-key="hero.image" data-content-type="img" alt="Fallback alt" />
```

4) Opdatér kun alt-teksten:
```html
<img src="assets/images/whatever.png" data-content-key="hero.imageAlt" data-content-type="alt"> 
```

Redigering
- Opdater `assets/content/content.json` for at ændre tekster eller sætte et andet billednavn.
- Læg nye billeder i `assets/content/images/`.

Noter
- Hvis du bruger absolutte URLs i `content.json` (starter med `http`), bruges de som de er.
- Scriptet kører automatisk ved DOMContentLoaded.
