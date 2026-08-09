# Historico de Pesquisas

## 2026-08-09 (sessao inicial)
- Criacao do banco. 20 builds locais importados do Studio (via `list_library`).
- Pesquisas no Creator Store (tipo Model):
  - `castle medieval` -> 13 assets salvos (categoria castle_medieval)
  - `house building` -> 8 assets salvos (house_city)
  - `modern skyscraper tower` -> 10 assets salvos (skyscraper_modern)
  - `cabin cottage nature wood` -> 8 assets salvos (cabin_nature)
  - `church temple gothic` -> 8 assets salvos (church_gothic)
  - `mansion villa luxury house` -> 8 assets salvos (mansion_villa)
  - `warehouse industrial factory` -> 8 assets salvos (warehouse_industrial)
  - `school hospital building rp` -> 3 assets salvos (school_rp)
  - `sci-fi laboratory base facility` -> resultados ruins (car dealer etc.), nada salvo
- Total: 64 assets publicos + 20 builds locais no banco.

## 2026-08-09 (sessao laboratorio)
- Reconstruido o `LabRadiacao` no Workspace: fechado como predio 56x56 em volta da cratera.
  - Pastas preenchidas que estavam vazias: Paredes (8), Janelas (14), Teto (1), Bancadas (9),
    Equipamentos (15: capela de exaustao, chuveiro, lava-olhos, painel), Danos (14 vergalhoes).
  - Zonas de radiacao (6) reposicionadas em anel externo (raio 46) fora do predio; cratera/nucleo e
    pocoes radioativas permanecem no interior.
  - Novo build gerado e salvo na biblioteca: `modern/lab_radiologico` (61 partes, 58x21x58.2).

## 2026-08-09 (sessao lab v2)
- LabRadiacao ficou mais alto (paredes 10 -> 16 studs) e com janelas maiores:
  20 janelas 4.5x7 (2 frontais, 6 laterais, 2 traseiras x vidro+moldura), porta 13 studs.
  Teto em y 18.5. Nucleo da cratera (y 1-11) continua no interior.

## 2026-08-09 (sessao igreja)
- Inserida no Studio a igreja `Medieval Church` (assetId 4995693293, criador detonador665) em `game.Workspace`.
  - Modelo com interior: Church Roof, Crosses, Church Walls, Stone Walls, Doors & Windows, Interior Light (231 partes ancoradas).
  - Bounding box: 31,9 x 72,8 x 80,2 studs; centrada em (1,72; 36,41; 7,85) — base em y=0.
  - Para inserir assets de terceiros foi necessario: ativar "Permitir carregamento de conteudos de terceiros"
    (Game Settings > Seguranca) e verificar idade da conta (verificacao por documento).
  - Asset anterior 9615867294 retorna 404 (removido/restrito).
- Registrado asset 4995693293 no `creatorStore[]` (categoria church_gothic).

## Observacoes
- Pesquisas de sci-fi/futurista no Creator Store estao retornando lixo (assets "car dealer").
  Tentar queries mais especificas em sessao futura (ex.: "spaceship hangar", "futuristic base").
