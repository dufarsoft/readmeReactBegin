# React Routers


### Iniciando
- Instalar globalmente a ferramenta que o facebook disponibiliza já configurada para trabalharmos com aplicações web    
        npm install -g create-react-app

- Agora vamos iniciar a criação de nosso aplicação em si , via terminal :

        create-react-app nomeDaAplicação

- Depois disso já podemos iniciar dentro do diretório nomeDaAplicação nossa própria aplicação em um servidor, o endereço de onde vai ser startado irá aparecer, via terminal : 

        cd nomeDaAplicação
        npm start

### Enxugando nosso template de desenvolvimento ( fazendo a limpa)

- Após essa instalação demorada será gerado vários arquivos e pastas dentro do diretório da nossa aplicação,


- pasta public: onde contém o HTML, cujo é apenas uma pagina HTML que trará nosso componente.

- pasta src : precisaremos basicamente do arquivo index.js e App.js.
- App.js : é o nosso componente que que escreve o que será renderizado.
- index.js : é o arquivo que importa nosso App e o fais ser renderizado.

### Criando Views

- Nossas views sãos os conteúdos que vao sendo alterados quando navegamos por rotas na nossa SPA.

- Nossa AppShell é o componente Pai , o coração da nossa aplicação.. e agora criaremos componentes filhos que serão nossas views nas quais navegaremos através de rotas.

- Um componente filho tem basicamente a mesma estrutura do componente Pai, a mais enxuta fica dessa forma : 

            import React, { Component } from 'react';

            class ComponenteFilho extends Component {
            render() {
                return (
                <div>
                    <h1> View 1 </h1>
                </div>
                );
            }
            }
            export default ComponenteFilho;

### Injetando o ReactRouter na aplicação.

- Entraremos dentro do diretório de nosso projeto via terminal:

            cd app

- Instalar o react router para podermos fazer nossa SPA funcionar.

            npm install --save-dev react-router-dom

- No index.js vamos importar um dos componentes de rotas do react-router:

            import { BrowserRouter } from 'react-router-dom';


- Agora vamos importar nossos componentes filhos criados anteriormente dentro de nosso componente pai AppShell.

            import View1 from './View1';
            import View2 from './View2';
            import View3 from './View3';


- Ainda no index.js..aonde renderizamos o componente pai, colocaremos nosso componente pai dentro de uma instancia do componente BrowserRouter que importamos do react-router-dom.  

            ReactDOM.render(
                    <BrowserRouter>
                        <AppShell  />
                    </BrowserRouter>
                    , document.getElementById('root'));



- Também em nosso componente pai, importamos componentes para fazermos nossa rota funcionar de uma forma dinâmica

            import { Switch , Route}

- Esses componentes Switch e Route é que vão fazer a magica acontecer, vou definir melhor cada um deles:

- <Switch> , é o componente que cuida da troca de rotas fazendo com que não ocorra conflito ,nesse caso  colocaremos o componente Route dentro do Switch

- <Route> , esse componente é o que especifíca que rota aponta pra que componente ou seja dentro desse componente vamos usar dois atributos, um nomeando a rota e o outro referenciando o componente cujo aquela mesma rota pertence.

            <Switch>
                <Route path="one" component={nomeDoComponente}/>
            </Switch>

## Criando Links para navegar entre views

- Dentro do mesmo import do Switch, vamos importar o component Link

            import { Switch, Route, Link};