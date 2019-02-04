# React Native 101

Projeto com o objetivo de facilitar a vida de quem está começando no React Native ou quer se aperfeiçoar.

PRs são bem vindas. Contribua e ajude seus colegas desenvolvedores.

>O algarismo "101" pode ser usado como adjetivo em inglês com o sentido de "básico", "elementar", "fundamental" etc. Este emprego tem sua origem nas universidades americanas que denominam as matérias dadas no início do curso dessa forma: "PHYSICS 101", "CALCULUS 101" etc.
>
>[O que significa “101” em inglês? - Tecla SAP](https://www.teclasap.com.br/vocabulario-elementar/)

## Sumário
`TODO`

## 1. Iniciando um projeto
### 1.1 React Native CLI ou Expo?

O Expo é sem dúvida uma excelente ferramenta. Permite criar apps com setup quase zero, vem com diversas
bibliotecas integradas, além de poder fazer projetos inteiros usando somente o browser. Incrível, não? Só que como dizem por aí:

> Não existe almoço grátis.

Todas essas facilidades do Expo trazem alguns _drawbacks_, sendo os que considero principais:

* Tamanho do app (mais de *20MB* no Android)
* Incapacidade de adicionar módulos com código nativo (a.k.a. `react-native link`)

_Ah mas o app que eu publiquei na Play Store usa Expo blá blá blá_

Parabéns! 80% do app que seu usuário baixou não tem serventia, é apenas uma pilha de entulho no dispositivo dele.

**Então eu não devo usar o Expo para nada?**

Errado. O Expo é ótimo para estudos, para testar aquela sua ideia ou pra compartilhar componentes com outros desenvolvedores. Apenas tenha em mente as suas limitações e evite usar em produção.

### 1.2 Criando o projeto

Antes de começar, você precisa ter seu ambiente configurado. O melhor lugar pra aprender o que deve ser feito está na documentação oficial, na aba [Building projects with Native Code](https://facebook.github.io/react-native/docs/getting-started)

O próximo passo é criar seu projeto:
`react-native init myProject`

E então adicionar o repositório remoto a ele:
`git remote add origin https://link-do-seu-repositorio.git`

Se você não faz ideia do que seja Git, pare tudo que você está fazendo e [aprenda sobre ele](http://rogerdudler.github.io/git-guide/index.pt_BR.html)

Se você sabe o que é Git mas não utiliza, reveja seus conceitos. Mesmo que seja apenas um projeto de estudos, nenhuma empresa hoje em dia trabalha sem um Sistema de Controle de Versões (SCV), então, torne o Git um hábito.

👉 Não sabe que estrutura utilizar dentro do Git? Dê uma olhada [nesse artigo.](https://nvie.com/posts/a-successful-git-branching-model/)

### 1.3 Alterando o nome do projeto

Caso você vá publicar esse projeto nas lojas de aplicativo, crie o mesmo no Google Play Store e/ou Apple App Store.

❗️ **Escolha um nome de pacote consistente.** 

Costuma-se utilizar a notação `com.nomedasuaempresa.nomedoapp`. Esta etapa é muito importante, já que não é possível alterar este identificador após publicar o app.

❗️ **Renomeie seu projeto para refletir o nome do pacote.**

Para facilitar o processo, recomendo a utilização do `react-native-rename`

```
npm -i -g react-native-rename
yarn global add react-native-rename
```

Digamos que seu projeto chama-se _App de Táxis_. Para renomear usando o `react-native-rename`, faça o seguinte:

```
react-native-rename appdetaxis -b com.nomedasuaempresa.appdetaxis
```

### 1.4 Styleguide

Por mais que existam diversos styleguides, recomendo o uso do [StandardJS](https://standardjs.com/). É simples, não tem configuração e formata seu código _automagicamente_ ~~, Além de usar aspas simples, que são bem mais legais que aspas duplas~~. Caso você queira integrar com o seu editor de código favorito, [aqui tem uma lista de opções](https://standardjs.com/#are-there-text-editor-plugins).

Lembre-se de adicionar no seu `package.json` o seguinte trecho (e instalar o `babel-eslint` como `devDependency`):

```
"standard": {
    "parser": "babel-eslint"
  }
```

### 1.5 Referências
[React-native first impressions: Expo vs. Native](https://medium.com/@paulsc/react-native-first-impressions-expo-vs-native-9565cce44c92)

[Should i not be using expo?](https://www.reddit.com/r/reactnative/comments/94xsbd/should_i_not_be_using_expo/)

[Why not Expo?](https://docs.expo.io/versions/latest/introduction/why-not-expo/)

[Is it possible to change the package name of an Android app on Google Play?](https://stackoverflow.com/questions/17582289/is-it-possible-to-change-the-package-name-of-an-android-app-on-google-play)

## 2. Módulos nativos que você (provavelmente) vai usar

Essa lista mostra os módulos nativos mais comuns que você vai utilizar em quase todos os seus projetos. Recomendo instalar eles antes de escrever uma única linha de JavaScript, para que o ambiente do seu app já tenha as peças necessárias para você construir suas funcionalidades.

É interessante também criar um `branch` para cada módulo nativo, já que existem chances de você ter problemas na instalação e ninguém quer fazer tudo do zero né? Mantendo um `branch` para cada módulo, fica fácil reverter para um ponto onde as coisas ainda funcionavam.

❗️ **Após cada instalação, teste seu app. Se ele abrir sem nenhum erro, vá para o próximo módulo.** 

* `react-native-firebase`: Mesmo que você não vá usar o Firestore/Realtime Database como seu banco de dados, o Firebase oferece o **Crashlytics**, ferramenta mais que obrigatória em qualquer aplicativo para monitorar falhas em tempo real. Basta seguir [a documentação oficial](https://rnfirebase.io) para adicionar ele ao seu projeto.

* `react-native-splash-screen`: Por padrão, o React Native apresenta uma tela cinza (Android) ou uma tela branca com o nome do app (iOS) enquanto o código nativo e o bundle JS são inicializados. Para fechar esta lacuna, o [react-native-splash-screen](https://github.com/crazycodeboy/react-native-splash-screen#installation) permite a personalização da tela de carregamento de forma simplificada.

    [Este artigo](https://medium.com/handlebar-labs/how-to-add-a-splash-screen-to-a-react-native-app-ios-and-android-30a3cec835ae) mostra o passo a passo de como adicionar telas de carregamento personalizadas em ambas as plataformas. 

* `react-native-vector-icons`: O que é um app sem ícones, não é mesmo? [Esse módulo](https://github.com/oblador/react-native-vector-icons) fornece diversas bibliotecas de ícones, como FontAwesome, Feather, MaterialIcons, etc. Você pode conferir todos os ícones disponíveis [aqui](https://oblador.github.io/react-native-vector-icons/).

❗️ **Se você for usar ícones próprios, não é necessário instalar este módulo nativamente.** 

## 3. Módulos JavaScript que você (provavelmente) vai usar

* `axios`: Com uma [extensa documentação](https://github.com/axios/axios), é o seu client de requisições HTTP. Uma alternativa é a [Fetch API](https://facebook.github.io/react-native/docs/network#using-fetch).

* `react-navigation`: Responsável por fazer seu app 'trocar de telas', o [`react-navigation`](https://reactnavigation.org/) tornou-se o módulo predileto de navegação da comunidade. É possível acompanhar o progresso da ferramenta pelo [canny.io](https://react-navigation.canny.io).

* `redux`: O Redux é um container de estado para seu app. Em outras palavras, é um """`state` global""" (repare na quantidade de aspas nesse termo). Uma boa referência para entender o que é Redux é [este vídeo (em inglês)](https://www.youtube.com/watch?v=KcC8KZ_Ga2M) (recomendação do [starchild637](https://github.com/starchild637)). Só antes de sair instalando, verifique se você entende o que é Redux e se realmente precisa adicionar essa camada de complexidade no seu projeto.

* `styled-components`: Recomendação pessoal. o [`styled-components`](https://www.styled-components.com/) simplifica a personalização visual dos seus componentes, usando uma sintaxe próxima ao do CSS.

## 4. Estrutura de pastas

❗️ **Isso aqui não é regra. Modifique como quiser, ou ignore e crie a sua estrutura.** 

Organizar arquivos é uma tarefa complicada. Baseado nos projetos realizados nos últimos dois anos, a estrutura abaixo é proposta:

### 4.1 Visão geral
```
.
├── 📄 App.js
├── 📄 app.json
├── 📄 index.js
├── 📄 package.json
├── 📁 android
├── 📁 ios
├── 📁 src
│   ├── 📁 assets
│   │   └── 📁 images
│   │       └── 📄 logo.png
│   │
│   ├── 📁 components
│   │   └── 📁 Button
│   │       ├── 📄 index.js
│   │       └── 📄 Button.story.js
│   │
│   ├── 📁 config
│   │   ├── 📄 colors.js
│   │   └── 📄 routes.js
│   │ 
│   └── 📁 redux
│       ├── 📄 store.js
│       └── 📁 reducers
│           ├── 📄 index.js
│           └── 📄 customer.js
│
├── 📁 screens
│   └── 📁 Home
│       ├── 📄 index.js
│       └── 📄 _localComponents.js
│
├── 📁 services
│   └── 📁 API
│       ├── 📄 API.js
│       └── 📄 SomeAPIEndpoint.js
│
└── 📁 utils
    └── 📁 String
        └── 📄 camelize.js
```

### 4.2 Descrição

* **./assets:** A pasta onde todos os seus arquivos externos vão ficar.

* **./components:** Cada componente deve ter a sua própria pasta, sendo sempre que possível `stateless`. Caso você use Storybook, sua `story` deve ficar dentro da pasta do respectivo componente.

* **./config:** Arquivos de configuração do seu app. Rotas, cores, etc.

* **./redux:** Caso use Redux, aqui ficam o `store` e os `reducers` da sua aplicação. A estrutura desses reducers serão abordadas nos próximos capítulos deste guia 🦆.

* **./screens:** As telas do seu app. Cada tela tem sua própria pasta. Dentro de cada pasta pode existir também algo que chamo de `_localComponents`. O conteúdo desses arquivos são geralmente **ajustes de layout** específicos para a tela em questão (separadores, margens, etc). São regras que não vão se repetir em outras telas, e para não poluir o arquivo principal, eu as movo para este arquivo genérico.

* **./services:** Serviços são (preferencialmente) classes que fazem algo específico no seu app, ou seja, não podem ser copiadas e coladas em outro projeto. Ficam aqui chamadas para APIs, por exemplo.

* **./utils:** Utilitários são funções que fazem algo genérico, ou seja, podem ser copiadas e coladas em outro projeto. Semelhantes aos módulos do `npm`, os arquivos que estão em `./utils` não são modificados de acordo com a necessidade.

### 4.3 Configuração

Para fazer essa estrutura (ou qualquer outra) funcionar sem precisar fazer imports longos, você vai usar o pacote [`babel-plugin-module-resolver`](https://github.com/tleunen/babel-plugin-module-resolver). Após a instalação, altere o seu arquivo `.babelrc` para a seguinte estrutura:

❗️ **Caso não exista um arquivo `.babelrc`, crie um.** 

❗️ **Caso exista um arquivo `babelrc.config.js`, modifique para a mesma estrutura usando notação JavaScript ou apague ele e crie um `.babelrc`, dá na mesma.** 

❗️ **Caso seu projeto quebre, encerre o processo do bundler e inicie um novo, limpando o cache. use o comando `react-native start --reset-cache` dentro da pasta do app.** 

```
{
  "presets": [
    "module:metro-react-native-babel-preset"
  ],
  "plugins": [
    [
      "module-resolver",
      {
        "cwd": "babelrc",
        "root": ["./src"],
        "extensions": [".js"],
        "alias": {
          "screens": "./src/screens",
          "components": "./src/components",
          ...outros alias aqui (assets, services, etc)
        }
      }
    ]
  ]
}
```

