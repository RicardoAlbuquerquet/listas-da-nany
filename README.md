# Listas da Nany 🏥

App simples para **guardar cirurgias com seus materiais e quantidades** e gerar, em um clique, o **PDF A4 do dia** — 4 cirurgias por folha, com linhas tracejadas (✂) no centro para **dobrar e cortar na régua**.

➡️ **Abrir o app:** https://ricardoalbuquerquet.github.io/listas-da-nany/

> Dica: depois de abrir, salve nos **Favoritos** do navegador (Edge ou Chrome) para entrar sempre rápido.

---

## Para que serve

Em vez de digitar tudo de novo todo dia, você **cadastra cada cirurgia uma vez** (nome + materiais + quantidades). No dia, é só **pesquisar pelo nome**, clicar em **+ dia** e **Baixar PDF**.

## Como usar (passo a passo)

1. **Cadastrar uma cirurgia** → botão **➕ Nova cirurgia**. Dê o nome, adicione os materiais com a quantidade (use os botões **−** e **+**). Clique em **✔ Salvar no catálogo**.
   - Atalho: dentro do editor, abra **“📋 Colar lista (rápido)”** e cole os materiais no formato `Material - quantidade` (um por linha) para preencher tudo de uma vez.
2. **Montar o dia** → no catálogo, **pesquise pelo nome** e clique em **+ dia** em cada cirurgia. Elas aparecem em **🗓️ Lista do dia** (dá para reordenar com ▲ ▼ ou remover com ✕).
3. **Gerar o PDF** → clique em **⬇ Baixar PDF**. Abra o arquivo e mande imprimir (não precisa mexer em nada da impressão).
4. **Editar / Excluir** → use os botões **✏️** e **🗑️** em cada cirurgia do catálogo.

## Seus dados estão seguros 🔒

- As cirurgias ficam salvas **no seu navegador** automaticamente — **nada é enviado para a internet**.
- **Backup automático (recomendado):** clique em **💾 Ativar backup automático** e escolha um arquivo. Se você salvar esse arquivo dentro de uma pasta do **OneDrive** ou **Google Drive**, suas cirurgias ficam guardadas também na nuvem — você **nunca perde nada**, mesmo trocando de computador. (Funciona no Edge/Chrome abrindo pelo link acima.)
- **Backup manual:** **⬇ Baixar backup** guarda uma cópia em um arquivo `.json`. Para repor (ou levar para outro computador), use **↩ Restaurar backup**.

---

## Notas técnicas (para quem mantém o código)

- **Um único arquivo:** [`index.html`](index.html) — HTML + CSS + JavaScript, **sem dependências externas**, 100% offline.
- **Gerador de PDF próprio** escrito à mão em JS puro (sem bibliotecas): escreve o PDF byte a byte (`PdfBuilder`/`Canvas`, fontes Helvetica/Helvetica-Bold/ZapfDingbats, métricas embutidas). A pré-visualização é um **renderizador SVG com a mesma geometria** (`drawPage`/`drawCard` recebem o renderer) → preview = PDF exato.
- **Parser:** divide cada linha no **último hífen** cujo texto seguinte começa com número (preserva sufixos como "cada"); linha sem número vira **título**.
- **Persistência:** `localStorage` (cópia de trabalho) + backup/restauração em `.json` + backup automático opcional via **File System Access API** (Chromium; só em `https`, por isso o link do GitHub Pages).
- **Os dados da Nany nunca vão para este repositório** — ficam apenas no navegador/arquivo dela.

### Rodar localmente

Basta abrir `index.html` com duplo clique no navegador. (No modo arquivo local o backup automático em arquivo não está disponível — use o backup manual.)
