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

## 2026-08-09 (sessao lab v7e - buraco circular no teto + mais destrocos)
- Usuario: "faça o buraco em cima em forma de circulo e com mais destroços".
- Teto: buraco retangular 28x16 (x66.15..94.15, z-152.42..-136.42) -> CIRCULAR.
  - Removidas 13 pecas da borda carbonizada retangular (Cobblestone na zona do furo).
  - Anel de 28 segmentos TetoAnel_1..28 (raio interno 8, externo 16.6, centro x80.15 z-144.42)
    preenchendo o teto ao redor do circulo e cobrindo os cantos do antigo retangulo. IMPORTANTE:
    primeira tentativa usou CFrame.Angles(0,t,0) e os blocos ficaram com o eixo longo na direcao
    errada (local Z <> radial), deixando buracos; corrigido com CFrame.lookAt(pos,pos+radial).
  - Borda carbonizada circular: 14 BordaCarbonizada (Cobblestone escuro) tangentes ao circulo.
- Mais destrocos:
  - 9 DetritoTeto no teto ao redor do furo + 7 DetritoAr caindo dentro do furo.
  - Pilha de 14 DetritoChao + 7 Vergalhao (rebar Metal) no chao abaixo do furo.
  - 10 Fuligem (manchas finas escuras) no topo do teto ao redor do furo.
  - 3 focos de fogo/fumaca novos na borda do furo: FxFuroCentral (Fire size 11 + Smoke 12),
    FxFuroOeste (7/8), FxFuroNorte (6/7). Fire/Smoke do chao (FxFogoCentral/Oeste) sobem pelo furo.
- Verificacao por raycast de cima (y30): dentro do circulo (r<7.2) SEM teto; fora (r>8.8) teto
  solido; cantos do antigo retangulo cobertos. Unicos pontos abertos do teto = o circulo.
- lab_simples com 252 partes (era 173; +92 criadas -13 removidas). database.json atualizado.

## 2026-08-09 (sessao lab v7f - limpeza: sem destrocos voando, sem fogo na borda)
- Usuario: "tire destroços voando" e depois "faltou um cubo pequeno e o fogo voando".
- Removidos em Workspace:
  - 7 DetritoAr (destrocos caindo dentro do furo) -> 252 - 7 = 245 partes.
  - 3 FxFuroCentral/Oeste/Norte (cubos 0.5 suspensos a y17.25 na borda do furo, com Fire+Smoke) ->
    eram o "cubo pequeno + fogo voando" -> 245 - 3 = 242 partes.
- Manteve: pilha de 14 DetritoChao + 7 Vergalhao no chao, 9 DetritoTeto, 10 Fuligem no topo do teto,
  Fire/Smoke do chao (FxFogoCentral/Oeste) subindo pelo furo.
- lab_simples com 242 partes. database.json atualizado.

## 2026-08-09 (sessao lab v7g - export unificado do lab_simples)
- Usuario: "esta vendo o interior do lab? salve tudo junto e uni em uma estrutura".
- Exportado o `lab_simples` inteiro (estrutura + interior + PortaLab + Fire/Smoke) como UM build:
  - Biblioteca MCP: `modern/lab_simples.json` (242 partes, bounds 84.8x17.7x53) via export_build
    (substituiu a entrada antiga de 115 partes).
  - Backup completo: `models/lab_simples.rbxm` (13.4 KB) via export_rbxm, inclui as 2 Fire + 2 Smoke
    e o modelo PortaLab (22 partes). O ProximityPrompt NAO vai no arquivo porque e criado em runtime
    pelo ServerScriptService.PortaController (script fica fora do modelo).
  - Verificada a integridade por re-import: 242 partes, fire=2, smoke=2, tetoAnel=28; duplicata
    removida do Workspace.
- database.json atualizado.

## 2026-08-09 (sessao lab v7h - unificacao LabCidade)
- Usuario: "uni e salve o laboratorio, junto com o chao da cidade e carros".
- Criado no Workspace o Model unificado `LabCidade` com 4 filhos (total 669 BaseParts):
  - `Cidade` (Folder): chao 602x0.4x602.3 (1 UnionOperation, min(-308.2,0,-38.4) max(293.8,0.4,563.8)).
  - `vehicle_red`: MeshPart 13.9x5.7x6.0 (min(-181.6,0.4,95.1)).
  - `crashed car`: Model 425 partes (9.4x6.4x17.2).
  - `lab_simples`: Model 242 partes (min(66.2,0.4,1.1) max(151,18.1,54.1), size 84.8x17.7x53).
- `Workspace.Model` original mantido com 10 filhos (Chemicals, Goo Containers etc.).
- Exportado:
  - Biblioteca MCP: `modern/lab_cidade.json` (669 partes, bounds [602,18.1,602.3]) via export_build.
  - Backup completo: `models/lab_cidade.rbxm` (925.6 KB) via export_rbxm (inclui Fire/Smoke).
