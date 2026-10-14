# index-lander

Build static publicat pentru **<https://index.yebichu.com>** (între timp, pe subcalea
GitHub Pages: <https://yebichu.github.io/index-lander/>).

> **Nu edita fisierele din acest depozit.** Tot arborele este generat de
> `pnpm release` din depozitul privat `bvb-onnx` și apoi copiat aici; orice
> modificare facuta direct este stearsa la urmatorul build.

## Ce contine

| Cale | Rol |
| --- | --- |
| `index.html` | raportul (SPA Vite/React), cu datele pipeline-ului importate la build |
| `assets/` | JS + CSS, cu nume hash (cache imutabil) |
| `brand/`, `fonts/` | ilustratiile de brand și fonturile self-hosted |

## De ce merge de oriunde

Rutele traiesc în **hash** (`#/ro/romania/weights?v=prudent`), deci singura cale
reala este rădăcina site-ului:

* același artefact functioneaza pe domeniu, pe subcalea unei pagini de proiect
  GitHub Pages sau local, fără rescrieri pe server;
* resursele sunt scrise relativ (`./assets/...`, `../fonts/...`);
* nu e nevoie de `404.html`: orice adresa ceruta serverului este un fisier real.

## Publicare

Fluxul rulează din depozitul privat:

```bash
pnpm release            # build in release-dist/
pnpm release:publish    # build + commit + push in acest depozit
pnpm release:serve      # previzualizare locala, ca pe GitHub Pages
```

Hărțile de surse (`*.map`) **nu** se publica: ar expune sursa depozitului privat.
