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

## 2026-08-09 (sessao lab v5c - escala pro jogador, porta pronta, vidro transparente)
- `modern/lab_simples` ampliado de novo (104 -> 139 partes, 56.8x25.2x32.8 -> 84.8x33.2x52.8): sala unica interior 84x52x16 para escala de jogador.
- Janelas transparentes (Transparency 0.7) e em maior numero: 12 vidros 6x5 com molduras pretas (6 norte, 3 leste, 3 oeste); parede sul sem janelas (entrada).
- Porta de laboratorio PRONTA do Creator Store: asset 92172398640603 [FREE] Factory/Laboratory Door (22 partes, 4.8x7.3x1.1, decals) inserida na parede sul. Scripts removidos pela sanitizacao (insercao segura). Observacao: `Model:PivotTo` deixou 2 folhas da porta para tras no modelo sem PrimaryPart; solucionado movendo por delta do centro do bbox.
- Vao da porta ampliado (5.2 x 7.5) para caber a porta; faixa amarela no piso na entrada.
- Teto explodido ampliado: buraco central 28x16; Fire/Smoke recriados.
- Reimportado em Workspace [20, 0.4, 11] e database.json atualizado.

## 2026-08-09 (sessao lab v6 - porta funcional)
- Porta do lab_simples (PortaLab, asset 92172398640603) agora ABRE/FECHA.
- Removidos os 44 Welds do asset (todas as 22 partes sao ancoradas, welds so atrapalhavam a animacao).
- Criado `ServerScriptService.PortaController`: classifica a folha deslizante (17 partes movem; 3 montantes + verga + soleira fixos), cria ProximityPrompt ("Abrir porta", E, dist 7) em runtime e faz toggle com TweenService 0.8s.
- Descobrimento: as partes do asset tem rotacoes locais variadas — usar multiplicacao local (`CFrame * CFrame.new(delta)`) NAO funciona; usar translacao em ESPACO-MUNDO (`CFrame.new(pos+delta) * rotacao`).
- Folha desliza +X 4.4 studs (para dentro da parede sul, do lado direito) e +Z 0.45 (para fora, evitando z-fight com o montante).
- Validado em playtest `mode=play`: E abre (folha em x22.9..25.9) e fecha (x18..22) corretamente. Edit permanece intacto (porta fechada, sem prompt salvo).
- database.json atualizado: asset 92172398640603 registrado no `creatorStore[]`; nota do `modern/lab_simples` indica porta funcional.

## 2026-08-09 (sessao lab v7 - janelas frontais)
- Parede sul do `lab_simples` (que nao tinha janelas) ganhou 4 janelas PRONTAS do Creator Store:
  asset 13064299369 "Modern Window (Set of 4)" (CmooseStudiosRoblox, verificado, sem scripts, 240 triangulos,
  5 partes por janela: 1 painel preto translucido transp 0.6 + 4 molduras Smoky grey).
- Posicionadas como `JanelaFrente_1..4` (filhas de lab_simples, ancoradas, 8x4x0.1 em z -116.6, y 4.5..8.5):
  J1 x56..64, J2 x66..74, J3 x86..94, J4 x96..104; porta (x77.8..82.2) entre as duplas.
- VAO REAL cortado na faixa inferior da parede sul (y 1.05..8.55): os 2 segmentos (x38..77.4 e x82.6..122)
  foram substituidos por 10 pecas (ParedeSulSeg_1..10) deixando aberturas atras de cada janela +
  ParedeSulSuperior (y 8.45..16.95) recriada. Raycast de dentro do lab confirma que os 4 vãos
  enxergam o vidro (painel) das janelas — visiveis do interior.
- Lab_simples agora com 167 partes (antes 139). Posicao do lab em mundo: x37.6..122.4, z-169.1..-116.2.
- database.json atualizado: asset 13064299369 registrado no `creatorStore[]` (categoria nova `window`);
  nota do `modern/lab_simples` indica as 4 janelas frontais com vao real.

## 2026-08-09 (sessao lab v7b - janelas frontais trocadas por vidro proprio)
- Usuario achou as janelas do asset 13064299369 (Modern Window Set of 4) "estranhas".
- Causa raiz: ao reposicionar, as partes foram parar em z=-118.3 (1.7 studs FORA da parede, que vai de
  -117.1 a -116.3) — janelas flutuando na frente da fachada. Alem disso, as molduras de 0.1 do asset
  eram tao finas que o conjunto parecia quebrado (painel preto 4x3.8 dentro de um bbox 8x4).
