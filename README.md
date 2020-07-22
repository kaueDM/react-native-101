# React Native 101

Projeto com o objetivo de facilitar a vida de quem está começando no React Native ou quer se aperfeiçoar.

PRs são bem vindas. Contribua e ajude seus colegas desenvolvedores.

> O algarismo "101" pode ser usado como adjetivo em inglês com o sentido de "básico", "elementar", "fundamental" etc. Este emprego tem sua origem nas universidades americanas que denominam as matérias dadas no início do curso dessa forma: "PHYSICS 101", "CALCULUS 101" etc.
>
> [O que significa “101” em inglês? - Tecla SAP](https://www.teclasap.com.br/vocabulario-elementar/)

## 1. Iniciando um projeto

### 1.1 React Native CLI ou Expo?

O Expo é sem dúvida uma excelente ferramenta. Permite criar apps com setup quase zero, vem com diversas
bibliotecas integradas, além de poder fazer projetos inteiros usando somente o browser. Incrível, não? Só que como dizem por aí:

> Não existe almoço grátis.

Todas essas facilidades do Expo trazem alguns _drawbacks_, das quais podemos listar:

- Tamanho do app (mais de _10MB_ no Android, mas algo que [estão trabalhando para diminuir](https://expo.canny.io/feature-requests/p/reducing-app-size))
- Incapacidade de adicionar módulos com código nativo (`react-native link` ou `autolinking`)
- Aquisições dentro do aplicativo (como ativar um plano premium)
- Dependência do Expo em políticas das App Store/Play Store - como a recente mudança na Play Store para suporte obrigatório a processadores 64 bits.

**Então eu não devo usar o Expo para nada?**

Errado. O Expo deve te atender perfeitamente em alguns casos, mas você deve ter em mente suas limitações e avaliar qual é a melhor opção para você. O ponto principal é que se você precisa usar código nativo ou quer ter um maior controle, evite usar o Expo.

### 1.2 Criando o projeto

##### Expo

Como o propósito do Expo é facilitar o setup, basta ter o NodeJS e o `expo-cli` instalado em sua máquina

`npm i -g expo-cli`

Feito isso, inicialize seu projeto:

```
expo init meu-novo-projeto
cd meu-novo-projeto
expo start
```

##### React Native CLI

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

Digamos que seu projeto chama-se _App de Táxis_, esses seriam os passos para renomear seu projeto:

#### Expo

Você deve adicionar as configurações do ios e do android no arquivo `app.json`, onde fica todas as configurações do seu aplicativo:

```
"ios": {
  "bundleIdentifier": "com.nomedasuaempresa.appdetaxis"
},
"android": {
  "package": "com.nomedasuaempresa.appdetaxis"
}
```

##### React Native CLI

Para facilitar o processo, recomendo a utilização do `react-native-rename`

```
npm -i -g react-native-rename
yarn global add react-native-rename
```

Para renomear usando o `react-native-rename`, faça o seguinte:

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

[React Native Web, Expo, React.memo, O Universo do React Native | #PR 04](https://www.youtube.com/watch?v=VsU6p7DHVtA)

## 2. Módulos nativos que você (provavelmente) vai usar

Essa lista mostra os módulos nativos mais comuns que você vai utilizar em quase todos os seus projetos. Recomendo instalar eles antes de escrever uma única linha de JavaScript, para que o ambiente do seu app já tenha as peças necessárias para você construir suas funcionalidades.

É interessante também criar um `branch` para cada módulo nativo, já que existem chances de você ter problemas na instalação e ninguém quer fazer tudo do zero né? Mantendo um `branch` para cada módulo, fica fácil reverter para um ponto onde as coisas ainda funcionavam.

❗️ **Após cada instalação, teste seu app. Se ele abrir sem nenhum erro, vá para o próximo módulo.**

- `react-native-firebase`: Mesmo que você não vá usar o Firestore/Realtime Database como seu banco de dados, o Firebase oferece o **Crashlytics**, ferramenta mais que obrigatória em qualquer aplicativo para monitorar falhas em tempo real. Basta seguir [a documentação oficial](https://rnfirebase.io) para adicionar ele ao seu projeto.

- `react-native-splash-screen`: Por padrão, o React Native apresenta uma tela cinza (Android) ou uma tela branca com o nome do app (iOS) enquanto o código nativo e o bundle JS são inicializados. Para fechar esta lacuna, o [react-native-splash-screen](https://github.com/crazycodeboy/react-native-splash-screen#installation) permite a personalização da tela de carregamento de forma simplificada.

  [Este artigo](https://medium.com/handlebar-labs/how-to-add-a-splash-screen-to-a-react-native-app-ios-and-android-30a3cec835ae) mostra o passo a passo de como adicionar telas de carregamento personalizadas em ambas as plataformas.

- `react-native-vector-icons`: O que é um app sem ícones, não é mesmo? [Esse módulo](https://github.com/oblador/react-native-vector-icons) fornece diversas bibliotecas de ícones, como FontAwesome, Feather, MaterialIcons, etc. Você pode conferir todos os ícones disponíveis [aqui](https://oblador.github.io/react-native-vector-icons/).

❗️ **Se você for usar ícones próprios, não é necessário instalar este módulo nativamente.**

- `react-native-reanimated`: Animar é preciso. E nada melhor que construir animações que rodam diretamente na thread UI do dispositivo. Para entender a necessidade e o funcionamento, escrevi [um artigo sobre](https://medium.com/@kauedm/react-native-reanimated-um-guia-pr%C3%A1tico-cbd16465b0b8), confere aí :D

❗️ **Atualmente, o artigo aborda a primeira versão do react-native-reanimated. O material sobre a v2 sairá em breve.**

- `react-native-gesture-handler`: O [RNGH](https://docs.swmansion.com/react-native-gesture-handler) entrega controle total aos gestos do usuário para os mais diversos fins.

## 3. Módulos JavaScript que você (provavelmente) vai usar

- `axios`: Com uma [extensa documentação](https://github.com/axios/axios), é o seu client de requisições HTTP. Uma alternativa é a [Fetch API](https://facebook.github.io/react-native/docs/network#using-fetch).

- `react-navigation`: Responsável por fazer seu app 'trocar de telas', o [`react-navigation`](https://reactnavigation.org/) tornou-se o módulo predileto de navegação da comunidade. É possível acompanhar o progresso da ferramenta pelo [canny.io](https://react-navigation.canny.io).

- `redux`: O Redux é um container de estado para seu app. Em outras palavras, é um """`state` global""" (repare na quantidade de aspas nesse termo). Uma boa referência para entender o que é Redux é [este vídeo (em inglês)](https://www.youtube.com/watch?v=KcC8KZ_Ga2M) (recomendação do [starchild637](https://github.com/starchild637)). Só antes de sair instalando, verifique se você entende o que é Redux e se realmente precisa adicionar essa camada de complexidade no seu projeto.

- `styled-components`: O [`styled-components`](https://www.styled-components.com/) simplifica a personalização visual dos seus componentes, usando uma sintaxe próxima ao do CSS.

- `restyle`: Uma alternativa ao `styled-components`. Focado no React Native, o [`restyle`](https://github.com/Shopify/restyle) é um gerenciador de temas poderoso construído pelo Shopify.

## 4. Estrutura de pastas

> Tópico sendo reescrito. Volte em breve para ler ;D
