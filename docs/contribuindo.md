# Como Contribuir

Este site é open-source e cresce por contribuição da comunidade. Esta página explica como propor mudanças no conteúdo, no código ou na rede em si.

## 🌐 Tipos de contribuição

| Quero contribuir com... | Vá para |
| :--- | :--- |
| Texto, correção, nova página | Esta página |
| Foto do meu setup | [Galeria](galeria.md) |
| Hardware ou dinheiro para nó comunitário | [Financiamento](financiamento.md) |
| Local físico para repetidora | [Infraestrutura](infraestrutura.md) |
| Tempo (mutirão, simulado, palestra) | [Eventos](eventos.md) |
| Reportar relato de uso real | [Casos de Uso](casos-de-uso.md) |
| Falar problema de comportamento | [Código de Conduta](codigo-de-conduta.md) |

## 📝 Como editar este site

O site é escrito em Markdown e gerado com [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/). Para qualquer mudança você só precisa de um editor de texto e uma conta no GitHub.

### Edição rápida (uma página)

Para corrigir um erro de digitação ou adicionar um parágrafo:

1. Abra a página no site.
2. Clique no ícone de **lápis** no topo (✏️) — vai te levar ao GitHub.
3. Edite o Markdown direto pelo navegador.
4. Role até o fim, clique em **Propose changes**.
5. Envie um Pull Request com título descritivo.

A comunidade revisa e merge em poucos dias.

### Edição estruturada (várias páginas, nova feature)

Para mudanças maiores, clone o repositório e rode local:

```bash
git clone https://github.com/scmesh/scmesh.github.io.git
cd scmesh.github.io
uv sync
uv run mkdocs serve
```

Acesse `http://localhost:8000` — atualiza ao salvar.

Antes de abrir PR:

```bash
uv run mkdocs build --strict
```

Se passar sem erros, pode mandar.

## ✍️ Estilo editorial

Para o site manter coerência:

- **Português do Brasil**, tom direto, frase curta. Nada de "neste artigo abordaremos".
- **Cabeçalhos em sentence case**: "Como configurar", não "Como Configurar".
- **Listas com marcadores `-`** (não `*`).
- **Links inline**: `[texto](url)`. Evite footnote.
- **Código em blocos** com a linguagem (` ```bash`, ` ```yaml`).
- **Termos técnicos** definidos no [Glossário](glossario.md). Linke a primeira ocorrência por página.
- **Admonições** Material para destaques: `!!! tip`, `!!! warning`, `!!! note`. Não abuse.
- **Imagens** em `docs/img/<categoria>/`. Inclua `alt` descritivo.
- **Sem emoji decorativo** em parágrafos. Os atuais nos cabeçalhos vão ficar — não acrescente novos sem consenso.
- **Datas e preços** no formato BR (`12/04/2026`, `R$ 350`).
- **Coordenadas** em decimal com sinal, sem grau (`-26.91, -48.74`).

## 🔁 Padrão de commits

Commits descritivos no infinitivo:

```
Adiciona pagina de simulado 2026-Q2
Corrige link quebrado em hardware.md
Atualiza preco do RAK4631 em hardware.md
```

Evite:
- "Update X" (genérico).
- "Pequena correcao" (não diz o que).
- Commits com 20 arquivos modificados (separe por tema).

## 📐 Padrão de Pull Request

Título curto e descritivo. Corpo com:

```markdown
## Resumo
1-3 bullets do que mudou e por quê.

## Validação
- [ ] mkdocs build --strict passa
- [ ] Conteúdo factual checado em fonte
- [ ] Links externos funcionam
- [ ] Sem dados pessoais expostos

## Capturas (se UI/visual)
Screenshots ou recortes.
```

Para mudanças que afetam o protocolo da rede (canais padrão, PSK, role recomendado), abra **issue de discussão antes** do PR. Mudança em padrão precisa de consenso, não só de bom Markdown.

## 🐛 Reportar problema

Encontrou erro factual, link quebrado, informação desatualizada?

1. Cheque se já não há issue aberta sobre o tema.
2. Abra uma [nova issue](https://github.com/scmesh/scmesh.github.io/issues) com:
    - Página afetada (URL).
    - O que está errado.
    - Fonte da informação correta, se possível.
3. Se quiser corrigir você mesmo, mande PR direto referenciando a issue.

## 🛡️ Antes de mergear

Quem revisa PR observa:

- **Factual** — informação confere com fonte oficial?
- **Útil** — mudança ajuda mais que atrapalha?
- **Conciso** — texto enxuto, sem inflar parágrafos.
- **Seguro** — nada que exponha PSKs, contatos pessoais sem consentimento ou facilite abuso.

PRs bons saem em dias. PRs grandes ou polêmicos podem precisar de discussão pública no grupo antes.

## 📜 Licença

O conteúdo deste site é publicado sob licença permissiva — qualquer pessoa pode reutilizar, traduzir e adaptar, contanto que cite a fonte. Detalhes no [LICENSE](https://github.com/scmesh/scmesh.github.io/blob/main/LICENSE) do repositório (em definição).

Ao contribuir, você concorda em publicar sua contribuição sob a mesma licença.

## 🙏 Reconhecimento

Toda contribuição mergeada aparece automaticamente no histórico Git do repositório. Para colaborações sustentadas (operação de nó, organização recorrente de eventos), há reconhecimento na [Comunidade](comunidade-governanca.md).
