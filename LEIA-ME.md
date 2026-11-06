# Site do LoopiServ

Página de apresentação do LoopiServ: o que é, como funciona, telas do sistema, para quem serve, quem faz, perguntas frequentes e um formulário de interesse.

## Antes de publicar

Abra `config.js` e preencha pelo menos um contato:

```js
window.LOOPISERV = {
  whatsapp: "5571999999999",       // país + DDD + número, só dígitos
  email: "contato@seudominio.com.br"
};
```

O formulário "Pedir demonstração" não precisa de servidor. Ele abre o WhatsApp do número configurado com a mensagem pronta (nome, empresa, tipo de serviço e tamanho da equipe). Sem WhatsApp, abre o e-mail.

## Como ver no computador

Dê dois cliques em `index.html`.

## Como publicar (grátis)

Qualquer hospedagem de site estático serve. Envie a pasta inteira, com `index.html`, `config.js` e `assets/`:

- **Netlify Drop**: arraste a pasta para app.netlify.com/drop.
- **Vercel**, **Cloudflare Pages** ou **GitHub Pages**: crie um projeto apontando para esta pasta.

Depois, ligue o seu domínio (ex.: loopiserv.com.br) nas configurações da hospedagem. O HTTPS vem incluído.

## Arquivos

- `index.html`: a página inteira, com estilos e scripts
- `config.js`: contatos (WhatsApp e e-mail)
- `assets/`: logos, símbolo e ícones da marca
- `assets/telas/`: prints do sistema em WebP (dados de exemplo), usados na seção "Veja o LoopiServ por dentro"

## Como refazer os prints do sistema

Os prints saem do sistema rodando com um banco separado, só com os dados de exemplo do seed. Nunca use o banco real (`storage/development.sqlite3`).

1. Na pasta do sistema, crie o banco de prints e suba o servidor:
   `DATABASE_URL=sqlite:./storage/prints.sqlite3 node scripts/seed.js` e depois
   `DATABASE_URL=sqlite:./storage/prints.sqlite3 PORT=3100 npm start`.
2. Capture em 1440x900 (desktop, salvo com 1600px de largura) e 390x844 (celular, em 2x).
3. Salve em `assets/telas/` em WebP, qualidade ~80.
4. Pare o servidor e apague `storage/prints.sqlite3`.
