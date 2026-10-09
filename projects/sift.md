# Sift

A browser search engine with an inspectable ranking pipeline.

[Source and run instructions](https://github.com/justalivefornothing/sift-search) · TypeScript · Web Workers

![Sift search results and ranking explainer](../assets/sift-preview.png)

The demo searches 10,000 generated film-style records. After the dataset loads, queries run locally in a worker. Each result exposes its ranking criteria and the criterion that separates it from the result above.

## Implementation

- A compressed radix trie handles prefix and bounded typo matching.
- A positional inverted index and bitset facets select results.
- Six ranking criteria feed a top-K heap. The UI exposes the criteria and tie-break explanation.
- The JSON playground uses the same local engine. It is not a hosted API.

## A concrete fix

[Recover from invalid requests and bound pagination (#1)](https://github.com/justalivefornothing/sift-search/pull/1), merged September 24, 2026, clamps page values before allocating the result heap. Invalid requests reject their matching operation while allowing later searches to continue. Search and playground requests track stale responses separately.

The [pagination tests](https://github.com/justalivefornothing/sift-search/blob/main/src/engine/search-index.test.ts) and [request recovery tests](https://github.com/justalivefornothing/sift-search/blob/main/src/store.test.ts) exercise those cases.

## Limits

- The bundled corpus is synthetic. Its timing results describe that dataset and workload.
- Queries use at most 16 words; extra words are ignored.
- Candidate expansion caps typo matches at 64 and zero-typo matches at 4,096 per word. These bounds can omit matches on larger vocabularies.
- Result pages contain at most 100 hits.

[Back to profile](../README.md)
