# 🌐 Guia de Publicação do Portal de Onboarding na Internet

Este guia explica como colocar o portal web de onboarding online com um **link público com SSL (HTTPS)** para enviar diretamente para seus clientes.

---

## 🚀 Opção 1: Direto na sua VPS via Coolify (Recomendado)

Como você já tem o **Coolify** rodando na VPS com Docker, n8n e Evolution API, você pode rodar este portal como mais um serviço leve (consome menos de **10 MB de RAM** com Nginx Alpine).

### Passo a Passo no Coolify:
1. Acesse o painel do seu **Coolify**.
2. Clique em **+ New Resource** (Novo Recurso) no seu projeto.
3. Escolha uma das opções:
   - **Opção A (Via Git):** Conecte o repositório GitHub onde estão estes arquivos. Aponte o diretório base para `apps/izy-coach-onboarding-web`. O Coolify detectará o `Dockerfile` automaticamente.
   - **Opção B (Via Dockerfile ou Docker Compose direto):** Crie uma aplicação vazia, copie o conteúdo de `Dockerfile` e `index.html`.
4. No campo **Domains / FQDN**, defina o seu subdomínio público, por exemplo:
   ```text
   https://onboarding.odiretorcriativo.com
   ```
   *(ou `https://onboarding.seudominio.com` / subdomínio padrão do Coolify com nip.io).*
5. Clique em **Deploy**.
6. O Coolify (via Traefik) gerará automaticamente o certificado SSL (HTTPS Let's Encrypt).
7. Pronto! Seu portal estará acessível em qualquer smartphone ou computador do mundo.

---

## ⚡ Opção 2: Cloudflare Pages (Grátis, Global e Zero Carga na VPS)

Se preferir não usar memória nem portas na sua VPS para servir arquivos HTML estáticos:
1. Acesse o painel da **Cloudflare** -> **Workers & Pages** -> **Create application** -> **Pages**.
2. Conecte ao seu GitHub e aponte para a pasta `apps/izy-coach-onboarding-web`.
3. Clique em **Save and Deploy**.
4. Você terá uma URL pública instantânea (ex: `https://izy-onboarding.pages.dev`) e pode apontar seu domínio próprio (`https://onboarding.odiretorcriativo.com`) em 1 clique.

---

## 📲 Como Usar no Gerador de Links

Quando você abrir o portal (seja localmente em `localhost:3000` ou já no link de produção):
1. Clique no botão **`[ GERAR LINK DE CLIENTE ]`** no topo.
2. No campo **1. Domínio Público do Portal**, informe sua URL pública (ex: `https://onboarding.odiretorcriativo.com`).
3. O portal guardará essa URL no seu navegador e **nunca mais gerará links com localhost**.
4. Cole a URL do webhook do n8n deste cliente e clique em **`Copiar Link`**.
5. Envie diretamente no WhatsApp do seu cliente!