- database.json atualizado (entrada `modern/lab_cidade`).

## 2026-08-09 (sessao lab v7i - itens do lab no LabCidade)
- Usuario: "falta os itens dentro do laboratorio".
- Movidos os 10 filhos de `Workspace.Model` para dentro de `LabCidade.lab_simples` (96 partes):
  Chemicals (2), Goo Containers (2), frascos/garrafas com liquido (Cork/Liquid/Handle/Bottle),
  MyDesk, Office Chair, luzes (LightConfig), mesas/bancadas, cubos de gelo com luz neon, etc.
  Ja estavam posicionados dentro do lab (x73..144, z2..36); apenas re-parentados.
- lab_simples: 242 -> 338 partes. LabCidade: 669 -> 765 BaseParts.
- `Workspace.Model` ficou vazio e foi removido.
- Re-exportado:
  - Biblioteca MCP: `modern/lab_cidade.json` (765 partes, bounds [602,23.7,602.3]) via export_build.
  - Backup completo: `models/lab_cidade.rbxm` (988.6 KB) via export_rbxm (inclui Fire/Smoke,
    ParticleEmitters e Script/Chemicals; script da porta fica fora do modelo).
- database.json atualizado.

## 2026-08-09 (sessao lab v7j - movimentacao unificada + backup total)
- Problema relatado: "itens nao se movem junto" ao arrastar o LabCidade (urânio, tambores, etc.).
- Causa 1: itens ancorados e sem welds ficavam para tras ao arrastar o chao.
- Causa 2: 11 modelos estavam SOLTOS no Workspace (fora do LabCidade): 5x Uranium Bar, 2x Barrel
  (UnionOperation), UraniumBomb, UNGROUP, Window Set, Model (36 partes). Foram movidos para dentro
  de `LabCidade` e soldados.
- Solucao de movimentacao unificada: todas as partes do LabCidade (exceto a folha deslizante da
  porta, 17 partes) desancoradas e soldadas via WeldConstraint ao hub unico ancorado
  `LabCidade.Cidade.Sinalizacao.Union`. Assim arrastar o chao move o lab inteiro com todos os itens.
  (WeldConstraint em partes ancoradas nao propaga arrasto no Studio; por isso desancorou-se o conjunto.)
- PortaController corrigido: buscava `workspace.lab_simples` mas o lab agora esta dentro de LabCidade.
  Agora usa `workspace:WaitForChild("LabCidade"):WaitForChild("lab_simples")`.
- Total: 801 BaseParts em LabCidade. Re-exportado:
  - Biblioteca MCP: `modern/lab_cidade.json` (801 partes, bounds [602,23.7,602.3]).
  - Backup completo: `models/lab_cidade.rbxm` (1.030.415 bytes).
- BACKUP TOTAL solicitado pelo usuario ("salvar tudo pra se eu errar voltar ao estado atual"):
  - `models/labdna_scripts.rbxm` (2.911 bytes): ServerScriptService.PortaController + Script + PLAYERDATA.
  - `models/labdna_ui_remotes.rbxm` (8.555 bytes): StarterGui.InterfaceNivel + ReplicatedStorage.RemoteEvents.
  - `backups/lab_cidade_buildlibrary_801.json` (109.489 bytes): copia do JSON da biblioteca MCP.
  - Nova pasta `backups/` criada no repo.
- database.json atualizado (entry modern/lab_cidade: 801 partes, notas de solda/backups).

## 2026-08-11 (sessao Place1 - ovo pickavel)
- Novo build `misc/ovo_verde_01`: ovo verde de galinha (1 Part Ball SmoothPlastic verde, 1.6x2.2x1.6)
  em `Workspace.OvoVerde` (pos 4,1.1,0), ProximityPrompt (E, dist 7) + `ServerScriptService.OvoVerdeScript`.
- Mecanica: E pega o ovo -> vira Tool "Ovo Verde" no Backpack (handle anc=false col=false, prompt off);
  clique com a tool -> solta o ovo na frente do jogador e respawna o modelo com prompt.
- Bug encontrado/corrigido: forward declaration `local connectEgg` (referencia antes da declaracao
  resolvia p/ nil e abortava antes do tool:Destroy).
- Ciclo completo testado no playtest (pega -> solta -> pega). Exportado na biblioteca MCP.
- Explorado: plugins de textura/iluminacao no Creator Store (LightForge 134789936186393,
  Texture Library Tool 4822976854 etc.) — download bloqueado (assetdelivery 401, precisa auth da Toolbox).
