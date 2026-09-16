# Admin Lanchão Massa

Painel administrativo do cardápio conectado ao Firebase Authentication e ao Cloud Firestore.

## Funcionalidades

O painel permite entrar com e-mail e senha, cadastrar produtos, editar nome, preço, descrição, categoria, disponibilidade e link público da foto, além de remover produtos. As mudanças são salvas na coleção `products` do Firestore.

## Configuração única no Firebase

1. No Firebase Console, abra o projeto `lanchao-98527`.
2. Em **Authentication > Sign-in method**, ative **E-mail/Senha**.
3. Em **Authentication > Users**, crie o usuário administrador.
4. Em **Firestore Database**, crie o banco em modo de produção.
5. Publique o arquivo `firestore.rules` para permitir leitura pública dos produtos e escrita apenas para usuários autenticados.

A chave do Firebase usada em `src/firebase.ts` é uma chave pública de aplicação web. A proteção real das alterações fica nas regras do Firestore e no login.

## Foto por link

No campo **Link da foto**, cole uma URL pública que termine em `.jpg`, `.jpeg`, `.png` ou seja servida por um CDN. O site público poderá carregar a imagem diretamente dessa URL. O link precisa permitir acesso sem login e sem bloqueio de domínio.

## Desenvolvimento

```bash
pnpm install
pnpm dev
pnpm build
```

Depois de conectar o site público à mesma coleção `products`, qualquer alteração salva neste painel será refletida automaticamente no cardápio.
