# Duckbench

Data preparation workbench that runs in the browser, with two engines. Full runs DuckDB-wasm: every transform, and CSV, TSV, TXT, XLSX, XLS and Parquet files. Express runs Arquero: most transforms, CSV and Excel only. It also imports `.duckbench.json` project files.

## Engine versions

- Full mode runs the DuckDB 2.0 engine. npm publishes it as a prerelease build of `@duckdb/duckdb-wasm` (`1.33.1-dev114.0`), so Duckbench pins that exact version and never a floating tag. If it cannot load, or the browser lacks WebAssembly exception handling, it falls back to the last stable release (`1.32.0`, DuckDB 1.4).
- Express mode runs Arquero 8.0.3 from the CDN.
- A version chosen in the engine panel is remembered in that browser. Automatic fallbacks are not remembered, so the next load tries the default again.

## Limits

- Parquet and the full set of transforms need Full mode. Express covers common transforms on CSV and Excel only.
- Full mode downloads DuckDB-wasm from a CDN at run time, so its first load needs a connection. Express loads only Arquero.
- Excel and Parquet imports and Parquet and JSON exports in Full mode need a DuckDB extension that is downloaded on first use.
- There is no service worker, so the page does not work offline.

## Self-test

Open `selftest.html` for Full against Arquero, or `selftest-frame.html` for Full against Frame. Every case should pass; the Parquet and JSONL export cases need the extension downloads above.

## Network and install

Calls registry.npmjs.org for the latest DuckDB version when asked, and extensions.duckdb.org when Full mode first needs an extension. Loads DuckDB-wasm and Arquero from a CDN. Not installable; no service worker.
