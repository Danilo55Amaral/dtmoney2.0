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

## Criando radio button acessivel

- Esse botções de entrada e saida funcionam como um radio button do html, funciona 
como uma entrada de dado que só pode ser selecionada uma opção.

- O Radix tem o elemento de Radio chamado Radio Group e vamos utiliza-lo para controlar a informação de qual botão foi selecionado.

- deve rodar o comando   npm install @radix-ui/react-radio-group

link: https://www.radix-ui.com/docs/primitives/components/radio-group

- Importei o RadioGroup e no styles no transactioType que é div que está por volta dos botoes, transformei ela no RadioGroup.root, também  vou fazer com o TransactionTypeButton.

- Vai gerar um erro no arquivo index por que é obrigatório passar uma propriedade, 
chamada value que indica qual o valor do intem especifico.

## Configurando JSON Server Para simular api

- Nesse projeto é necessário Consumnir uma api isso por que é importante aprender a 
utilizar a api de fetch do navegador para poder fazer a comunicação de um front end 
com um back end independentemente da linguagem em que o back end foi criado, vamos 
seguir o padrão de uma api rest full.

- Como ainda não temos um back end para esse projeto é necessário alguma ferramenta 
que faça a simulação de um back end para que possamos testar, o json-server é uma das melhores opções que temos atualmente. 

- https://github.com/typicode/json-server

- Esse projeto do json-server a partir de um arquivo json ele cria uma api completa 
permitindo criar rotas, fazer filtros, paginação, ordenação, fazer operações entre varias outas coisas.

- instalamos rodando o seguinte comando  npm i json-server -D

- Crio um arquivo na raiz do projeto chamado server.json dentro desse arquivo foi 
criado um objeto, para cada propriedade que for passada a esse objeto vai ser uma 
rota da aplicação, ou podemos chamar de entidade da aplicação.

- O json-server só será util em desenvolvimento em produção não é possivel utilizar 
esse é um projeto para que seja possivel construir uma interface front end sem 
depender que o back end da aplicação esteja pronto, ele deixa o react por ex com 
tudo pronto para fazer o consumo de uma api que possa vir no futuro quando o projeto 
for para produção.

- Para rodar basta rodar o seguinte comando  npx json-server nome-do-arquivo

- Para rodar o json-server modificando a porta basta rodar o comando abaixo passando a porta
npx json-server nome-do-arquivo -p 3333

- Para acessar basta colocar o endereço da porta no navegador http://localhost:3000

- Para acessar a rota criada basta colocar a rota no endereço http://localhost:3000/transactions.

- Por padrão o arquivo do json-server não fica monitorando se ele mudou para mostrar as informações 
atualizadas sem a necessidade de rodar novamente para que isso seja feito de forma automatica basta quando 
rodar o comando utilizar o -w       npx json-server nome-do-arquivo -w

- O json-server é muito poderoso por que não é apenas uma ferramenta de listagem mas é uma api completa
da para criar uma nova informação utilizando o POST por exemplo, da para atualizar informações já 
existentes, da para deletar informações, da para listar alguma informação especifica.

- Posso simplificar o meu comando para rodar o json-server indo lá no arquivo package.json em scripts 
e adicionar "dev:server": "npx json-server nome-do-arquivo -w -d 500", salvando. com isso para rodar 
o json-server basta rodar o comando criado no script            npm dev:server

## Realizando requisição HTTP

- O Json server funciona exatamente como o back end da aplicação isso por que ele simula um back end 

- Para carregar os dados das transações vindas do back end, no componente de Transaciotns, deve ser tomado 
açguns cuidados para que essa lista seja carregada é necessário utilizar a api de fetch do navegador, esse 
metodo é chamado é passado o endereço, esse metodo devolve uma resposta response, isso é feito através de 
uma promise, porém é importante lembrar que tudo que estiver dentor da função do componente irá executar 
sempre que o componente for renderizado, isso não pode acontecer aqui por que queremos que esse fecth seja 
executado uma unica vez, por isso devemos utilizar o useEffect do react que é uma forma de conseguir 
disparár uma função em determinado momento, dentro do useEffect se tivermos o array de dependencias vazio 
a função será executada uma única vez.

- E necessário converter os dados que vem da requisição para algum formato e dentro do proprio fetch 
tem api que faz isso, temos a opção text e Json, o text vai trazer como um json, e o json vai trazer 
já como um objero JavaScript.

