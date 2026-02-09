# Guia de Implementação - Pipeline CI/CD

## ✅ O que foi implementado

### 1. **Estrutura do Projeto**
- ✅ `index.html` na raiz (obrigatório para GitHub Pages)
- ✅ `style.css` com estilos personalizados
- ✅ Pasta `images/` com arquivo SVG placeholder
- ✅ `README.md` com badges de status da pipeline

### 2. **Pipeline CI (Integração Contínua) - `ci.yml`**

Dispara automaticamente em **Pull Requests** para a branch `main`.

**Validações implementadas:**

| Validação | Descrição | Comando |
|-----------|-----------|---------|
| ✅ Verificação de `index.html` | Garante que o arquivo principal existe na raiz | `test -f index.html` |
| ✅ Linter HTML | Valida sintaxe HTML com HTMLHint | `htmlhint index.html` |
| ✅ Tamanho de arquivos | Bloqueia arquivos > 500KB | `find . -type f -size +500k` |
| ✅ Termos proibidos | Detecta TODO, FIXME, senha, password | `grep -R -i -E "TODO\|FIXME\|senha\|password"` |
| ✅ Validação de links | Testa URLs internas e externas com Linkinator | `linkinator index.html --recurse` |
| ✅ Matrix Strategy | Testa em Node.js 18 **e** 20 simultaneamente | Configurado em `strategy.matrix` |

**Comportamento:**
- Se **qualquer validação falhar**, o merge fica bloqueado automatically
- Apenas com todas as validações passando o botão "Merge" aparece habilitado

### 3. **Pipeline CD (Entrega Contínua) - `cd.yml`**

Dispara automaticamente quando código é mergeado para `main`.

**O que faz:**
1. Faz checkout do código
2. Configura o GitHub Pages
3. Upload de todos os arquivos como artefato
4. Deploy automático para GitHub Pages

**Permissões necessárias:**
```yaml
permissions:
  contents: read      # Ler conteúdo do repositório
  pages: write        # Escrever no GitHub Pages
  id-token: write     # Gerar token de identidade
```

### 4. **Notificação de Falhas - `notify-failure.yml`**

Novo workflow que:
- Dispara quando CI falha
- Exibe um resumo da falha
- Fornece link direto para os logs da ação

## 🚀 Como Testar a Pipeline

### Teste 1: Validar que CI passa com código correto (main)
```bash
git checkout main
git pull origin main
# Verificar https://github.com/SEU_USUARIO/SEU_REPO/actions
# A pipeline CD deve estar em status "passing" (verde)
```

### Teste 2: Testar falha da CI propositalmente

**Passo 1:** Criar um branch de teste
```bash
git checkout -b teste-erro-ci
```

**Passo 2:** Introduzir um erro (ex: adicionar TODO)
```html
<!-- Editar index.html -->
<!-- TODO: Melhorar design --> <!-- ❌ Vai falhar! -->
```

**Passo 3:** Fazer commit e push
```bash
git add index.html
git commit -m "test: Adicionar TODO para testar CI"
git push -u origin teste-erro-ci
```

**Passo 4:** Criar Pull Request no GitHub
- Acesse: `https://github.com/SEU_USUARIO/SEU_REPO`
- Clique em "Compare & pull request"
- Crie o PR com título relevante
- A pipeline CI **deve falhar** automaticamente ✅

**Resultado esperado:**
- ❌ Badge vermelha na página do PR
- ❌ Botão "Merge" desativado
- ❌ Logs mostrando: "Termos proibidos encontrados"
- ❌ Notificação de falha (navigate-failure.yml dispara)

### Teste 3: Corrigir e re-testar
```bash
# Remover o comentário TODO
git add index.html
git commit -m "fix: Remover comentário TODO"
git push
# A pipeline CI vai rodar novamente automaticamente
# Desta vez deve passar ✅
```

## 📊 Badges de Status

Os badges no README.md mostram status em tempo real:

```markdown
[![CI Status]()](https://github.com/SEU_USUARIO/SEU_REPO/actions?query=workflow%3A...)
[![CD Status]()](https://github.com/SEU_USUARIO/SEU_REPO/actions?query=workflow%3A...)
```

**Como ele funciona:**
- GitHub gera automaticamente a imagem do badge
- A cor muda conforme o status (passing = verde, failing = vermelho)
- Clique no badge para ver os logs detalhados

## 🔒 Proteção de Branch

Para ativar proteção de branch (obrigatório):

1. Acesse: `Settings` → `Branches` → `Branch protection rules`
2. Clique em "Add rule"
3. Padrão de nome da branch: `main`
4. Ative: "Require status checks to pass before merging"
5. Selecione: `validar` (job do ci.yml)
6. Salve

A partir de então:
- PRs não podem ser mergeados se CI falhar
- Assim garante que apenas código validado chega em produção

## 📍 Próximos Passos

1. **Configurar colaboradores:**
   - Settings → Collaborators → Adicionar: `09116428-collab`

2. **Acessar o site:**
   - Vá para: `https://github.com/SEU_USUARIO/SEU_REPO/settings/pages`
   - Confirme que GitHub Pages está ativado
   - URL do site: `https://SEU_USUARIO.github.io/SEU_REPO/`

3. **Monitorar pipelines:**
   - Abas: `Actions` → Clique em qualquer workflow para ver logs completos

## 🎯 Checklist de Entrega

- [ ] ✅ Estrutura de pastas `.github/workflows/` com `ci.yml`, `cd.yml`, `notify-failure.yml`
- [ ] 📸 Print de falha (CI vermelha com erro de TODO/FIXME)
- [ ] 📸 Print de sucesso (Actions mostrando Deploy concluído)
- [ ] 🔗 Link do GitHub Pages funcionando
- [ ] 👥 Colaborador `09116428-collab` adicionado
- [ ] 🛡️ Branch main protegida (opcional mas recomendado)

## 📞 Suporte

**Dúvidas comuns:**

**P: Por que o merge está desativado?**
R: A pipeline CI falhou. Clique no X vermelho para ver os erros nos logs.

**P: Como linkinator valida URLs com porta?**
R: Linkinator testa URLs internas (relativas) e externas. Certifique-se de que links apontam para URLs válidas.

**P: Matrix strategy está funcionando?**
R: Sim! A pipeline roda 2x para cada commit - uma vez com Node.js 18 e outra com 20.

---

**Implementado em:** 09/02/2026
