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

## 2026-08-09 (sessao lab v3)
- Corrigido: janelas agora tem VAGO REAL nas paredes (antes vidro colado em parede macica).
  Paredes reconstruidas em segmentos ao redor das aberturas: 10 janelas 4.5x7 (vidro+molduras)
  abertas nas 4 faces, porta 13 studs com vao. Build regenerado com 93 partes.

## 2026-08-09 (sessao igreja)
- Inserida no Studio a igreja `Medieval Church` (assetId 4995693293, criador detonador665) em `game.Workspace`.
  - Modelo com interior: Church Roof, Crosses, Church Walls, Stone Walls, Doors & Windows, Interior Light (231 partes ancoradas).
  - Bounding box: 31,9 x 72,8 x 80,2 studs; centrada em (1,72; 36,41; 7,85) — base em y=0.
  - Para inserir assets de terceiros foi necessario: ativar "Permitir carregamento de conteudos de terceiros"
    (Game Settings > Seguranca) e verificar idade da conta (verificacao por documento).
  - Asset anterior 9615867294 retorna 404 (removido/restrito).
- Registrado asset 4995693293 no `creatorStore[]` (categoria church_gothic).

## 2026-08-09 (sessao lab v4 - expansao)
- Expansao do LabRadiacao: 4 modulos novos gerados e importados (todos compartilham a origem local com o nucleo, pos [712.9, 2.4, -39.3]):
  - `modern/lab_entrada` (42 partes, 59x33x98) - ala de entrada/fachada (z local -48..-28,5)
  - `modern/lab_controle` (74 partes, 107x33x98) - ala Leste (sala de controle)
  - `modern/lab_armazem` (76 partes, 107x33x98) - ala Oeste (armazem)
  - `modern/lab_tecnico` (83 partes, 72x33x98) - ala Norte (corredor tecnico)
- Descobrimento chave: `import_build` ancora a ORIGEM LOCAL do modelo (nao o centro da bbox).
- Vagos de porta cortados no nucleo (Leste/Oeste z -42,3..-36,3; Norte x 709,9..715,9) + 4 portas metalicas.
- Piso interno do nucleo reconstruido (y 2,4..2,8) com fosso aberto para a cratera (buraco x696..730, z-56..-22); cratera/reator reposicionada ao centro.
- Destruicao/efeitos: 5 marcas de queimadura, 6 escombros, painel de teto caido, 2 janelas quebradas + cacos, fogo no reator, fumaca nas pocoes/teto/janela.
- Iluminacao: 17 luminarias fluorescentes com PointLight; script FlickerLights faz 8 piscarem.
- Portas funcionais: ProximityPrompt + script DoorsController (dobradica por TweenService).
- Sinalizacao: 5 placas SurfaceGui (PERIGO RADIACAO, SALA DE CONTROLE, ARMAZEM, fachada, placa lore).
- Organizacao em pastas: Piso->Chao, Paredes (novos trechos norte), Portas, Iluminacao, Efeitos, Sinalizacao.
- Registrados os 4 builds no `localBuilds[]` do database.json.

## 2026-08-09 (sessao lab v5 - simplificacao)
- Usuario achou o LabRadiacao (lab v1-v4) "esquisito e bugado" e pediu algo SIMPLES: estrutura, textura, janelas e teto explodido.
- Apos confirmacao, o modelo `LabRadiacao` foi DELETADO do Workspace junto com `ServerScriptService.LabScripts` (FlickerLights/DoorsController).
- Novo build `modern/lab_simples` (55 partes, 40.8x21.2x22.8) gerado e importado em Workspace na posicao [20, 0.4, 11]:
  - Sala unica interior 40x22x10 (piso de concreto, paredes de concreto cinza-claro, 7 janelas de vidro 4x3.5 nas 4 faces, porta metalica entreaberta com faixa amarela no piso).
  - Teto explodido: buraco central 16x10 com 4 lajes remanescentes, bordas irregulares carbonizadas inclinadas, fuligem sob o teto e detritos caidos no chao.
  - Fogo + fumaca: `FxFogoCentral` (Heat 30, Size 9) e `FxFogoOeste` (Heat 20, Size 5) no buraco.
  - Interior minimo: mesa de trabalho branca, console com tela Neon azul.
- Causa do deslocamento do lab v4 durante playtest `mode=run` continua NAO determinada; a partir de agora usar `mode=play` (DataModel separado, nao corrompe o edit).
- Registrado `modern/lab_simples` no `localBuilds[]` do database.json.

## 2026-08-09 (sessao lab v5b - maior e janelas arrumadas)
- `modern/lab_simples` ampliado (55 -> 104 partes, 40.8x21.2x22.8 -> 56.8x25.2x32.8).
- Sala unica agora interior 56x32x12. Janelas uniformizadas: 10 janelas de vidro 6x5 (4 em cada lado longo, 2 em cada lateral) todas com moldura preta; porta metalica central na parede sul com faixa amarela.
- Teto explodido ampliado: buraco central 24x14, bordas carbonizadas tortas, fuligem sob o teto, detritos caidos; Fire/Smoke recriados (FxFogoCentral/FxFogoOeste).
- Reimportado em Workspace [20, 0.4, 11] e database.json atualizado.

## Observacoes
- Pesquisas de sci-fi/futurista no Creator Store estao retornando lixo (assets "car dealer").
  Tentar queries mais especificas em sessao futura (ex.: "spaceship hangar", "futuristic base").