- O código pode ser melhorado excrevendo uma função async e chamado ela dentro do useEffect.

- Para os dados serem mostrado em tela foi criado um estado, o estado é a melhor e única forma de se 
armazenar informações dentro do react para serem consumidas pela interface. 

PS- quando se cria um estado no react é sempre importante tipar o estado principalmente se for um 
array ou um objeto. foi criado uma interface para tipar os dados e foi passado para o useState, dentro da tbody eu passei um map que vai percorrer todo o transaction retornando toda a tr da tabela. Com isso dentro do td posso passar as informações.

- PS- Lembrando que quando temos um map dentro do react é importante que o primeiro elemento possua
uma key com alguma informação que seja unica.

## Criando contexto de transações

- Vai ser necessário ter esses dados que vem da api em outros locais da aplicação como no sumary
por exemplo, é necessário ter acesso aos dados da api para conseguir calcular as entradas e saidas 
por exemplo, esses dados poderiam ser enviados através de proppriedades sem problemas. 

- Porém como temos varios componentes de niveis diferentes precisando acessar essas informações de 
transactions, a forma mais fácil de se fazer isso é com contexto.

- Foi criado uma pasta chamada contexts, dentro foi criado um arquivo chamado 
TransactionsContext.tsx

- Depois de criado o contexto movemos o código de chamada api para dentro do contexto

- Dentro do App.tsx colocamos o nosso provider do contexto.

- Em seguida utilizei o useContext chamando meu contexto dentro do componente em que uso os dados.

- Dentro do componente de summary eu também vou acessar esses dados atraves da context api

## Calculando resumo de transações 

- Aqui vamos calcular o resumo de entradas e saidas assim também como o total.
- Poderiamos colocar dentro do contexto se fossemos utilizar esse calculo em outros compomentes
porém como só vamos utilizar no summary é interessante fazer o calculo e trabalhar esses dados 
dentro dele.

- Para fazer isso foi criado uma const summary e utilizamos o metodo reduce que permite percorrer 
um array e reduzir esse array a alguma nova estrutura de dados, nesse caso queremos converter transactions em um array de objetos que tem a seguinte estrutura { income: 0, outcome: 0, total: 0 } 
para isso eu passei uma função como primeiro parametro do meu reducer e o segundo paramtro é a 
estrutura de dados inicial que se comeca que nesse caso é esse objeto, dentro dessa função do reducer
temos dois parametros um é o resumo atual que chamamos de acc (acumulation) esse acc nada mais é que o objeto que passamos nessa função, todas as operações dentro do Reducer irá acontecer dentro do 
acumulation e como segundo parametro será colocado a estrutura que vai ser recebida no nosso caso o 
transaction, para não ter erro com o typeScript essa função precisa retornar o proprio acc. Após isso 
eu posso dentro do meu reducer fazer as operações com o acc.

- Eu montei uma estrutura if que com cada interação que vai acontecer na lista de transações ela vai 
aumentando o income e o outcome do acc. O total quando for uma entrada ele vai aumentar o preço da transação e se for uma saída ele vai diminuir.

- Após isso basta jogar os dados do summary no meu código Tsx.

## Formatando Valores

- Aqui vamos ver os valores que não estão formatados em tela.

- Para trabalhar com essa formatação foi criada uma nova pasta chamada utils e dentro 
um arquivo chamado formatter.ts dentro desse arquivo foi criado os dois objetos de 
formatação.

- Utilizamos para a formatação o new Intl que é a api de internacionalização do proprio
javascript passando o DateTimeFormat para formatar as datas e o NumberFormat para os 
valores.

- Após isso eu vou nas páginas e utilizo esses objetos para fazer a conversão.

- Também criei uma condicional para que quando a minha transação for outcome ele colocar um sinal 
indicando negativo.       {transaction.type == 'outcome' && '-'}

- O nosso creatdAt vem como uma string e antes é necessário converter utilizando o new Date

## Criando hook para o resumo 

- Aqui vemos um poder que temos dentro do React que permite com que melhoremos a escrito do código
criando hooks próprios parte que calcula o resumo está dentro do proprio componente e está totalmente 
correto fazer dessa forma porém existe outra forma de se fazer que também é bem interessante.

- O React permite que a gente crie os nossos proprios hooks que nada mais são do que funções que 
utilizam os outros hooks do react com isso podemos utilizar dentro dos nossos componentes.

