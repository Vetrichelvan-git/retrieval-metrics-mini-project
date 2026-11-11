## Write up your findings

### Result Table

| Query | Keyword rank | Semantic rank |
|---|---|---|
| my redis cache keeps showing old data | 8 | 1 |
| how do I add semantic search to a table I already have | miss | 2 |
| redis or memcached for caching | 1 | 2 |
| why did my query get slower after I added an index | miss | 1 |
| what does ACID actually guarantee | 2 | 1 |
| how do I keep my postgres online while changing the schema | 6 | 3 |
| my background jobs stop after every deploy | miss | 2 |
| how do I let my database accept more writes per second | 4 | 1 |
| sql or nosql for a new product | 1 | 3 |
| why does my redis memory keep climbing | miss | 2 |
| **Summary** | **MRR 0.30 · Recall@10 0.60** | **MRR 0.67 · Recall@10 1.00** |

### Interpretation

Semantic search is significantly better overall across both evaluated metrics, achieving an MRR of 0.67 compared to 0.30 for keyword search, and finding the correct answer in the top 10 for every single query (Recall@10 of 1.00 vs 0.60). Keyword search won queries such as "redis or memcached for caching" (rank 1 vs 2) and "sql or nosql for a new product" (rank 1 vs 3), which share concise, exact technical keywords and comparison formats where lexical matching is strong. In contrast, semantic search dominated queries describing symptoms and paraphrased issues, such as "my redis cache keeps showing old data" (rank 1 vs 8) and questions where keyword search produced outright misses like "why did my query get slower after I added an index" and "my background jobs stop after every deploy". A real-world engineering team would still keep the keyword search system around because it reliably outperforms semantic search on rare technical tokens and exact naming, providing the perfect complementary foundation for a hybrid search architecture (such as Reciprocal Rank Fusion) that combines the strengths of both models.