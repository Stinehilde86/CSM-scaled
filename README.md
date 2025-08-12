[README.md](https://github.com/user-attachments/files/21738074/README.md)
# Prosjektoversikt – Scaled CSM (Netlify-drop)

En enkel, statisk webapp du kan **dra og slippe** i Netlify (no build).

## Innhold
- `index.html` – laster React fra CDN og Babel Standalone for JSX i nettleser.
- `assets/styles.css` – lettvekts stilark med Simployer-farger.
- `assets/app.jsx` – selve appen (React), lagring i `localStorage`.

## Deploy (Netlify drag & drop)
1. Pakk mappen som ZIP eller last opp mappen direkte i Netlify **Sites → Add new site → Deploy manually**.
2. Ingen build-kommando nødvendig.
3. **Publish directory**: rotmappen (der `index.html` ligger).

## Funksjoner
- Søk, statusfilter, eierfilter
- Klikkbar sortering på kolonner
- Legg til / rediger / slett prosjekter (lagres i `localStorage`)
- CSV-eksport
- Frist-fargekoding: **rød** (forfalt), **gul** (<7 dager), **grønn** (ellers)
- Statusbadge for “Pågår” bruker **primærfargen** (#A770FF)
- Liten brand-logo i hero

## Tilpasning
- Endre farger i `:root` i `assets/styles.css`:
  - `--primary: #A770FF`
  - `--on-primary: #FFFFFF`
  - `--fg: #333333`

## Personvern
Appen lagrer data bare i nettleserens `localStorage`. Ingen serverlagring.
