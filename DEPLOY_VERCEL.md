# 🚀 Deploy no Vercel + GitHub + Turso (100% GRATUITO!)

## 📋 Pré-requisitos

- ✅ Conta no GitHub (gratuita)
- ✅ Conta no Vercel (gratuita)
- ✅ Conta no Turso (gratuita)

---

## Passo 1️⃣: Criar Conta no Turso (SQLite na Nuvem)

### 1. Acesse [turso.tech](https://turso.tech)

### 2. Clique em "Sign Up" e faça login com GitHub

### 3. Instale o Turso CLI no seu computador:

```bash
# macOS/Linux
curl -sSfL https://get.tur.so/install.sh | bash

# Windows (PowerShell)
irm get.tur.so/install.ps1 | iex
```

### 4. Faça login no Turso:

```bash
turso auth login
```

### 5. Crie seu banco de dados:

```bash
turso db create finance-app
```

### 6. Obtenha a URL do banco:

```bash
turso db show finance-app --url
```

**Copie essa URL!** Exemplo: `libsql://finance-app-seunome.turso.io`

### 7. Crie um token de acesso:

```bash
turso db tokens create finance-app
```

**Copie esse token!** Exemplo: `eyJhbGc...` (vai ser bem longo)

---

## Passo 2️⃣: Enviar Projeto para o GitHub

### 1. Crie um repositório no GitHub:
- Acesse [github.com](https://github.com)
- Clique em "New Repository"
- Nome: `finance-app`
- Deixe como **Public** (gratuito)
- **NÃO** marque "Initialize with README"
- Clique em "Create Repository"

### 2. No seu computador, extraia o projeto:

```bash
# Extrair o arquivo
tar -xzf finance-app-vercel.tar.gz
cd finance-app-vercel
```

### 3. Inicialize o Git e faça push:

```bash
# Inicializar git
git init

# Adicionar todos os arquivos
git add .

# Fazer primeiro commit
git commit -m "Initial commit - Finance App"

# Adicionar remote (substitua SEU-USUARIO pelo seu username do GitHub)
git remote add origin https://github.com/SEU-USUARIO/finance-app.git

# Renomear branch para main
git branch -M main

# Enviar para GitHub
git push -u origin main
```

---

## Passo 3️⃣: Deploy no Vercel

### 1. Acesse [vercel.com](https://vercel.com)

### 2. Clique em "Sign Up" e faça login com GitHub

### 3. Na dashboard, clique em "Add New..." → "Project"

### 4. Importe seu repositório:
- Encontre `finance-app` na lista
- Clique em "Import"

### 5. Configure as variáveis de ambiente:
No campo "Environment Variables", adicione:

**Nome:** `TURSO_DATABASE_URL`  
**Valor:** Cole a URL que você copiou no Passo 1.6

**Nome:** `TURSO_AUTH_TOKEN`  
**Valor:** Cole o token que você copiou no Passo 1.7

**Nome:** `NODE_ENV`  
**Valor:** `production`

### 6. Configure o Build:

**Framework Preset:** Selecione "Other"

**Build Command:**
```bash
cd client && npm install && npm run build
```

**Output Directory:**
```
client/dist
```

**Install Command:**
```bash
npm install && cd server && npm install && cd ../client && npm install
```

### 7. Clique em "Deploy" 🚀

**Aguarde 2-3 minutos...**

---

## ✅ Pronto! Seu App Está no Ar!

O Vercel vai te dar uma URL tipo:
```
https://finance-app-seunome.vercel.app
```

---

## 🔄 Atualizações Futuras

Sempre que você fizer mudanças:

```bash
git add .
git commit -m "Descrição da mudança"
git push origin main
```

**O Vercel vai fazer deploy automático!** 🎉

---

## 💰 Custos

- ✅ **GitHub:** R$ 0,00
- ✅ **Vercel:** R$ 0,00 (até 100GB de banda/mês)
- ✅ **Turso:** R$ 0,00 (até 500 DBs, 9GB armazenamento)

**Total: R$ 0,00/mês!**

---

## 🐛 Troubleshooting

### Erro: "Build failed"
- Verifique se as variáveis de ambiente estão corretas
- Verifique os logs no Vercel

### Erro: "Database connection failed"
- Confirme se TURSO_DATABASE_URL e TURSO_AUTH_TOKEN estão corretos
- Teste a conexão com: `turso db shell finance-app`

### Erro: "Cannot find module"
- Limpe o cache do Vercel: Settings → General → Clear Build Cache

---

## 📱 Domínio Customizado (Opcional)

Quer usar seu próprio domínio? (ex: minhasfinancas.com)

1. Compre um domínio (Registro.br, Namecheap, etc)
2. No Vercel: Settings → Domains
3. Adicione seu domínio
4. Configure o DNS conforme instruções

---

## 🎯 Desenvolvimento Local

Para rodar localmente (sem Turso):

```bash
cd finance-app-vercel
npm run install:all
npm run dev
```

O banco será SQLite local automaticamente!

---

## 🆘 Ajuda

- **Turso Docs:** https://docs.turso.tech
- **Vercel Docs:** https://vercel.com/docs
- **GitHub Docs:** https://docs.github.com

---

**Parabéns! 🎉 Seu app de finanças está online e 100% gratuito!**
