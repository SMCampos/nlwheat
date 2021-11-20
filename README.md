### Desenvolvimento da API com autenticação via Github com acesso via Web e Mobile

**TECNOLOGIAS UTILIZADAS NO PROJETO**

[Node.js] (https://nodejs.org/en/)  \
[Typescript] (https://www.typescriptlang.org/)  \
[Express] (https://expressjs.com/pt-br/)  \
[Prisma] (https://www.prisma.io/)  \
[Github Oauth App] (https://github.com/settings/developers)  \
[Socket.io] (https://socket.io/)  \
[Vite.js] (https://vitejs.dev/)  \
[React.js] (https://pt-br.reactjs.org/)  \
[React Native] (https://reactnative.dev/)  \
[Expo] (https://expo.dev/) 


Para criar o projeto no terminal integrado do Vs Code digite:

`yarn init -y`

Esse comando vai criar o arquivo **package.json**

Em seguida no terminal instale as dependências: \
[Express](https://www.npmjs.com/package/express) \
`yarn add express`

[Typescript](https://www.npmjs.com/package/typescript) \
`yarn add @typescript -D`

[TS-NODE](https://www.npmjs.com/package/ts-node) \
`yarn add ts-node-dev` 

[@TYPES/EXPRESS](https://www.npmjs.com/package/@types/express)  \
`yarn add @types/express -D`

Após instalar essas dependências, digite no terminal o comando:  \
`yarn tsc --init`

Esse comando irá criar o arquivo tsconfig.json. 

No arquivo package-json inserir o **scripts**: 

```
"{
  "name": "nlwheat",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "scripts": {
    "dev": "ts-node-dev --exit-child src/server.ts"
  },

```

Na raiz do projeto criar a pasta **src** e dentro dela criar o arquivo **App.ts**

Para armazenar os dados foi utilizado o [PRISMA](https://www.prisma.io/) \
"O Prisma ajuda os desenvolvedores de aplicativos a construir mais rapidamente e cometer menos erros com um kit de ferramentas de banco de dados de código aberto para PostgreSQL, MySQL, SQL Server e SQLite."  \

Para instalar as dependências do Prisma, no terminal digite: \
`yarn add prisma -D`  e em seguida digite: `yarn prisma init`

Será criada no projeto a pasta **prisma** e o arquivo **.env**

### Configurando o Githhub OAuth Apps

Acesse sua conta no github, na parte superior da tela à sua direita clique na imagem do seu avatar e vá na opção Settings, \
escolha a opção Developer Settings no menu lateral e selecione OAuth Apps.

Também é possível acessar diretamente através do link [OAuthApps](https://github.com/settings/developers)

- Clique em New OAuth App, preencha as informações:  \
- Application Name: Api Node
- Homepage URL: http://localhost:4000
- Application Description: Api Node
- Authorization Callback URL: http://localhost:4000/signin/callback
  
clique em Register Application.  \

Será criado automaticamente um novo Client ID \
clique em Generate a new Client Secrets

Volte ao projeto no arquivo **.env** e insira as informações do Client ID e Client Secret, conforme o exemplo abaixo: 

```
GITHUB_CLIENT_SECRET=[insira aqui o seu Client Secret]
GITHUB_CLIENT_ID=[insira aqui o seu Client ID]

```
Por questão de segurança, **INSIRA O NOME DO ARQUIVO .env** no seu arquivo **.gitignore**, pois assim ele não será enviado quando salvar o projeto no Github.

Adicione as dependências abaixo:  \
[dotenv](https://www.npmjs.com/package/dotenv) `yarn add dotenv`  \
[axios](https://www.npmjs.com/package/axios) `yarn add axios`  \
[jsonwentoken](https://www.npmjs.com/package/jsonwebtoken) `yarn add jsonwebtoken`
[@types/jsonwebtoken](https://www.npmjs.com/package/@types/jsonwebtoken) `yarn add @types/jsonwebtoken -D`  \
[prisma/client](https://www.npmjs.com/package/@prisma/client) `yarn add @prisma/client -D`

Na pasta **PRISMA** abra o arquivo **schema.prisma**, encerre a aplicação com o comando `CTRL + C` no terminal.  \
Crie a **model User** e execute o comando no terminal: `yarn prisma migrate dev`  \
em nome da new migration coloque: **create-user** \
Crie a **model Message** e execute o comando no terminal: `yarn prisma migrate dev`  \
em nome da new migration coloque: **create-messages** \

Para rodar o **PRISMA** em modo visual digite no terminal o comando: `yarn prisma studio` .

### Criando a conexão via Websocket

Adicione as dependências:  \
[socket.io](https://www.npmjs.com/package/socket.io) `yarn add socket.io`  \
[@types/socket.io](https://www.npmjs.com/package/@types/socket.io) `yarn add @types/socket.io -D` \
[cors](https://www.npmjs.com/package/cors) `yarn add cors`
[@types/cors](https://www.npmjs.com/package/@types/cors) `yard add @types/cors -D`

### Projeto ReactJs - FRONT-END

Para criação do projeto será utilizado a aplicação [VITE](https://vitejs.dev/)

Para criar o projeto: na pasta do projeto crie uma sub-pasta e nomeie como: **web**

No terminal do Visual Studio Code navegue para a pasta web e digite o comando: 

`yarn create vite web --template react-ts`

Digite o comando: `yarn`

Adicione as dependências:  \
`yarn add sass`  \
`yarn add react-icons` \
`yarn add axios` \
`yarn add socket.io-client` \


### Projeto mobile com React Native com Typescript

Para desenvolvimento do projeto utilizamos o Visual Studio Code.

Para emular o projeto foi utilizado um dispositivo físico (celular) com sistema operacional Android.

Para emular o projeto utilizamos a aplicação [EXPO](https://expo.dev/)

Crie uma nova pasta e nomeie com o nome que desejar, no projeto utilizei **nlwheatapp**

Antes de criar o projeto insira as dependências do **EXPO**

`yarn global add expo-cli`

No terminal do VS Code digite o comando: \
`expo init nlwheatapp`

Escolha a opção **blank (Typescript)**

Para rodar o projeto digite no terminal: `expo start`

o projeto vai abrir em uma ba do navegador: http://localhost:19002/

Você poderá optar em utilizar um emulador ou um dispositivo físico (necessita a instalação do App Expo Go).

Adicione as dependências:
`expo install expo-font @expo-google-fonts/roboto`  \
`expo install expo-app-loading`  \
`expo install react-native-svg`  \
`expo install expo-linear-gradient` \
`expo install react-native-reanimated`  \

`yarn add -D react-native-svg-transformer`
`yarn add react-native-iphone-x-helper`
`yarn add moti`

Após instalar o **moti e reanimated** é necessário atualizar o arquivo **babel.config.js** acrescentando `plugins: ['react-native-reanimated/plugin'],` \
em seguida pare a aplicação com o comando CTRL + C e reinicie a aplicação com o comando expo start.

Ainda deverão ser adicionadas as dependências:  \
`expo install expo-auth-session expo-random`
`expo install @react-native-async-storage/async-storage`
`yarn add socket.io-client`

### Criar autorização no Github OAuthApp

Acesse sua conta no github, na parte superior da tela à sua direita clique na imagem do seu avatar e vá na opção Settings, \
escolha a opção Developer Settings no menu lateral e selecione OAuth Apps.

Também é possível acessar diretamente através do link [OAuthApps](https://github.com/settings/developers)

- Clique em New OAuth App, preencha as informações:  \
- Application Name: App Heat
- Homepage URL: https://auth.expo.io/@smcampos/nlwheatapp
- Application Description: App Heat
- Authorization Callback URL: https://auth.expo.io/@smcampos/nlwheatapp

Clique em Register Application.  \

Será criado automaticamente um novo Client ID \
clique em Generate a new Client Secrets  \







