# News

The common news vocabulary -- the news articles published and aggregated, and the sources that publish them -- distilled from the APIs that already exist. Blog posts belong to content management and help articles to the knowledge base. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged News, News API, Journalism, Media Monitoring, News Aggregation, Media Intelligence in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| news_article | 31 | 31 | name 77%, description 58%, published_at 58%, id 52%, source_id 52% | news 15, articles 8, stories 5, top-headlines 5 |
| news_source | 10 | 10 | name 70%, category 60%, language 60%, country 50% | sources 9, feeds 1 |

Cohort: 73 providers with harvested OpenAPI, 31 crosswalks. Of the providers exposing a news_article: 26% create, 84% list, 32% fetch, 0% update, 0% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A news article agrees on title, description, publish date, id and its source across aggregators, publishers and media-monitoring tools -- the headline record NewsAPI popularised, which most of the category copied.
- A news source agrees on name, category, language and country.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Articles are `/news-articles` and sources `/news-sources`: the knowledge base owns `/articles`, and a bare `/sources` means something else in most contexts.
- Stories, headlines and news search results are news articles.
- Duplicates merged: Dow Jones into Factiva.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