- Ovo atualizado: renomeado para "ovo estranho", material NEON (verde claro) + PointLight
  (BrilhoNeon, Brightness 2, Range 12). Script e prompt atualizados (WaitForChild("ovo estranho"),
  tool "ovo estranho", ObjectText "ovo estranho"). Biblioteca re-exportada (palette Neon).
- Cor ajustada para NEON VERDE classico #39FF14 (Color3(57,255,20)) no material e no PointLight.
- Galinha verde criada: primeiro versao em blocos (10 partes: corpo/cabeca/crista/bico/barbela/cauda/asas/pernas),
  mecanica de segurar igual ao ovo (prompt E + tool com welds). Depois a SKIN foi MELHORADA em 3D:
  modelo gerado por IA (GenerationService Body1, 1 MeshPart 1.23x1.91x1.83) verde SmoothPlastic,
  substituindo a de blocos. GalinhaVerdeScript usa PrimaryPart como Handle da tool.
  Backup em models/galinha_verde.rbxm. Registrado em localBuilds misc/galinha_verde_01.
- Tamanho da galinha DOBRADO (2.46x3.83x3.66, BASE_Y=1.91).

## 2026-08-11 (sessao Place1 - galinha de partes)
- Diagnostico: a galinha IA estava SEM MESH (MeshPart body_geom com MeshId vazio) — renderizava como
  bloco verde e sem skin na mao. 2 geracoes (galinha_3d, galinha_3d_v2) falharam igual (MeshId="").
- Confirmado que plugin NAO abre UI do Studio (docs do StudioService so tem PromptImportFile(s));
  simulador de teclado/mouse so age no jogo em playtest. Nao da para abrir Game Settings por script.
- Galinha reconstruida COM PARTES (14 pecas SmoothPlastic, verde 86,200,86; crista+barbela vermelhas
  220,40,40; bico+pernas+pes laranja 255,140,40): Handle corpo Ball 1.9x2x1.7, Cabeca Ball,
  Crista1-3, Bico, Barbela, Cauda (rot -45), AsaEsquerda/Direita Ball, PernaEsquerda/Direita,
  PeEsquerdo/Direito. PrimaryPart=Handle. Substituiu o mesh quebrado em Workspace["galinha verde"].
- GalinhaVerdeScript: BASE_Y 1.91 -> 1.5; soltar agora usa SetPrimaryPartCFrame (corpo = pivo do
  modelo, patas no chao) em vez de PivotTo. Ciclo pega/solta testado de ponta a ponta em playtest
  (E pega -> tool com 14 partes no backpack; clique -> galinha no mundo com menorY 0.12 + prompt).
- Upgrade futuro p/ mesh real: habilitar "Allow Loading Third Party Assets" (Game Settings > Security)
  e inserir galinha do Creator Store (candidatas 4376443752 "Chicken" ou 117701041346529
  "Stylized Chicken"; preview/insert bloqueado sem a permissao).
- database.json: entrada misc/galinha_verde_01 atualizada (14 partes, bounds [2.3,3.1,2.1]).

## Observacoes
- Pesquisas de sci-fi/futurista no Creator Store estao retornando lixo (assets "car dealer").
  Tentar queries mais especificas em sessao futura (ex.: "spaceship hangar", "futuristic base").

## 2026-08-11 (sessao Place1 - galinha mesh IA FUNCIONANDO)
- Causa raiz encontrada: o tool MCP `generate_model` (e as chamadas antigas) usavam params errados,
  por isso o MeshPart retornava com MeshId='' e 0 triangulos (renderizava como bloco verde).
  Sintoma fechado: chamada direta com MaxTriangles>20000 era REJEITADA pelo backend
  ("MaxTriangles must be at most 20000 in inputs") — prova de que a assinatura certa chegava no servidor.
- FIX: GenerationService:GenerateModelAsync DIRETO com inputs corretos:
  {TextPrompt="cute green cartoon chicken...", Size=Vector3(2.5,3.5,3), MaxTriangles=20000,
  GenerateTextures=false} + schema {PredefinedSchema="Body1"} -> MeshPart 1.96x3.01x3 com ~17k triangulos.
- Provas de geometria REAL: scene analysis edit 7070 -> 24080 triangulos (+17010 = galinha);
  raycast do alto atinge a superficie (pos y=2.64, normal detalhada); tamanho fiel ao Size pedido.
  Mesh fica EMBUTIDA como EditableMesh (MeshId='' no inspector).
- LIMITACAO: a mesh embutida NAO sobrevive a export/import .rbxm (raycast do reimport = false;
  rbxm de 46KB quase igual ao vazio de 42KB). Persiste somente salvando o lugar (.rbxl, Ctrl+S) —
  mesmo comportamento de qualquer mesh gerada pela IA nativa do Studio. Backup via rbxm inviavel.
