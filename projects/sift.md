# Sift

Search that shows its work.

**TypeScript · Web Workers · [Source code ?](https://github.com/justalivefornothing/sift-search)**

![Sift search results and ranking explainer](../assets/sift-preview.png)

A browser search engine over 10,000 generated film-style records. Type a query, make a typo, narrow the results, and inspect why one result outranks another. After the dataset loads, queries run locally in a worker.

## Inside the engine

- A compressed radix trie supports prefix search and bounded typo matching.
- A positional inverted index and bitset facets narrow the candidate set.
- Six ranking criteria feed a top-K heap; each result exposes its criteria and tie-break explanation.
- Queries run in a worker after the bundled dataset loads. The playground exposes the request and response as JSON; it is not a hosted API.

## Making search recover

Extreme page values are clamped before heap allocation. Invalid requests reject the matching operation without disabling the whole app, and search and playground results have independent stale-response tracking. A valid failed request can be retried without editing it.

<details>
<summary>Verification</summary>

The search-recovery change passed **107 tests**, the TypeScript/Vite build, and Linux/Windows Node 24 CI. The image above is an application screenshot.

</details>

[← Back to selected work](../README.md)
