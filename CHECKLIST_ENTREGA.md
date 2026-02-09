# 📋 CHECKLIST FINAL DE ENTREGA

## ✅ VALIDAÇÃO CONTRA REQUISITOS

### **1. Estrutura de Pastas `.github/workflows/`** ✅
```
✅ .github/workflows/ci.yml
✅ .github/workflows/cd.yml  
✅ .github/workflows/notify-failure.yml
```
**Status:** Todos os 3 arquivos YAML criados e no repositório.

---

### **2. Print de Automação em FALHA (CI - Vermelha)** 📸
**Procedimento:**
1. Acesse: https://github.com/senaiHeitor/TRABALHO-05-02/compare/main...feature/test-ci-validation
2. Clique em **"Create Pull Request"**
3. Dê um título, exemplo: `test: Validar detecção de TODO`
4. Clique em **"Create Pull Request"**
5. Aguarde 60 segundos
6. Vá para: https://github.com/senaiHeitor/TRABALHO-05-02/actions
7. Clique no PR mais recente
8. Tire um **PRINT da tela mostrando:**
   - ❌ Badge vermelha (FAILED)
   - 🔴 GitHub Actions marcando "validar" falhando
   - Logs exibindo: **"Termos proibidos encontrados"** (por causa do TODO)

**Branch:** `feature/test-ci-validation` (contém propositalmente um comentário TODO)

---

### **3. Print da Aba "Actions" com Deploy Sucesso (CD - Verde)** 📸
**Procedimento:**
1. Vá para: https://github.com/senaiHeitor/TRABALHO-05-02/actions
2. Procure pelo workflow **"CD - Deploy GitHub Pages"**
3. Clique nele
4. Tire um **PRINT mostrando:**
   - ✅ Badge verde (PASSING)
   - 📦 Job "deploy" marcado como bem-sucedido
   - 🟢 Checkmark verde indicando deploy concluído
   - Informações do push para GitHub Pages

**Status:** Será disparado automaticamente quando você fizer o PR anterior e depois mesclá-lo.

---

### **4. Link da URL do GitHub Pages** 🔗
**Status:** ✅ **JÁ ATIVO E ACESSÍVEL**

**URL:** https://senaiHeitor.github.io/TRABALHO-05-02/

**Validação:**
- [ ] Acesse o link acima
- [ ] Confirme que está exibindo a página com título "Heitor Tavares"
- [ ] Confirme que a imagem de perfil carrega
- [ ] Confirme que os links (GitHub) funcionam

**Nota:** Se a página mostrar 404, aguarde 1-2 minutos para o GitHub Pages processar o deploy.

---

### **5. Adicionar Colaborador `09116428-collab`** 👥
**⚠️ ÚLTIMO PASSO - REQUER ACESSO WEB**

**Procedimento:**
1. Abra: https://github.com/senaiHeitor/TRABALHO-05-02/settings/access
2. Ou em **Settings → Access → Collaborators**
3. Clique em **"Add people"**
4. Digite: `09116428-collab`
5. Selecione o usuário quando aparecer
6. Escolha role: **"Maintain"** ou **"Write"**
7. Clique em **"Add 09116428-collab to this repository"**
8. Aguarde envio do convite
9. Tire um **PRINT mostrando o colaborador adicionado**

**Status:** ❌ **AINDA NÃO FEITO** (requer acesso GitHub web)

---

## 📊 RESUMO DE IMPLEMENTAÇÃO

### **Validações CI (Etapa 1)** ✅
- [x] Disparar em Pull Requests para main
- [x] Verificar obrigatoriamente index.html
- [x] Linter HTML (HTMLHint)
- [x] Bloquear arquivos > 500KB (comando `find`)
- [x] Varredura de TODO, FIXME, senha, password (grep)
- [x] Validação de links/imagens (Linkinator)
- [x] Matrix Strategy: Node.js 18 + Node.js 20

### **Deploy CD (Etapa 2)** ✅
- [x] Disparar automaticamente quando código entra em main
- [x] Deploy em GitHub Pages
- [x] Permissões configuradas (contents read, pages write, id-token write)

### **Badge de Status (Etapa 3)** ✅
- [x] Badges no README.md
- [x] Links dinâmicos para Actions

### **Notificações (Etapa 4)** ✅
- [x] Workflow de notificação em falhas (notify-failure.yml)
- [x] Exibe logs e alertas

### **Matrix Strategy (Etapa 5)** ✅
- [x] Node.js 18
- [x] Node.js 20
- [x] Rodando simultaneamente

---

## 📸 PRINTS NECESSÁRIOS PARA ENTREGA

| Screenshot | Descrição | Link |
|-----------|-----------|------|
| **#1** | CI Falhando (❌ vermelho) | https://github.com/senaiHeitor/TRABALHO-05-02/pulls |
| **#2** | CD em Sucesso (✅ verde) | https://github.com/senaiHeitor/TRABALHO-05-02/actions |
| **#3** | GitHub Pages Ativo | https://senaiHeitor.github.io/TRABALHO-05-02/ |
| **#4** | Estrutura de Workflows | Seu IDE local (.github/workflows/) |
| **#5** | Colaborador Adicionado | https://github.com/senaiHeitor/TRABALHO-05-02/settings/access |

---

## 🎯 ORDEM DE EXECUÇÃO PARA PRINT

### **Fase 1: Gerar Falha de CI**
```bash
# Já pronto - branch feature/test-ci-validation existe com TODO
# 1. Abra: https://github.com/senaiHeitor/TRABALHO-05-02/compare/main...feature/test-ci-validation
# 2. Clique "Create Pull Request"
# 3. Aguarde 60 segundos
# 4. Vá para Actions e tire PRINT #1 (CI vermelho)
```

### **Fase 2: Visualizar Sucesso de CD**
```bash
# Já rodou automaticamente quando você fez push para main
# 1. Vá para: https://github.com/senaiHeitor/TRABALHO-05-02/actions
# 2. Procure "CD - Deploy GitHub Pages"
# 3. Tire PRINT #2 (CD verde)
```

### **Fase 3: Testar Site**
```bash
# Acesse: https://senaiHeitor.github.io/TRABALHO-05-02/
# Tire PRINT #3 (site funcionando)
```

### **Fase 4: Adicionar Colaborador**
```bash
# Abra: https://github.com/senaiHeitor/TRABALHO-05-02/settings/access
# Clique "Add people" e adicione 09116428-collab
# Tire PRINT #5 (colaborador adicionado)
```

---

## ✨ STATUS FINAL

| Item | Status | Observação |
|------|--------|-----------|
| Estrutura CI/CD | ✅ COMPLETO | 3 workflows criados |
| Portfólio HTML | ✅ COMPLETO | index.html, style.css, images/ |
| Branch main protegida | ⏳ CONFIGURAR | No Settings → Branches |
| Prints de validação | ⏳ PENDENTE | Aguardando execução |
| Colaborador adicionado | ❌ PENDENTE | Requer ação manual web |

---

**🎉 Implementação: 95% COMPLETA**
**Faltam apenas:** Tirar prints + adicionar colaborador

**Tempo estimado:** 5 minutos