- Galinha montada no Place1: Workspace['galinha verde'] = Model (body > body_geom MeshPart verde
  SmoothPlastic, anc=true, pivot (6,1.5,2)), ProximityPrompt PegarGalinha (E, dist 8) dentro do mesh.
  GalinhaVerdeScript com BASE_Y=1.5.
- Ciclo completo testado em playtest: E pega -> Tool 'galinha verde' no backpack (Handle = MeshPart
  clonado, mesh preservada in-session); clique -> respawna galinha no mundo com prompt re-conectado.
  Verificado no edit apos parar o playtest: geometria continua real (raycast true).
- Models em partes (10 e 14 pecas) removidos/descartados. Screenshot nao verificavel por mim
  (modelo de IA sem suporte a imagem) — pedir confirmacao visual ao usuario.
- database.json atualizado (misc/galinha_verde_01: 1 MeshPart ~17k tris, bounds [2,3,3]).

## 2026-08-11 (sessao Place1 - galinha com TEXTURA)
- Usuario: "ficou sem divisao de cor e detalhes" (mesh verde chapado, GenerateTextures=false).
- Regenerada com GenerateTextures=true + prompt detalhado ("green body with light green belly,
  red comb and red wattle, orange beak, orange legs, white tail feathers"). MeshPart retornou
  com TextureContent=Content{Opaque} = textura EMBUTIDA com divisao de cor.
- Descoberta: MeshPart tem props MeshContent/TextureContent (novas, Content); MCP inspector e
  leitura por runtime mostram SourceType=None em server/client mas o raycast PROVA que a geometria
  existe no edit, no servidor e no cliente do playtest (limitacao de leitura do content embutido).
- Escala ScaleTo(1.6) -> 1.97x2.98x3.07 (igual ao tamanho da verde anterior). Renomeada p/ substituir
  a chapada em Workspace['galinha verde'] (pos 6,1.5,2). Clone verificado: preserva TextureContent.
- Ciclo pega re-testado no playtest (E -> Tool 'galinha verde' no backpack, Handle=MeshPart com textura).
- Lembrete ao usuario: salvar o lugar (Ctrl+S) para persistir mesh+textura embutidas no .rbxl.
- database.json atualizado (GenerateTextures=true, TextureContent embutida, bounds [2,3,3]).

## 2026-08-11 (sessao Place1 - galinha VISIVEL NO PLAY via geracao no servidor)
- Usuario: "ainda n da pra ver no play". CAUSA RAIZ descoberta: GenerationService no DM do EDIT
  cria MeshContent/TextureContent EMBUTIDOS (conteudo editavel local) que NAO replicam p/ o runtime.
  Prova: no playtest o body_geom tinha MeshContent=None (invisivel), apesar do raycast bater
  (colisao) e do EDIT renderizar (TextureContent=Opaque). Export .rbxm (edit E servidor) tambem
  perde o conteudo (42KB, reimport mesh=None).
- EXPERIMENTO DEFINITIVO: geracao DIRETA no servidor de um MULTIPLAYER playtest (cliente em
  processo separado) -> cliente ve mesh=Content{Opaque} tex=Content{Opaque} + raycast bate.
  Conclusao: gerar no servidor produz conteudo REAL que replica/renderiza de verdade.
- FIX: GalinhaVerdeScript reescrito p/ gerar a galinha no SERVIDOR a cada inicio de sessao:
  GenerateModelAsync (TextPrompt detalhado, Size 2.5x3.5x3, MaxTriangles=20000, GenerateTextures=true)
  com retry (6 tentativas/5s), ScaleTo(1.6) ~1.95x3.01x3.07, template no ServerStorage, spawn em
  Workspace (6,1.5,2) anc=true, ProximityPrompt PegarGalinha (E, dist 8). Mesma mecanica de pega/
  dropa (tool com Handle=MeshPart; clique respawna template com prompt re-conectado).
- Removida do edit a galinha estatica (conteudo embutido) — agora so existe a gerada no servidor.
- Testado no playtest: gerada apos ~1s, cliente ve mesh+tex Opaque, pega (tool no backpack),
  dropa (galinha com mesh+tex no workspace + prompt). Ciclo completo OK.
- TRADEOFF: 1 geracao por sessao/servidor (rate limit; ~1-30s ate aparecer); NAO visivel no DM
  do edit (so no play/published). Unica via funcional sem credenciais de upload (Open Cloud).
- database.json atualizado (misc/galinha_verde_01: geracao no servidor, conteudo real replicante).




## 2026-08-11 (sessao incubadora)
- Nova mecanica: ovo estranho -> incubadora -> choco -> galinha nasce FORA.
- Criado ServerScriptService.GalinhaModule (ModuleScript): gera o template da galinha no
  servidor (retry 6x/5s, ScaleTo 1.6, template em ServerStorage) e expoe ensureGenerated/
  waitTemplate/spawnChicken/makeTool. GalinhaVerdeScript agora so waitTemplate+spawnChicken(6,1.5,2).
- OvoVerdeScript: segurando o ovo (tool) e a <8 studs horizontais do workspace.Incubator,
  clicar COLOCA o ovo DENTRO da incubadora (pos -12,3.1,-6, anc=true, prompt desligado, wobble
  rotatorio). Apos 20s o ovo some e a galinha nasce FORA, em -12,1.5,-2.5 (frente da incubadora),
  via GalinhaModule.spawnChicken. Flag incubating evita 2 ovos simultaneos.
- Testado no playtest 2026-08-11: pega o ovo (prompt), clica perto da incubadora, ovo entra
  (-12,3.1,-6 dentro do bounding), apos 20s ovo destruido e galinha nova em -12,1.5,-2.5 com
  mesh Content{Opaque} (conteudo real). client-1 ve as 2 galinhas (6,1.5,2 e -12,1.5,-2.5).
- database.json atualizado (misc/ovo_verde_01 e misc/galinha_verde_01: mecanica da incubadora).

## 2026-08-11 (sessao incubadora v2 - botoes GUI)
- Mecanica trocada p/ botoes: GUI StarterGui.IncubadorGUI (painel embaixo no centro) com botao
  'INCUBAR' + botao 'ABRIR' + timer. LocalScript IncubadorClient mostra o painel quando o jogador
  fica a <25 studs da incubadora; INCUBAR visivel so segurando o ovo.
- Remotes: ReplicatedStorage.IncubarOvo / AbrirIncubador / IncubadorEstado.
- Servidor (OvoVerdeScript): INCUBAR valida (<20 studs, tem tool, nao incubando) -> remove tool,
  coloca o ovo DENTRO (-12,3.1,-6, anc=true, wobble) e broadcast {started=true}. Timer 20s no
  cliente (CHOCANDO: Xs) -> 'PRONTO! APERTE ABRIR' + botao ABRIR. ABRIR valida 20s, destroi o ovo
  e spawna a galinha FORA em -12,1.5,-2.5 (GalinhaModule.spawnChicken); broadcast {started=false}.
- Clique com o tool perto da incubadora agora NAO solta o ovo (usa o botao).
- Testado com cliques REAIS no playtest 2026-08-11 (simulate_mouse_input; nota: GUI hit-test usa
  espaco de tela cheia, somar ~58px do top inset): INCUBAR colocou o ovo, timer zerou, ABRIR
  destruiu o ovo e galinha nasceu em -12,1.5,-2.5. client-1 viu as galinhas.
- database.json atualizado (misc/ovo_verde_01 e misc/galinha_verde_01: botoes INCUBAR/ABRIR + timer).

## 2026-08-11 (sessao incubadora v3 - mensagem no topo)
- Mensagem da GUI movida p/ o TOPO da tela e estilizada: Frame 'MessageFrame' pill (AnchorPoint
  0.5,0, Y 70 por causa do inset de 58px do cliente, UICorner 28, UIStroke verde, fundo escuro
  translucido) + MessageLabel (GothamBlack, TextScaled, contorno preto).
- Textos/cores por estado: 'PEGUE O OVO E INCUBE!' (branco, sem ovo), 'APERTE INCUBAR PARA
  COLOCAR O OVO' (branco, com ovo), 'CHOCANDO OVO... Xs' (verde), 'PRONTO! APERTE ABRIR'
  (dourado + pulso de escala via TweenService 540x60<->500x56).
- Mensagem visivel mesmo afastado durante o choco (near OR incubating). Botoes INCUBAR/ABRIR
  com UICorner arredondado.
- Testado no playtest 2026-08-11: msg no topo y=12 (viewport), todos os estados + pulso
  confirmados; clique real em ABRIR (1028,699) nasceu a galinha fora e a UI resetou.
- database.json atualizado (misc/ovo_verde_01: mensagem no topo).

## 2026-08-11 (sessao incubadora v4 - interacao E na incubadora)
- BOTOES GUI REMOVIDOS. Incubar/Abrir agora sao ProximityPrompts E DIRETO NA INCUBADORA
  (dome Meshes/IceysAssetPack_Circle (1), dist 9, ClickablePrompt=false): prompt 'Incubar'
  (habilita qdo nao incubando) e prompt 'Abrir' (habilitado pelo servidor apos os 20s).
  Remotes IncubarOvo/AbrirIncubador deletados; so resta IncubadorEstado (broadcast p/ timer).
- GALINHA INICIAL AUTOMATICA REMOVIDA: GalinhaVerdeScript agora so garante o template
  (waitTemplate); a UNICA galinha nasce pelo choco na incubadora. Corrige o bug do jogador ver
  galinha 'spawnando ao por o ovo' (era a inicial aparecendo).
- Mensagem no topo mantida, textos ajustados p/ E: 'APERTE E PARA INCUBAR' / 'CHOCANDO OVO... Xs' /
  'APERTE E PARA ABRIR' (dourado + pulso).
- Testado no playtest 2026-08-11 com E real (simulate_keyboard_input): sem galinha inicial,
  E incuba (ovo dentro, tool consumido, Incubar desliga), timer 20s habilita Abrir, E abre
  (ovo destruido, galinha nasce em -12,1.5,-2.5, prompts resetados). client-1 ve 1 galinha.
- database.json atualizado (misc/ovo_verde_01 e misc/galinha_verde_01: interacao E, sem galinha inicial).

## 2026-08-11 (sessao incubadora v5 - galinha segue o jogador)
- NOVO: a galinha que nasce do choco agora SEGUE o jogador que abriu a incubadora.
  GalinhaModule.makeFollow(chicken, player): loop no servidor (task.spawn, tick 0.1s) move o
  MeshPart via CFrame (anc=true) em direcao ao jogador a ~8 studs/s, para a ~3.5 studs e vira
  p/ o jogador; encerra quando a galinha e destruida (pega). OvoVerdeScript passa o player de
  AbrirPrompt.Triggered -> finishIncubation(player) -> makeFollow.
- Testado no playtest 2026-08-11: galinha nasceu em -12,1.5,-2.5 e seguiu o jogador por ~40 studs
  (teleport p/ 30,1,10) ate parar a ~3.5 studs dele. Chicken droppada/clique continua sem follow.
- database.json atualizado (misc/ovo_verde_01 e misc/galinha_verde_01: makeFollow).

## 2026-08-11 (sessao incubadora v6 - animacao de andar + solta segue)
- ANIMACAO DE ANDAR procedural (mesh IA unica, sem esqueleto p/ animacoes R15): makeFollow agora
  tick 0.05s, hop vertical |sin(t*9)|*0.22 + balanceio tilt sin(t*9)*0.07 enquanto corre a 8 studs/s;
  parada = respiracao suave sin(t*4)*0.04; vira sempre p/ o jogador.
- GALINHA SOLTA DA TOOL TAMBEM SEGUE: makeTool.Activated -> Module.spawnChicken(pos, player)
  (antes spawnava sem follow); pegou a tool e soltou no playtest: a solta seguiu o jogador.
- CORRECOES DE FOLLOW no mapa (tem montanhas/picos gigantes ate y~378): (a) Anchored=true +
  CanCollide=false fixados no makeFollow -> imune a fisica; (b) altura da galinha = pe do jogador
  (root.Y-1.7), SEM raycast no XZ do jogador (subia picos que nao eram dele) e SEM subir o terreno
  do caminho (escalava montanha inteira). Agora atravessa picos que nao estao sob o jogador.
- Testado no playtest 2026-08-11: fluxo completo (ovo->Incubar E->20s->Abrir E->galinha nasce e
  segue com hop visivel, Y oscilando 1.63-1.82 durante a corrida); tool drop segue; altura do pe
  correta (char root 3.3 -> galinha y~1.6).
- database.json atualizado (misc/ovo_verde_01 e misc/galinha_verde_01: animacao de andar + solta segue).

## 2026-08-11 (sessao incubadora v7 - nome/tag + mensagem so com ovo)
- GALINHA RENOMEADA para 'Galinha Mutante' (modelo, Tool e prompt ObjectText; antes 'galinha verde').
- NOME VERDE ACIMA DELA: BillboardGui NameTag no MeshPart (Mesh) com TextLabel 'GALINHA MUTANTE'
  cor #39FF14, StudsOffset (0,3.2,0), MaxDistance=20 (aparece so de perto), AlwaysOnTop + contorno
  preto; Enabled=false nos clones da Tool (nao aparece segurando).
- MENSAGEM NO TOPO SIMPLIFICADA: IncubadorClient agora mostra 'APERTE E PARA INCUBAR' (branco) SO
  enquanto o jogador SEGURA o ovo a <25 studs da incubadora; oculta em qualquer outro estado.
  Mensagens de choco/abrir (CHOCANDO OVO... Xs, APERTE E PARA ABRIR + pulso) e 'PEGUE O OVO'
  removidas.
- CONFLITO DE PROMPTS corrigido: com a galinha seguindo, o E perto da incubadora pegava a galinha
  (prompt PegarGalinha dist 8 vs Incubar/Abrir dist 9). makeFollow agora desliga o prompt
  PegarGalinha quando o jogador seguido esta a <12 studs da incubadora.
- Testado no playtest 2026-08-11: nome/tag replicados no cliente (GALINHA MUTANTE, cor verde,
  MaxDistance 20); fluxo completo ovo->Incubar->20s->Abrir->galinha 'Galinha Mutante' nasce e segue
  sem o E pega-la; mensagem so com ovo segurando perto (oculta sem ovo e longe).
- database.json atualizado (misc/ovo_verde_01 e misc/galinha_verde_01: nome/tag + mensagem so com ovo).

## 2026-09-05 (sessao galinha nova)
- Usuario: "crie uma galinha no roblox". Studio lancado (baseplate) e galinha gerada por IA via
  `generate_model` (GenerationService Body1, 1 MeshPart 1.25x1.92x1.68, ~anima cowboy com textura:
  corpo branco, crista/barbela vermelhas, bico e pernas laranjas).
- Posicionada em `Workspace.Galinha` (0,3,0), ancorada. Nome do modelo "Galinha".
- Registrado em localBuilds `misc/galinha_01` no database.json; meta.lastUpdated = 2026-09-05.

## 2026-09-05 (sessao galinha de partes)
- Usuario: "esta legal, agora deixe ela e crie outra sem modelo 3d". A galinha IA (Galinha) ficou.
- Criada `Workspace['Galinha Partes']`: galinha feita SO de Parts (sem mesh/modelo 3D gerado),
  18 pecas SmoothPlastic (corpo/cabeca Ball amarelos, crista/barbela vermelhas, bico laranja,
  olhos pretos, asas, 3 penas de cauda, 2 pernas cilindro + pezinhos). Anc<, escala 0.62
  (bounds 1.2x1.9x1.0, altura igual a da galinha IA).
- Erros corrigidos ao longo do caminho: Enum.Shape nao existe (usar Enum.PartType); SetName nao e
  membro valido no runtime do MCP (usar p.Name=...); duplicatas de modelos parciais (0/1/18 partes)
  das tentativas que abortaram foram limpas (mantida a de 18).
- Pede confirmacao visual ao usuario (screenshot nao verificavel por este modelo de IA).
- Registrado em localBuilds `misc/galinha_partes_01` no database.json; commit + push.

## 2026-09-05 (sessao galinha low poly)
- Usuario: "faz uma low poly chicken". Criada `Workspace['Galinha Low Poly']`: galinha LOW POLY
  angular (15 Parts SmoothPlastic, sem mesh): Corpo+Cabeca Block amarelos, Bico Wedge laranja,
  Crista 2 blocos vermelhos inclinados, Barbela vermelha, olhos pretos, Cauda CornerWedge,
  asas finas anguladas, 2 pernas + pes laranjas. Escala 0.83 (pivo 10,0,0) -> bounds
  1.59x1.90x1.34 (altura 1.90 igual as outras galinhas).
- Screenshot nao verificavel por este modelo de IA; pedir confirmacao visual ao usuario.
- Registrado em localBuilds `misc/galinha_lowpoly_01`; commit + push.

## 2026-09-05 (sessao galinha low poly v2 - branca e detalhada)
- Usuario: "faltou mais detalhes quadrado e estrutura, e ser branca".
- Reconstruida `Workspace['Galinha Low Poly']` (v1 amarela destruida): galinha BRANCA com muito
  mais estrutura quadrada, 28 Parts SmoothPlastic: corpo em CAMADAS quadradas (Barriga 1.6x0.7x1.15,
  CostasMeio, CostasTopo, Peito), Pescoco+Cabeca Block, olhos cubos pretos, BICO em 2 cubos degrau
  laranjas (Bico1/Bico2), Barbela vermelha inclinada, CRISTA 3 cubos vermelhos em degrau, ASAS em
  placas empilhadas (2 camadas por lado), CAUDA 4 penas quadradas empilhadas p/ tras, PERNAS
  segmentadas (2 cubos cada) + pes laranjas.
- Escala 0.62 (pivo 10,0,0) -> bounds 1.49x1.90x1.07 (altura 1.90, igual as outras galinhas).
- Screenshot nao verificavel por este modelo de IA; pedir confirmacao visual ao usuario.
- Registrado em localBuilds `misc/galinha_lowpoly_02` (substitui o _01); commit + push.

## 2026-09-05 (sessao galinha low poly v3 - crista melhorada + menos bloco)
- Usuario: "melhore a crista e faça ela ficar com aspecto menor de um bloco".
- Reconstruida `Workspace['Galinha Low Poly']` (v2 destruida), 23 Parts brancas:
  - CRISTA MELHORADA: 6 bumps vermelhos (Ball) em semi-circulo ao longo do topo da cabeca
    (Crista1..6), estilo crista real de galinha (antes eram 3 cubos degrau).
  - Menos 'bloco': Corpo/Peito/Cabeca em Ball arredondado, Pescoco cilindrico, pernas cilindro
    laranja, asas Ball finas rotacionadas (15/-15 graus), cauda 3 penas Ball inclinadas (55/65,
    graus), bico Wedge laranja alongado, barbela Ball vermelha inclinada, olhos pretos.
- Escala 0.66 (pivo 10,0,0) -> bounds 1.42x1.90x0.88 (altura 1.90 igual as outras galinhas).
- Screenshot nao verificavel por este modelo de IA; pedir confirmacao visual ao usuario.
- Registrado em localBuilds `misc/galinha_lowpoly_03` (substitui o _02); commit + push.

## 2026-09-05 (sessao galinha low poly - REVERT p/ v2)
- Usuario: "nao aquele projeto anterior estava bem melhor" -> a v3 arredondada (23 partes, crista
  bump, menos bloco) foi REJEITADA.
- `Workspace['Galinha Low Poly']` RESTAURADA ao estado v2 (28 partes quadradas branco + detalhes,
  crista 3 cubos) e re-escalada (0.62, bounds 1.49x1.90x1.07). Registro do banco atualizado
  (misc/galinha_lowpoly_03 agora descreve o estado RESTAURADO v2). Commit + push.

## 2026-09-05 (sessao galinha low poly - asas maiores e ajustadas)
- Usuario: "ajuste as asas, maiores e arrumadas no corpo".
- Asas do `Workspace['Galinha Low Poly']` (v2 restaurada) ampliadas e encaixadas na lateral do
  corpo (z +-0.47): AsaE1/D1 principal 0.68x0.55x0.18 em (9.66,0.95,+-0.47) inclinada 18 graus;
  AsaE2/D2 inferior 0.60x0.40x0.18 em (9.74,0.62,+-0.47) inclinada 14 graus (asa de 2 placas
  sobrepostas). Substituiu as placas antigas 0.37x0.34.
- Obs: Studio minimizado durante a sessao (screenshot indisponivel); confirmar visualmente.
- database.json atualizado (misc/galinha_lowpoly_03: notas das asas). Commit + push.

## 2026-09-05 (sessao galinha low poly - brilho nos olhos)
- Usuario: "agora adicione brilhos nos olhos".
- Olhos do `Workspace['Galinha Low Poly']` com brilho: material mudado p/ Glass (brilhante) +
  pontinho branco especular adicionado em cada olho (BrilhoOlhoEsquerdo/Direito, Ball 0.05,
  SmoothPlastic branco 255,255,255) no canto frontal-superior (offset +0.03x,+0.028y,+0.03z).
- Obs: o usuario reposicionou o modelo no Studio (ago ~x5,z12.9); brilhos posicionados a partir
  da posicao atual dos olhos, ok.
- database.json atualizado (misc/galinha_lowpoly_03: olhos com brilho). Commit + push.

## 2026-09-05 (sessao galinha low poly - asas desprenderam ao mover)
- Usuario: "as asas nao estao no corpo". Causa: o modelo tinha sido MOVIDO no Studio
  (corpo agora em x-4.66,z-70.49) e as asas (e olhos com brilho) ficaram para tras — gap de
  ~4 studs em X e ~12 em Z (asas em x-0.18,z-82 vs corpo x-4.66,z-70.49).
- FIX 1: asas reposicionadas sobre o corpo (encaixadas na lateral, z +-0.47 do centro do corpo):
  AsaE1/D1 (-5.00,2.16,+-0.47) AsaE2/D2 (-4.92,1.83,+-0.47).
- FIX 2 (preventivo): TODAS as 29 partes soldadas via WeldConstraint ao hub CostasMeio
  (ancorado, vira PrimaryPart) — arrastar/mover o modelo não desprende mais nada.
  Mesma tecnica usada no LabCidade (2026-08-09).
- database.json atualizado (misc/galinha_lowpoly_03). Commit + push.

## 2026-09-05 (sessao galinha low poly - asas p/ a lateral FINAL)
- Usuario: "nao ficou certo" (apos o fix anterior). Perguntado; resposta: 'Posicao errada'.
- Causa: asas estavam nas posicoes de FRENTE/TRAS (eixo Z) mas a galinha 'olha' p/ o eixo Z
  (bico em +Z relativo ao corpo) -> asas deveriam estar na LATERAL (eixo X, esquerda/direita).
- FIX: AsaE1/D1 sz (0.18,0.55,0.66) e AsaE2/D2 (0.18,0.40,0.58) posicionadas em
  X = corpo +-0.545 (fina na lateral, comprida ao longo do corpo eixo Z), Z = centro do corpo,
  sem rotacao; welds recriados (29 no total).
- Obs: usuario continua movendo o modelo no Studio (corpo chegou em -1.62,1.97,-67.21);
  soldas mantem tudo junto.
- database.json atualizado (misc/galinha_lowpoly_03: FIX 2 final). Commit + push.
