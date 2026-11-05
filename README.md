# Duckbench

Data preparation workbench that runs in the browser, with two engines. Full runs DuckDB-wasm: every transform, and CSV, TSV, TXT, XLSX, XLS and Parquet files. Express runs Arquero: most transforms, CSV and Excel only. It also imports `.duckbench.json` project files.

## Limits

- Parquet and the full set of transforms need Full mode. Express covers common transforms on CSV and Excel only.
- Full mode downloads DuckDB-wasm from a CDN at run time, so its first load needs a connection. Express loads only Arquero.
- There is no service worker, so the page does not work offline.

## Network and install

Calls registry.npmjs.org for the latest DuckDB version when asked; nothing else leaves the browser. Loads DuckDB-wasm and Arquero from a CDN. Not installable; no service worker.
