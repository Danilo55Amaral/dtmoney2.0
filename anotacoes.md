# Anotações Referentes ao projeto Dt Money2.0

## Styled-components
- Nesse projeto utilizaremos o Styled-components
- Rode o comando npm i styled-components para instalar 
- Rode o comando npm i @types/styled-components -D oara instalar a tipagem do styled-components
- Com isso podemos utilizar o styled-components

## ThemeProvider
- É o provider de contexto do styled-components e utilizamos ele dentro do App.tsx 
- ele irá prover o tema que vai ser usado ao longo de toda a aplicação.
- quando estamos utilizando o styled-component com o typeScript e utilizamos alguns recursos como theme, precisamos criar um arquivo de tipagem.
- Para isso criamos uma pasta chamada @types com um arquivo chamado styled.d.ts dentro desse arquivo é feita a importação do styled-components, vamos estender a 
tipagem que o styled já tem e não subcrever ela por isso a necessidade de importar ele.

- Quando eu crio o ThemeType e passo o defaultTheme ele já importa o defaultTheme.

## Componente Header

- Foi criada a pasta assets e importado o logo em svg do figma.
- Foi criada a pasta pages e um componente chamado Transactions

## Componente Summary

- Aqui criamos o componente Summary que mostra o resumo em tela.
- Aqui foi instalada a lib de icones do phosphor React rodando o comando abaixo
- npm i phosphor-react 
- foi criada a interface SummaryCardProps para criar uma propriedade chamada variant e criar uma condicional para cores.

## Tabela de transações 

- A tabela de transações foi feita dentro da página trnasactions porém se for necessário ter mais lógica ou ser reaproveitada pode ser separada em um componente separado.

## Componente SearchForm 

- Aqui foi contruido o formulário de busca, dentro da pasta pages foi criada uma nova pasta de components que foi criado o componente SeachForm.

## Criando um modal acessível (Libs interessantes)

- Alguns elementos que tem algum tipo de comportamento visual como modal,dropDown entre  outros.
elementos que dada a ação do usuario aparece algum elemento em tela, é sempre bom cuidar com acessibilidade.

- Existem algumas libs que fazem isso com acessibilidade como o Ariakit que funciona super bem. 
- Tem a lib Headless UI 

- Tem a lib Radix que é uma série de componentes primitivos para essas finalizades e traz uma api bem flexivel para esses comportamentos, todos os elementos seguem todas as regras de acessibilidade.

- Nesse projeto utilizamos o Radix e o componente Dialog.

- Para utilizar basta seguir as recomendações na documentalçao. 
- rodar o comando            npm install @radix-ui/react-dialog

- Colocamos o modal no header e para utilizar basta seguir a documentação.
- Depois de importar utilizar por volta de todo o contexto do modal

- Vou utilizar a estrutura Trigger do Dialog que já é um button, eu posso fazer isso 
dentro do styles fazendo a importação do Dialog e substituindo o button dentro de NewTransactionButton por  (Dialog.Trigger) mas para evitar poluir o css não utilizamos essa maneira.

- Eu simplismente coloquei o Trigger por volta do Botão e passei uma propriedade chamada asChild essa propriedade impede que o Trigger crie um novo botão e sim aproveite o elemento do botção que já existe dentro da tag como sendo o trigger do modal.

- Utilizamos também  um Portal que é uma funcionalidade do React que fornece uma forma 
elegante de renderizar um elemento filho dentro de um outro local da DOM
com isso pode colocar um elemento dentro do Portal e ele vai parar em outro local 
da aplicação, com isso podemos colocar por ex o nosso modal fora de todas as divs de nossa aplicação.

- O Overlay é basicamente um fundo preto com a opacidade um pouco  mais baixa.

- O Content é o conteudo em si do modal. O Proprio Dialog já possue algumas predefinições de conteudo.

- O Close é o botao de fechar.

- Note que ao testar ele não traz nenhuma estilização apenas o componente primitivo e todo o css é feito a mão.

- Outra coisa legal é que se você inspecionar vai perceber que a div do dialog é criada fora do contexto da aplicação, isso ajuda bastante por que toda a parte de acessibilidade já vem junto como por ex fechar o modal apertando a tecla Esc do teclado.

link do Radix     https://www.radix-ui.com

## Modal de nova transação

- Foi criado um novo componente chamado NewTransactionModal esse componente apena tem a parte do conteudo do modal.

-  Foi necessário estilizar componentes do Dialog e para isso foi necessário importar dentro do 
arquivo styles.ts.

## Botões de entrada e Sáida

- Dentro do componente NewTransactionModal foi criado um container chamado TransactionType e um outro chamado TransactionTypeButton.