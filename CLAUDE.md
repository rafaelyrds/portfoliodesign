# Portfólio — Contexto do Projeto

> Este arquivo é o "briefing" do projeto. O Claude Code lê ele automaticamente
> no início de cada sessão. Mantenha-o atualizado conforme o site evoluir.

## O que é
Site de portfólio criativo de uma pessoa (design, fotografia e arte), feito para
mostrar trabalho a **clientes** e **recrutadores**. Hoje é um único arquivo
`index.html` (HTML + CSS + JS puro, sem build). O objetivo agora é evoluir para um
front mais sólido, mantendo a facilidade de adicionar/remover projetos.

## Decisões de design (já validadas — manter)
- **Tipografia:** fonte do sistema estilo Apple
  (`-apple-system, BlinkMacFontText, "SF Pro Display", "Inter", ...`), com Inter
  como fallback. Títulos em peso 800, letter-spacing negativo.
- **Cores:** fundo claro; acentos em **roxo** (`#6D4DE6`) e **verde** (`#16B981`).
  Já existe paleta para **modo escuro** via `[data-theme="dark"]`.
- **Modo claro/escuro:** botão sol/lua no topo (alterna `data-theme`).
- **Bilíngue PT/EN:** botão PT/EN no topo; textos vêm de um dicionário `i18n`.
- **Layout dos trabalhos:** mural estilo Pinterest (masonry com CSS `columns`,
  de 4 a 1 coluna conforme a tela). Cartões de alturas variadas.
- **Ordem da página:** apresentação (hero) primeiro, depois trabalhos, depois contato.

## Como os projetos funcionam (importante)
No `<script>` há uma lista `const projects = [...]`. Cada trabalho é um objeto:
`{ title:{pt,en}, cat, year, ratio, art }`. Adicionar = novo objeto; remover =
apagar o objeto; reordenar = mover. Filtros e contagem se atualizam sozinhos.
As imagens hoje são gradientes provisórios (`g1`..`g6`); a meta é trocar por
imagens reais (campo `img`).

## O que falta (próximos passos)
1. Substituir `[Seu Nome]`, e-mail e links de redes pelos dados reais.
2. Escrever a **copy** definitiva da apresentação (PT e EN) — fazer junto com o dono.
3. Trocar os gradientes por **imagens reais** dos projetos (otimizadas).
4. (Opcional) Persistir a preferência de tema/idioma com `localStorage`
   — funciona quando hospedado no próprio domínio.
5. (Opcional) Migrar para um front mais robusto (ex.: Astro ou Vite + componentes)
   mantendo o mesmo visual, se o dono quiser escalar.

## Convenções
- Sem dependências de build enquanto for um único arquivo; manter acessibilidade
  (foco visível, `prefers-reduced-motion`, contraste) e responsividade.
- Commits curtos e descritivos, em português, no imperativo.
- Hospedagem pretendida: **GitHub Pages** (arquivo principal = `index.html`).

## Rodar localmente
Abrir `index.html` no navegador (ou `python3 -m http.server` na pasta).
