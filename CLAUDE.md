# ely. — Contexto do Projeto

> Briefing que o Claude Code lê no início de cada sessão. Manter atualizado.

## O que é
Site da **marca pessoal `ely.`** (Rafaely Almeida — design e marketing), com os
trabalhos dela dentro. Não é mais "um portfólio": a marca vem primeiro, os cases
são a prova. Arquivo único `index.html` (HTML + CSS + JS puro, sem build).

## Identidade
- **Cores** (todas em tokens no topo do arquivo): principal `#DD073E`,
  dourado `#D8A649`, offwhite `#FFF7CD`, marrons `#493018` e `#301E0D`,
  fundo creme `#FFFDF4`, moldura areia `#E7DFCE`. Há paleta escura completa
  em `[data-theme="dark"]`.
- **Tipografia:** SF Pro (`-apple-system` puxa ela em Mac e iPhone), Inter como
  fallback fora do ecossistema Apple. Títulos em peso 900 com tracking negativo.
- **Logo:** SVG inline com `fill="currentColor"`, então acompanha o tema sozinha.
  Originais em `identidade/`.
- **Sem gradiente no layout.** Foi decisão dela: gradiente em texto e brilhos de
  fundo davam "cara de IA". O gradiente da marca só aparece no favicon.
- **Bilíngue PT/EN** por um dicionário `i18n`; **claro/escuro** por `data-theme`.

## Estrutura da página
Hero → Serviços → Trabalhos → Sobre → Contato. Tudo dentro de uma moldura
arredondada (`.shell`) sobre um fundo areia.

## Como os projetos funcionam
No `<script>` há `const projects = [...]`. Cada item:
`{ title:{pt,en}, cat, year, img, imgs, desc:{pt,en}, imgLayout }`.
- `img` = capa, em `trabalhos/<projeto>/capa.jpg`
- `imgs` = imagens do overlay, `trabalhos/<projeto>/01.jpg` em diante
- `imgLayout:"stack"` = uma imagem embaixo da outra (padrão: 3 colunas)
Adicionar = novo objeto; remover = apagar; reordenar = mover. Filtros e contagem
se atualizam sozinhos. Categorias em `catLabels`, ordem fixa em `renderFilters`.

## Regras de arquivo (importante)
- **Nomes de pasta e arquivo sem espaço, acento ou dois-pontos.** As pastas
  antigas tinham isso e quebravam em hospedagem que não fosse GitHub Pages.
- **Imagens no máximo 1600px de largura, JPEG qualidade 82.** As originais
  vinham com 3840px e vários MB cada.

## Publicação
- `main` é a branch publicada. GitHub Pages serve ela em
  https://rafaelyrds.github.io/portfoliodesign/
- **Mudança grande vai em branch**, e o merge na `main` só com aprovação dela —
  mesclar equivale a colocar no ar.
- Tag `v1-publicada` marca a versão anterior ao redesign de set/2026.

## Rodar localmente
O servidor de preview não consegue ler a pasta Downloads (proteção do macOS).
Espelhar em `/tmp/ely-preview` e servir de lá:
`rsync -a --delete --exclude .git --exclude .claude ./ /tmp/ely-preview/`
A entrada `ely` (porta 4545) do `~/.claude/launch.json` já aponta pra lá.
