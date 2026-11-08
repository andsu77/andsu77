# Guia de configuração do perfil

## 1. Repositório

O repositório precisa se chamar exatamente `andsu77` (mesmo nome do usuário) e ser **público**. O `README.md` da raiz aparece no perfil.

## 2. Estrutura

```text
andsu77/
├── README.md
├── assets/
│   ├── banner.svg
│   ├── divider.svg
│   └── cards/
│       ├── fila-zup.svg
│       ├── larissa-doces.svg
│       └── simeq.svg
├── .github/workflows/snake.yml
└── docs/README.md
```

O `snake.svg` e o dashboard não ficam em `assets/`: a cobra é gerada pelo workflow e publicada na branch `output`, e o dashboard vem de serviços externos com dados reais.

## 3. Publicar

1. Envie todos os arquivos para a branch `main` (mantenha a pasta `.github`).
2. Em **Settings > Actions > General > Workflow permissions**, escolha **Read and write permissions** e salve.
3. Abra **Actions > Gerar animação da cobra > Run workflow**.
4. Aguarde o fim (cerca de 1 minuto). A branch `output` será criada com `github-snake.svg` e `github-snake-dark.svg`.
5. Atualize a página do perfil. A cobra aparece na seção de atividade.

Depois disso o workflow roda todo dia às 03:00 UTC, manualmente e sempre que o arquivo `snake.yml` for alterado.

## 4. O que preencher

- **SIMEQ:** quando houver link (repositório ou demonstração), envolva a imagem no `README.md` com `<a href="...">`, conforme o comentário no arquivo. Edite também `assets/cards/simeq.svg` para trocar o texto "Link do repositório: a preencher".
- **Larissa Doces:** as tecnologias não foram informadas. Se quiser, troque os chips do card pela stack real.

## 5. Problemas comuns

- **Cobra não aparece:** confira se o workflow terminou com sucesso e se a branch `output` existe.
- **Erro de permissão (403):** revise o passo 2.
- **Cards de estatística lentos ou quebrados:** os serviços públicos (Vercel) têm limites de uso. Aguarde e recarregue.
- **Streak sem dados:** o serviço pode demorar a refletir contribuições recentes.

## 6. Segurança

O workflow usa só o `GITHUB_TOKEN` automático, com permissão `contents: write`. Nenhum segredo é necessário.
