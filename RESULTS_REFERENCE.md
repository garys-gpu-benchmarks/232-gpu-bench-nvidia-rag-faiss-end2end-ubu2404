# Results: 232 RAG Pipeline Sweep

**Main goal:** Measure end-to-end RAG retrieval plus generation performance  
**Tools:** Run scripts/gpu-bench-rag-faiss-end2end.py for squad_v2 retrieval, BGE embeddings, FAISS search, and Mistral generation

Reference results from the validation run on the system shown in each section (recorded 2026-11-22). Your own runs write `results/RESULTS_ACTUAL.md` in the same format.

> Smoke runs use deliberately small sizes. They check that the workload installs and runs end to end; their numbers are not performance results. Baseline and extended are.

<!-- profile:smoke -->
## smoke

- **System:** 1× NVIDIA H100 80GB HBM3 (81559 MiB) · Intel(R) Xeon(R) Platinum 8470 · Ubuntu 24.04.5 LTS · kernel 6.8.0-149-generic · driver 595.112.07
- **Run:** 2026-11-22T11:53:38Z · status **PASS** (exit 0)
- **Time (mm:ss):** setup 01:54 · benchmark 00:09 · whole run 02:13
- **Source:** run 232_20261122_115338
- **Command:** `bash run_benchmark.sh --smoke --chunk-size 64 --chunk-overlap 32 --corpus-dataset rajpurkar/squad_v2 --top-k 5 --embedding-model BAAI/bge-small-en-v1.5 --query-length 32 --batch-size 2 --llm-model mistralai/Mistral-7B-v0.3 --query-count 2 --reranker-model BAAI/bge-reranker-base`

| # | Metric | Result |
|---|---|---|
| 1 | E2E mean over queries, ms (end_to_end_query_latency_retrieval_generation_ms) | 690.164685016498 |
| 2 | Generation TTFT, ms (generation_phase_time_to_first_token_ms) | 58.0442079808563 |
| 3 | CPU FAISS retrieval latency, ms (retrieval_latency_vector_search_ms) | 0.2215510467067361 |
| 4 | Gen throughput, tok/s (generation_throughput_output_tokens_s) | 24.6434824700373 |
| 5 | Embedding throughput, chunks/s (embedding_throughput_chunks_s) | 517.1627451163256 |
| 6 | FAISS index vectors (faiss_index_ntotal) | 217.0 |
<!-- /profile:smoke -->
