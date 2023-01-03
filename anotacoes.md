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