- Trocadas por VIDRO PROPRIO no estilo das janelas do norte (Material Glass, Light blue, transp 0.7):
  4x `JanelaFrente_1..4` (5 partes cada, filhas de lab_simples, ancoradas):
  - Vidro 7.6x3.5x0.2 embutido no CENTRO da parede (z -116.7), y 4.75..8.25, x cx+-3.8
  - Moldura preta (Plastic) preenchendo o vao 8x3.9, flush na FACE INTERNA (z -116.3):
    MolduraTopo/Base 8.0x0.4, MolduraEsq/Dir 0.4x3.9.
  - cx: 60, 70, 90, 100 (porta entre x74 e x86).
- Verificado por raycast dos dois lados: de dentro acerta Vidro@z-116.6, de fora Vidro@z-116.8
  (vidro embutido, visivel dos dois lados). Total 167 partes (inalterado).
- database.json: asset 13064299369 marcado como testado/substituido; nota do lab_simples atualizada.

## 2026-08-09 (sessao lab v7c - janelas grandes de vidro)
- Usuario pediu janelas "tipo laboratorio ja criada no roblox e MAIORES" e depois "quero vidro".
- Asset 11963019007 "Factory Window" (11 partes, 0 scripts, 9.2x4.4x0.2): grade de aco com vidro
  invisivel (transp 5) + decal de sujeira. Inserido 4x no Workspace, welds removidos, partes ancoradas,
  escalado 1.5x (13.8x6.6) e posicionado nos vãos grandes. Usuario NAO gostou do estilo industrial.
- Parede sul RECONSTRUIDA com 4 vãos GRANDES simetricos (janela 13.8x6.6 em y4.2..10.8, centros x
  48.97/66.83/93.17/111.03, pilares/peitoris/vergas de 4.07 com simetria em torno da porta x80):
  - 6 pilares ParedeSulPilar_1..6 (x38..122, y1.05..16.95)
  - 4 peitoris (y1.05..4.2) + 4 vergas (y10.8..16.95) atras de cada janela
  - 1 verga da porta (ParedeSulPortaVerga, x77.8..82.2, y8.45..16.95)
- Janelas finais (aprovadas): VIDRO PROPRIO estilo norte ampliado — JanelaFrente_1..4 com Vidro
  13x5.8x0.2 (Material Glass Light blue transp 0.7) embutido no centro da parede (z-116.7) + moldura
  preta 13.8x6.6 flush na face interna (z-116.3). Raycast dos dois lados confirma visibilidade.
- lab_simples com 171 partes. database.json: asset 11963019007 registrado (testado/rejeitado);
  nota do lab_simples atualizada.

## 2026-08-09 (sessao lab v7d - alinhamento da parede sul)
- Usuario: "as paredes nao estao se encontrando de forma satisfatoria".
- Diagnosticado: a parede sul estava 1.72 studs AO SUL do footprint do lab (z-116.7), enquanto piso,
  paredes laterais e PORTA estavam corretos (borda z-118.42). Furos de 1.32 nos cantos SW/SE.
- Correcoes em Workspace:
  - 15 pecas ParedeSul (6 pilares + 4 peitoris + 4 vergas + 1 verga da porta) movidas -1.72 em z ->
    centro z-118.42, flush com o piso e as paredes laterais (raycast nos 4 cantos confirma).
  - Pilares P1/P6 alargados ate x37.75 / x122.25 (flush com as faces externas das paredes oeste/leste).
  - 4 janelas JanelaFrente_1..4 movidas -1.72 em z (vidro embutido em z-118.42, molduras z-118.02).
  - PortaLab NAO foi movido (ja estava em z-118.97..-117.87, centro z-118.42 = centro da parede).
  - PortaVerga (ParedeSulPortaVerga) estendida de y8.45..16.95 para y8.28..16.95, selando a fresta
    de 0.15 acima do marco da porta (topo da folha y8.30).
  - Cantos NW/NE fechados com 2 blocos novos CantoNorte_W/E (0.4x15.9x0.4 em x37.95/122.05, z-170.62).
- Verificacao por raycast (y1.5..16.5, x37.75..122.25): SUL, NORTE e LATERAIS SEM furos; regiao da
  porta selada. lab_simples agora com 173 partes (2 novas).
- database.json: nota do lab_simples atualizada (173 partes, z-118.42, cantos fechados).

## Observacoes
- Pesquisas de sci-fi/futurista no Creator Store estao retornando lixo (assets "car dealer").
  Tentar queries mais especificas em sessao futura (ex.: "spaceship hangar", "futuristic base").
