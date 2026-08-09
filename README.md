# Roblox Builds DB

Banco de dados publico de construcoes para projetos Roblox. Consultar ANTES de procurar qualquer construcao.

## O que tem aqui

- `database.json` — banco principal
  - `creatorStore[]`: modelos publicos de construcao do Creator Store da Roblox (assetId, nome, categoria, link direto, preco)
  - `localBuilds[]`: builds criados/importados no seu Studio (biblioteca local do MCP)
- `history.md` — registro do que foi pesquisado em cada sessao
- `README.md` — este arquivo

## Categorias

- `castle_medieval` — castelos, vilas medievais, muralhas
- `house_city` — casas e predios residenciais de cidade
- `skyscraper_modern` — arranha-ceus e predios de escritorio modernos
- `cabin_nature` — cabanas e construcoes de madeira/rusticas
- `church_gothic` — igrejas, catedrais, templos
- `mansion_villa` — mansoes e vilas de luxo
- `warehouse_industrial` — galpoes e fabulas industriais
- `school_rp` — escolas e hospitais para roleplay

## Como usar (fluxo de toda sessao nova)

1. Sincronizar este repo (`git pull`) — o banco carrega no contexto.
2. Consultar `database.json` antes de pesquisar qualquer construcao.
3. Pesquisas novas no Creator Store: adicionar ao `creatorStore[]` (deduplicar por `assetId`).
4. Builds novos no Studio: adicionar ao `localBuilds[]`.
5. Atualizar `meta.lastUpdated`/`lastSearch`, registrar em `history.md`, commit + push.

## Regras

- `priceRobux = null` significa preco nao verificado; conferir na pagina do asset antes de comprar.
- Link de asset: `https://create.roblox.com/store/asset/{assetId}`
