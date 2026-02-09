# 🧪 INSTRUÇÕES DE TESTE - Pipeline CI/CD

## ✅ O QUE FOI PREPARADO

Todas as pipelines estão configuradas e prontas. Agora vamos validar:

### **Teste 1: Acessar o Painel de Ações (Actions)**

Para Ver TODOS os workflows (CI/CD) em ação:

```
https://github.com/senaiHeitor/TRABALHO-05-02/actions
```

Você verá:
- ✅ Workflow "CD - Deploy GitHub Pages" (deve estar PASSING/verde)
- ⚠️ Ainda não há CI rodando (precisa de PR)

---

## 🔴 Teste 2: Criar PR com ERRO para Testar Falha de CI

### **Passo 1:** Abra este link para criar o PR automaticamente:

```
https://github.com/senaiHeitor/TRABALHO-05-02/compare/main...feature/test-ci-validation
```

### **Passo 2:** Na página que abrir:
- Título: `test: Validar falha de CI com TODO`
- Descrição: `Este PR contém propositalmente um comentário TODO para validar se a pipeline bloqueia`
- Clique em: **"Create Pull Request"**

### **Passo 3:** Aguarde 30-60 segundos

- A pipeline CI **automaticamente** rodará
- Você verá um **❌ X vermelho** indicando falha
- Clique no X vermelho para ver os logs
- Esperado: **"Termos proibidos encontrados"**

---

## ✅ Teste 3: Corrigir o Erro e Revalidar

### **Passo 1:** Localmente, remova o TODO:

```powershell
git checkout feature/test-ci-validation
# Edite index.html e remova a linha: <!-- TODO: Adicionar links para LinkedIn e Twitter -->
git add index.html
git commit -m "fix: Remover comentário TODO"
git push
```

### **Passo 2:** Volte para o PR (já aberto no navegador)

- A pipeline CI rodará **novamente automaticamente**
- Desta vez você verá um **✅ checkmark verde** (passou!)
- Agora o botão **"Merge pull request"** estará **habilitado**

---

## 📊 Evidências para Entregar

### **Screenshot 1: CI Falhando (VERMELHO)**
Acesso: `GitHub > Actions > Pull requests > test: Validar falha...`
- Mostrar: ❌ Badge vermelha com "validar" falhando
- Mostrar: Logs com "Termos proibidos encontrados"

### **Screenshot 2: CD em Sucesso (VERDE)**
Acesso: `GitHub > Actions > Workflows > CD - Deploy GitHub Pages`
- Mostrar: ✅ Badge verde "passing"
- Mostrar: Histórico de deploys bem-sucedidos

### **Screenshot 3: GitHub Pages Ativo**
Acesso: `https://senaiHeitor.github.io/TRABALHO-05-02/`
- Site deve estar acessível e funcionando

### **Screenshot 4: Estrutura de Workflows**
Acesso: Browser > `.github/workflows/`
- Mostrar: `ci.yml`, `cd.yml`, `notify-failure.yml` existindo

---

## 🔒 Última Etapa: Proteger Branch (Opcional mas Recomendado)

Para garantir que o código **nunca** chegue em main sem passar por CI:

1. Abra: `https://github.com/senaiHeitor/TRABALHO-05-02/settings/branches`
2. Clique em **"Add rule"**
3. **Branch name pattern:** `main`
4. Marque: ✅ **"Require status checks to pass before merging"**
5. Selecione: `validar` (do arquivo ci.yml)
6. Salve

Pronto! Agora ninguém consegue fazer merge se a CI falhar.

---

## 📍 Links Rápidos de Acesso

| O que testar | Link |
|-------------|------|
| Dashboard de Actions | https://github.com/senaiHeitor/TRABALHO-05-02/actions |
| Criar PR com erro | https://github.com/senaiHeitor/TRABALHO-05-02/compare/main...feature/test-ci-validation |
| Ver workflow CI | https://github.com/senaiHeitor/TRABALHO-05-02/blob/main/.github/workflows/ci.yml |
| Ver workflow CD | https://github.com/senaiHeitor/TRABALHO-05-02/blob/main/.github/workflows/cd.yml |
| Settings (protege branch) | https://github.com/senaiHeitor/TRABALHO-05-02/settings/branches |
| GitHub Pages | https://senaiHeitor.github.io/TRABALHO-05-02/ |

---

**✨ Uma vez que você seguir esses passos, terá:**
- ✅ Print de CI em vermelho (falha com TODO detectado)
- ✅ Print de CD em verde (deploy bem-sucedido)
- ✅ Site funcionando no GitHub Pages
- ✅ Pipeline validando cada PR
- ✅ Repositório protegido contra código ruim

**Tempo estimado:** 3-5 minutos
