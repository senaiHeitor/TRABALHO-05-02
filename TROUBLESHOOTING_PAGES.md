# 🔧 TROUBLESHOOTING - GitHub Pages Não Está Carregando

Se você vê **404** ao acessar https://senaiHeitor.github.io/TRABALHO-05-02/, siga os passos abaixo:

---

## ✅ **Passo 1: Verificar Status do Workflow CD**

Acesse: https://github.com/senaiHeitor/TRABALHO-05-02/actions/workflows/cd.yml

**Procure por:**
- Ver se há um workflow "CD - Deploy GitHub Pages" recente
- Verificar se está com ✅ **checkmark (passing)** ou ❌ **X (falhando)**

**Se estiver falhando:**
- Clique no workflow
- Veja a seção "Logs" para entender o erro
- Comum: Permissões incorretas ou branch configurado errado

---

## ✅ **Passo 2: Habilitar GitHub Pages**

Acesse: https://github.com/senaiHeitor/TRABALHO-05-02/settings/pages

**Procure pela seção "GitHub Pages" e veja:**

1. **"Source"** - Deve estar como:
   - Deploy from branch: **main** (ou gh-pages se preferir)
   - Folder: **/ (root)**
   - Salve se fez alterações

2. **Status** - Deve exibir:
   - 🟢 "Your site is published at: https://senaiHeitor.github.io/TRABALHO-05-02/"
   
3. Se não vir esse status:
   - Clique em **"Save"** novamente
   - Aguarde 2 minutos
   - Recarregue a página (F5)

---

## ✅ **Passo 3: Verificar Permissões do Workflow**

O arquivo `.github/workflows/cd.yml` deve ter estas **permissões exatas**:

```yaml
permissions:
  contents: read
  pages: write
  id-token: write
```

✅ **Está correto no seu arquivo!**

---

## ✅ **Passo 4: Forçar Novo Deploy**

Se tudo acima está OK, mas ainda mostra 404:

### **Opção A: via GitHub Web (Recomendado)**
1. Abra: https://github.com/senaiHeitor/TRABALHO-05-02
2. Clique em **"Actions"**
3. Selecione workflow **"CD - Deploy GitHub Pages"**
4. Clique em **"Run workflow"**
5. Escolha branch: **main**
6. Clique em **"Run workflow"**
7. Aguarde 2-3 minutos

### **Opção B: via Terminal (Git)**
```powershell
cd "c:\Users\rpv\Desktop\Heitor\TRABALHO0502"

# Fazer um commit simples (sem mudanças de código)
git commit --allow-empty -m "trigger: Forçar novo deploy em GitHub Pages"

# Push para disparar workflow
git push origin main
```

---

## ✅ **Passo 5: Aguardar 2-5 Minutos**

GitHub Pages pode levar até **5 minutos** para processar. Isso é normal!

- ⏳ Recarregue a página a cada 1 minuto: https://senaiHeitor.github.io/TRABALHO-05-02/
- Se vir o título **"Heitor Tavares"** → **Sucesso! ✅**
- Se continuar 404 → Continue com próximos passos

---

## 🔍 **Passo 6: Verificar Arquivo index.html**

Certifique-se que:

1. Arquivo `/index.html` **existe na raiz** do repositório
2. Não está em subpasta (não pode ser `docs/index.html` ou `public/index.html`)
3. Tem o conteúdo correto (não está vazio)

**Seu arquivo está ✅ correto!**

---

## 📋 **Checklist de Resolução**

- [ ] Acessei https://github.com/senaiHeitor/TRABALHO-05-02/actions/workflows/cd.yml
- [ ] Confirmo que hay um workflow CD com ✅ checkmark (passing)
- [ ] Acessei https://github.com/senaiHeitor/TRABALHO-05-02/settings/pages
- [ ] Confirmo que GitHub Pages está habilitado (Source: main branch, folder: /)
- [ ] Esperei 2-5 minutos
- [ ] Recarreguei o browser (Ctrl+F5 para limpar cache)
- [ ] **SITE ESTÁ ATIVO!** ✅ https://senaiHeitor.github.io/TRABALHO-05-02/

---

## 🆘 **Se Nada Funcionar**

Se você seguiu tudo acima e ainda vê 404:

### **1. Verificar se Repositório é Público**
- Vá para: https://github.com/senaiHeitor/TRABALHO-05-02/settings
- Procure **"Repository visibility"**
- Deve estar: **🟢 Public**
- Se estiver **🔒 Private**, mude para **Public**

### **2. Reexecutar CD Workflow**
- Vá para: https://github.com/senaiHeitor/TRABALHO-05-02/actions
- Selecione: **"CD - Deploy GitHub Pages"**
- Clique: **"Run workflow"** → **main** → **"Run workflow"**
- Aguarde 5 minutos

### **3. Limpar Cache do Browser**
```
No navegador:
- Pressione: Ctrl + Shift + Delete
- Escolha: "All time"
- Marque: "Cookies and cached images"
- Clique: "Clear data"
```

---

## 📞 **URLs Rápidas**

| O quê | Link |
|------|------|
| Ver Actions | https://github.com/senaiHeitor/TRABALHO-05-02/actions |
| Ver CD Workflow | https://github.com/senaiHeitor/TRABALHO-05-02/actions/workflows/cd.yml |
| GitHub Pages Settings | https://github.com/senaiHeitor/TRABALHO-05-02/settings/pages |
| Seu Site | https://senaiHeitor.github.io/TRABALHO-05-02/ |

---

**Tempo estimado de resolução:** 5 minutos

Se após 10 minutos continuar 404, o problema é likely do lado do GitHub (raro) ou configuração de permissões.