- Essa estratégia é bastante utilizada quando temos um código muito grande para fazer determinada
coisa dentro do componente.

- Criamos uma pasta chamada hooks onde criamos nossos hooks.
- Dentro da pasta criamos um arquivo para nosso hook chamado useSummary.ts
- depois eu vou lá no meu componente quando eu calculo a soma dos valores e recorto o código que faz 
isso  para dentro do meu hook e no final retorno summary.

- Depois basta eu utilizar meu hook dentro do componente       const summary = useSummary();

- com isso o código ficou muito mais simples por que foi abstraido o calculo do resumo em um hook
separado isso é muito util.

## Aplicando React hook form 

- Aqui configuramos o react hook form nos formularios da aplicação.

- Para trabalhar com react hook form é necessário instalar a lib com o comando abaixo , também utilizamos o zod para fazer validação.
       npm i react-hook-from zod

- Depois eu utilizo o useForm dentro do meu componente SeachForm utilizando a principio as funções
register e handleSubmit

- Dentro de input eu chamai o register passando o  nome do campo que chamamos de query geralmente 
quando queremos fazer uma busca e ela não é em um campo especifico, quando busca em varios campos 
de um registro ao mesmo tempo utiliza-se query.

- dentro do onSubmit eu chamei a função handleSubmit passando como argumento a função que criei 
handleSearchTransactions após isso eu importei o zod e criei meu schema que chamei de searchFormSchema

- Também adicionei a tipagem e como estou utilizando o zod eu pude utilizar o z.infer que vai me 
retornar exatamente a tipagem do nosso formulario.

- Também é necessário instalar mais uma lib 
        npm i @hookform/resolvers  

- Utilizei o zodResolver dentro do useForm. 

- Dentro do handleSearchTransactions eu passaei como dados SearchFormInputs e utilizei um 
console.log(data); para testar se os dados estão vindo passando corretamente para a quary.

- Dentro da desestruturação do meu useform eu utilizei o  formState e desestruturei de dentro dele o 
isSubmitting que vai retornar um true ou false que informa se o formulario está em estado de submit ou seja enviando as informações ou não. Com isso eu posso desabilitar o botão quando tiver isSubmitting
disabled={isSubmitting}.

- a função handleSearchTransactions pode ser transformada em uma async e podemos simular uma 
requisição de api para fazer algo demorar ali dentro , dando um await criando uma nova promise 
e resolver essa promise depois de dois segundos.

- Dentro do estilos do compoente SearchForm e dentro do botão eu escrevo o seguinte quando o botção 
estiver disabled vou diminuir a sua opacidade para 0.6 e no estado de hover só vai ser aplicado 
somente se ele não estiver disabled.

- Também fizemos o mesmo no componente NewTransactionModal que também tem um form.

- PS- Para converter o valor do input para numero eu utilizei o { valueAsNumber: true }.

## Controlled components 

- Aqui utilizamos uma funcionalidade do react hook form para conseguir o envio da informação no 
TransactionType de entrada e saída para dentro do formulario, quando queremos inserir uma informação 
que ela não vem de um campo nativo do htlm, é necessário utilizar uma api do react hook form de 
controle, nesse caso vamos utilizar o conceito decontrolled e para usar isso teremos dentro do 
useForm utilizar uma propriedade chamada control ou seja sempre que quisermos incluir uma informação
num formulário e essa informação não vem de um input ou qualquer elemento nativo do html é interessante
utilizar esse formato de control.

- Por Volta do TransactionType eu utilizo um componente que importo do react hook form  chamado 
Controller, dentro dele é passado a propriedade control que importamos em cima, passo também 
a propriedade name passando o nome do campo no nosso projeto o type que é a informação que 
queremos inserir, depois foi passado uma ultima propriedade que é o render que é uma função 
que retorna qual o conteudo que será relacionado a esse campo e dentro eu coloco o TransactionType.

- dentro da propriedade render eu desestruturei a propriedade field que me permite 
ter acesso a função onChange que é a função que anota o valor do campo type, eu 
passei atravéz da propriedade onValuechange que quando o valor do campo type mudar 
eu chamo a partir de field a função onChange com isso temos a informação do valor atual e podemos passar o value={field.value}. 

- Isso é importante por ex quando queremos iniciar o valor do campo type com um valor
padrão

- dando um console em field eu posso monitorar esses dados.