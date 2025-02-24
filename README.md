# Tauri + SvelteKit + TypeScript

This template should help get you started developing with Tauri, SvelteKit and TypeScript in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) + [Tauri](https://marketplace.visualstudio.com/items?itemName=tauri-apps.tauri-vscode) + [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer).

## 画像表示のための設定


tauri v1 で convertFileSrc っていう関数があるのは知っているのでそこをスタートとする

- doc: https://v2.tauri.app/reference/javascript/api/namespacecore/#convertfilesrc

configファイルの変更が必要とのこと

- tauri.conf.json
  - app.security.csp
    - `"csp": "default-src 'self' ipc: http://ipc.localhost; img-src 'self' asset: http://asset.localhost"`
  - app.security.assetProtocol
