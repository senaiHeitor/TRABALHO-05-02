# 🚀 COMO HABILITAR GITHUB PAGES (PASSO A PASSO)

Se você está vendo página em branco ou 404 em https://senaiHeitor.github.io/TRABALHO-05-02/, siga EXATAMENTE estes passos:

---

## 📋 PASSO 1: Verificar se Repositório é PUBLIC

1. Abra: https://github.com/senaiHeitor/TRABALHO-05-02/settings
2. Procure por **"Repository visibility"** (seção "Danger zone")
3. **DEVE ESTAR:** 🟢 **Public**
4. Se estiver 🔒 Private, clique em **"Change visibility"** e mude para **Public**
5. **SALVE** as mudanças

---

## 📋 PASSO 2: Configurar GitHub Pages

1. **Abra:** https://github.com/senaiHeitor/TRABALHO-05-02/settings/pages
2. Você deve ver uma seção chamada **"GitHub Pages"**
3. Se não vir nada, significa que GitHub Pages não está habilitado ainda

### **CONFIGURAÇÃO NECESSÁRIA:**

#### **Source (Origem do Deploy)**
- [ ] Mude para: **Deploy from a branch**
- [ ] Escolha branch: **main**
- [ ] Escolha pasta: **/ (root)**
- [ ] Clique em **"Save"**

#### **RESULTADO ESPERADO:**
Você deve ver aparecer uma mensagem verde:
```
🟢 Your site is published at: 
   https://senaiHeitor.github.io/TRABALHO-05-02/
```

---

## 📋 PASSO 3: Verificar Pipeline CD

1. Abra: https://github.com/senaiHeitor/TRABALHO-05-02/actions/workflows/cd.yml
2. **Procure pelo workflow mais recente** (deve estar em cima)
3. Deve mostrar: **✅ Passing** (verde com checkmark)
4. Se estiver ❌ Red (falhando), clique nele e veja os logs

### **SE ESTIVER FALHANDO:**
- Clique no workflow
- Vá para **"Deploy"** step
- Leia a mensagem de erro
- Geralmente é por falta de permissões em GitHub Pages settings

---

## 📋 PASSO 4: Forçar Novo Deploy

Se após os passos acima ainda não funcionar:

### **Opção A: Renovar via Web**
1. Vá para: https://github.com/senaiHeitor/TRABALHO-05-02/actions
2. Procure por **"CD - Deploy GitHub Pages"** na lista esquerda
3. Clique nele
4. Clique em **"Run workflow"** (botão verde)
5. Escolha branch: **main**
6. Clique: **"Run workflow"**
7. Aguarde verde (2-3 minutos)

### **Opção B: Renovar via Terminal**
```powershell
cd "c:\Users\rpv\Desktop\Heitor\TRABALHO0502"

# Fazer commit vazio para disparar workflow
git commit --allow-empty -m "trigger: Renovar GitHub Pages"

# Push para GitHub
git push origin main

# Aguarde 2-5 minutos
```

---

## 📋 PASSO 5: Limpar Cache e Recarregar

Depois de fazer os passos acima:

1. **Aguarde 1-2 minutos** para GitHub processar
2. **Limpe o cache do navegador:**
   - Pressione: **Ctrl + Shift + Delete**
   - Escolha: **All time**
   - Marque: ☑️ Cookies and cached images
   - Clique: **Clear data**
3. **Recarregue o site:**
   - Acesse: https://senaiHeitor.github.io/TRABALHO-05-02/
   - Pressione: **Ctrl + F5** (reload forçado)
   - Aguarde carregar

---

## ✅ VOCÊ SABERÁ QUE FUNCIONOU QUANDO VER:

✅ Está no endereço: `https://senaiHeitor.github.io/TRABALHO-05-02/`
✅ Vê o título: **"Heitor Tavares"**
✅ Vê a foto de perfil em cima
✅ Vê as seções: Sobre, Habilidades, Projetos, Contato
✅ Pode navegar entre as seções
✅ A navbar volta ao topo ao clicar em links

---

## 🆘 CHECKLIST SE NÃO FUNCIONAR

- [ ] Repositório está **PUBLIC** (não private)
- [ ] GitHub Pages está **habilitado** em Settings > Pages
- [ ] Source está definido como **main branch, / folder**
- [ ] Workflow CD passou (checkmark ✅ verde)
- [ ] Aguardei **5 minutos** completos
- [ ] Limpei cache (**Ctrl+Shift+Del**)
- [ ] Recarreguei forçado (**Ctrl+F5**)
- [ ] Tentei em **outra aba** ou outro navegador
- [ ] Acessei exatamente este link:
  ```
  https://senaiHeitor.github.io/TRABALHO-05-02/
  ```

---

## 📍 LINKS PARA USAR

| AÇÃO | LINK |
|------|------|
| GitHub Pages Settings | https://github.com/senaiHeitor/TRABALHO-05-02/settings/pages |
| Repository Settings | https://github.com/senaiHeitor/TRABALHO-05-02/settings |
| Actions/Workflows | https://github.com/senaiHeitor/TRABALHO-05-02/actions |
| CD Workflow Specific | https://github.com/senaiHeitor/TRABALHO-05-02/actions/workflows/cd.yml |
| **SEU SITE** | **https://senaiHeitor.github.io/TRABALHO-05-02/** |

---

## 🎯 RESUMO RÁPIDO

```
❌ Problema: Site mostra 404 ou página em branco
✅ Solução: Habilitar GitHub Pages em Settings > Pages
           Source: main branch, / folder
           Salvar e aguardar 5 minutos
           Limpar cache e recarregar
```

---

## 💡 DICAS

1. **GitHub Pages leva tempo**: Pode levar até 5 minutos na primeira vez
2. **Cache é importante**: Sempre limpe com Ctrl+Shift+Del antes de recarregar
3. **Repositório deve ser PUBLIC**: Private repos precisam de upgrade pago para Pages
4. **Branch correta**: Certifique que é `main`, não `master`
5. **Pasta correta**: Deve ser `/` (root), não `/docs`

---

## 🔄 FLUXO ESPERADO

1. Você faz commit e push
2. GitHub dispara workflow CD
3. CD faz checkout, valida, faz upload, deploya
4. GitHub Pages recebe os arquivos
5. Após 2-5 min, site está ao vivo em:
   ```
   https://senaiHeitor.github.io/TRABALHO-05-02/
   ```

---

**Se seguir EXATAMENTE estes passos, o site estará funcionando em até 10 minutos. Comece pelo PASSO 1!**
