# lecta-lexicon-data

Tablas léxicas derivadas en español que usa [Lecta](https://lecta.luis-sg9915.workers.dev),
un lector EPUB con vocabulario integrado. Se publican para cumplir las
licencias de las fuentes (ODbL 1.0 y CC BY-SA 4.0) y para que cualquiera
pueda reutilizarlas.

## Archivos

| Archivo | Contenido | Filas | Licencia |
|---|---|---|---|
| `forms-es.csv.gz` | `form,lemma` — cada forma flexionada apunta a su lema | 665 732 | **ODbL 1.0** (`LICENSE-ODbL-1.0.txt`) |
| `lemmas-freq-es.csv.gz` | `lemma,zipf` — frecuencia en escala zipf (~0–8; vacío = sin medida) | 71 646 | **CC BY-SA 4.0** (`LICENSE-CC-BY-SA-4.0.txt`) |

## Cómo se generaron

1. `forms-es.csv.gz`: exportación de la lista de lematización `es` que
   empaqueta [simplemma](https://github.com/adbar/simplemma) 1.1.2
   (script `lexicon-export.py` del repo principal de Lecta).
2. `lemmas-freq-es.csv.gz`: frecuencias `zipf_frequency` de
   [wordfreq](https://github.com/rspeer/wordfreq) 3.1.1 para cada lema
   de la lista anterior (40 013 lemas con frecuencia medida; los demás
   llevan `zipf` vacío porque wordfreq no los tiene en su corpus).

## Fuentes y créditos

La lista `es` de simplemma combina:

- **Lemmatization Lists** de Michal Měchura — ODbL 1.0
- Wikcionario vía [kaikki.org](https://kaikki.org) — CC BY-SA 4.0 / GFDL
- FreeLing (UPC/IULA) — LGPLLR
- spaCy lookups-data — MIT
- UniMorph `spa` — CC BY-SA 3.0
- Wikinflection (Metheniti) — CC BY 4.0

Código de simplemma © Adrien Barbaresi, MIT.

Las frecuencias derivan de **wordfreq** de Robyn Speer (CC BY-SA 4.0),
que incluye Google Books Ngrams, Wikipedia, ParaCrawl, OpenSubtitles,
Twitter, Reddit, SUBTLEX y otras fuentes. Los datos SUBTLEX provienen de
Marc Brysbaert et al. y son datos libres (ver `NOTICE.md` de wordfreq).

**Contiene información de «Lemmatization Lists», disponible bajo la
Open Database License (ODbL) 1.0.**

## Uso

```bash
gunzip -c forms-es.csv.gz | head
gunzip -c lemmas-freq-es.csv.gz | head
```

Si reutilizas estas tablas, respeta las licencias indicadas: atribución
y share-alike en ambas, y ofrece las obras derivadas bajo los mismos
términos.
