# 🚀 Guia de Deploy — Viver Bem no Firebase Hosting

## O que você vai precisar
- Node.js instalado (baixe em nodejs.org se não tiver)
- Conta Google com acesso ao projeto viver-bem-76a26

---

## PASSO 1 — Instalar o Firebase CLI

Abra o terminal (Prompt de Comando no Windows) e rode:

```bash
npm install -g firebase-tools
```

---

## PASSO 2 — Fazer login no Firebase

```bash
firebase login
```

Vai abrir o navegador — faça login com sua conta Google (a mesma do Firebase).

---

## PASSO 3 — Entrar na pasta do projeto

Coloque os arquivos do Viver Bem numa pasta chamada `viver-bem` e entre nela:

```bash
cd viver-bem
```

A estrutura da pasta deve ser assim:

```
viver-bem/
  firebase.json
  .firebaserc
  public/
    index.html
```

---

## PASSO 4 — Fazer o deploy 🚀

```bash
firebase deploy --only hosting
```

Aguarde alguns segundos e vai aparecer:

```
✔ Deploy complete!
Hosting URL: https://viver-bem-76a26.web.app
```

---

## Seu app estará online em:

🌐 https://viver-bem-76a26.web.app
🌐 https://viver-bem-76a26.firebaseapp.com

---

## Para atualizar o app depois (quando fizer mudanças):

Edite o `index.html` e rode novamente:

```bash
firebase deploy --only hosting
```

Pronto! O app atualiza em segundos.

---

## ⚠️ Importante — Autorizar o domínio no Firebase Auth

Após o deploy, você precisa autorizar o domínio no Firebase Authentication:

1. Acesse console.firebase.google.com
2. Vá em Authentication → Settings → Authorized domains
3. Clique em "Add domain"
4. Adicione: `viver-bem-76a26.web.app`
5. Adicione: `viver-bem-76a26.firebaseapp.com`
6. Salve

Sem isso o login com Google não vai funcionar no domínio publicado.

---

## 🔒 Regras de segurança do Firestore (importante!)

No console do Firebase → Firestore → Regras, cole isso:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /usuarios/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

Isso garante que cada usuário só acessa os próprios dados.

---

## Resumo do que foi feito

✅ App completo com Firebase Authentication
✅ Firestore em tempo real (São Paulo - southamerica-east1)
✅ Login com Google e e-mail/senha
✅ Dados salvos na nuvem por usuário
✅ Dashboard, Transações, Metas, Hábitos, Relatórios com IA
✅ Modo sobrevivência e Rotina de estudos
✅ Pronto para publicar na web

---

Viver Bem v1.0.0 · Feito no Brasil 🇧🇷 · Powered by Claude IA
