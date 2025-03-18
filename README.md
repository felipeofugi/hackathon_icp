# Melhoria de Design da página de edição do Gerador de Landing Pages On-Chain

Este projeto foi submetido ao Hackathon-3 da ICP-Brasil. Neste projeto objetiva-se melhorar a experiência de usuário na página de edição da Landing Page, do projeto existente "Gerador de Landing Pages On-Chain", que pode ser encontrado em: https://github.com/diogodcmdcm/geradorlp

---

## 🔐 **Funcionalidades Desenvolvidas**

- **Criação de três colunas na tela de edição da Landing Pega**: Na primeira coluna encontram-se as seções disponíveis, na segunda coluna encontram-se os botões de edição e na terceira é exibida uma prévia do site.
- **Criação e Edição Dinâmica**: É possível criar e personalizar landing pages com base em templates pré-definidos, com uma visualização da prévia do site no momento em que as edições estão sendo feitas, permitindo o ajuste de textos e imagens conforme necessário.
- **Publicação Imediata**: Com apenas alguns cliques, a página é publicada e disponibilizada na blockchain, garantindo acessibilidade global.
- **Gerenciamento Simples**: Usuários têm liberdade para criar, editar ou excluir suas páginas, conforme suas estratégias de marketing evoluem.

---

## ⚙️ **Como Utilizar**

1. **Conecte-se** ao DApp utilizando sua identidade via Internet Identity.
2. **Escolha um template** e personalize-o com seus textos e imagens.
3. **Publique sua landing page** diretamente na blockchain ICP.
4. **Compartilhe o link** da sua landing page com o seu público.

---

Com o `geradorlp`, a criação de landing pages se torna mais acessível, segura e alinhada com o futuro da web descentralizada. 🚀

---

## ⚙️ **Instalação do Projeto**

Abaixo irei apresentar duas formas de instalar o projeto para rodar locamente. Uma mais pratica e outra mais detalhada. 

Para começar será necessário clonar o projeto (github). Lembre-se que se estiver utilizando o Sistema Operacional Windows é necessário utilizar o WSL.

Para quem preferir uma instalação mais rapida, após concluir o clone do projeto basta entrar no diretorio do projeto:

```bash
cd geradorlp
```

e em seguida instalar as dependencias utilizando o comando abaixo: 

```bash
npm install
```
Depois disso pode ir diretamente para o passo `Rodando o projeto localmente`

Para quem deseja realizar a instalação manual e conhecer as principais dependências do projeto, siga as instruções abaixo. Execute os comandos indicados para instalar todas as dependências necessárias (lembre-se que se estiver utilizando o Sistema Operacional Windows é necessário utilizar o WSL):

```bash
cd geradorlp
npm install --save @dfinity/auth-client
npm install react-router-dom
npm install react-helmet
npm install @dfinity/identity
npm install @dfinity/agent
npm install @dfinity/assets
```

Agora realize a instalação do Tailwind (ele será utilizado para estilização do Dapp). Dentro do diretório frontend execute os comandos abaixo:
```bash
cd src/geradorlp_frontend
npm install -D tailwindcss@3.4.14 postcss autoprefixer
npx tailwindcss init -p
```

Volte para o diretorio raiz do projeto e abra o código fonte no VS Code:

```bash
cd ../..
code .
```

Com o VS Code aberto, localize o arquivo `tailwind.config.js`. Ele se encontra no diretorio src/geradorlp_frontend.
Adicione a linha  content: `[ "./src/**/*.{js,jsx,ts,tsx}", ],`  

O código do arquivo deverá ficar igual ao ilustrado abaixo:

```bash
/** @type {import('tailwindcss').Config} */
export default {
  content: [ "./src/**/*.{js,jsx,ts,tsx}", ], 
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Depois disso pode ir para o passo `Rodando o projeto localmente`

## Rodando o projeto localmente

Para rodar o projeto localmente execute os seguintes comandos:

```bash
dfx start --background

dfx deploy
```

Para que o Canister do frontend consiga gravar os assets (imagens) será necessário liberar as permissões apresentadas abaixo.
Estes comandos não precisam ser executados a cada deploy, apenas no primeiro deploy ou em caso de reinstalação do Canister. 

```bash
dfx canister call geradorlp_frontend grant_permission '(record {permission = variant {Prepare}; to_principal = principal "535yc-uxytb-gfk7h-tny7p-vjkoe-i4krp-3qmcl-uqfgr-cpgej-yqtjq-rqe"})'
```

```bash
dfx canister call geradorlp_frontend grant_permission '(record {permission = variant {Commit}; to_principal = principal "535yc-uxytb-gfk7h-tny7p-vjkoe-i4krp-3qmcl-uqfgr-cpgej-yqtjq-rqe"})'
```

Depois disso copie a URL gerada ao termino do deploy e cole no seu navagador.
