# Campeonato Brasileiro de Futebolinha

Web app (PWA) de campeonato de pontos corridos entre amigos, visual para crianças de 8 a 12 anos.
Projeto separado do app de escala (`../hcpa/escala`).

## Arquivos
- `index.html`: o app inteiro (CSS + JS). Estado em `localStorage`, chave `campeonato-pc-v2`.
- `times.js`: `GRUPOS` (abas do seletor) e `TIMES` (480 itens: `[nome, sigla, fundo, cor, grupo, arquivo, UF]`).
  Grupos: Brasil A–D (156), seleções da Copa 2026 (48, bandeiras do flagcdn.com), e clubes de ENG, ESP, ITA, GER, FRA,
  POR, NED, ARG, USA, MEX, KSA, TUR, BEL, SCO. Fontes: Wikipédia pt (Brasil) e en (resto, temporada 2026–27).
  **Os 156 primeiros itens nunca mudam de posição**: o time escolhido fica gravado pelo índice. Novos times só no fim.
  Sem cor definida, `corTime` gera uma a partir do nome.
- Seletor de time: botão na linha do jogador abre um painel (`abrirSeletor`) com busca, abas por liga e grade de escudos.
  Time já escolhido por outro jogador aparece desabilitado com o nome do dono.
- `escudos/<arquivo>.png`: ~120–160 px. Sem arquivo, aparece o escudo desenhado.
- `sw.js`, `manifest.webmanifest`, `icon*.png`, `apple-touch-icon.png`: PWA (offline e instalável).
  O app é guardado na instalação; cada escudo é guardado na primeira vez que aparece.
  Ao mudar qualquer arquivo, aumente `CACHE` em `sw.js` (hoje `futebolinha-v4`).

## Regras do jogo
- Vitória 3, empate 1, derrota 0. Desempate: pontos, vitórias, saldo, gols pró. Coluna Apr. = aproveitamento.
- Calendário pelo método do círculo (turno e returno opcional); folga se o número for ímpar.
- A tabela é ao vivo: conta todo jogo com placar (▲ ▼ ou cronômetro iniciado = 0×0), gravado ou não. "Gravar rodada" só trava a rodada.
- Placar por botões ▲ ▼ (0–99). Cada jogo tem cronômetro regressivo (padrão 3 min, `S.dur`, editável), com barra, ±10 s,
  apito aos 30 s, cliques cada vez mais rápidos nos últimos 15 s e apito final. Só um cronômetro roda por vez. Estado em `S.tm`.
- Jogador que sai tem os jogos anulados (pode reativar).
- Jogador novo no meio entra sem pontos e ganha rodadas extras no fim ("Entrada de Nome").
- Zonas: Libertadores (primeiros) e rebaixamento (últimos), padrão ≈ 1/5 dos jogadores, editáveis.

## Publicação
- GitHub Pages: https://msrodrigues.github.io/futebolinha/ (repo `msrodrigues/futebolinha`, branch `main`).
- Teste local: `python3 -m http.server` nesta pasta (service worker não registra em `file://`).

## Preferências
- Responder em português; soluções enxutas.
