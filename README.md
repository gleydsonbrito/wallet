# Boas vindas ao projeto final de Front-End

Para realizar o projeto, atente-se a cada passo descrito a seguir, e se tiver qualquer dúvida, perguntem! #vqv 🚀

Aqui você vai encontrar os detalhes de como estruturar o desenvolvimento do seu projeto a partir deste repositório.

Clone este repositório.

## Entregáveis

<details>
  <summary><strong>👨‍💻 O que deverá ser desenvolvido</strong></summary><br />

  Neste projeto você vai desenvolver uma carteira de controle de gastos com conversor de moedas, ao utilizar essa aplicação um usuário deverá ser capaz de:

- Adicionar, remover e editar um gasto;
- Visualizar uma tabelas com seus gastos;
- Visualizar o total de gastos convertidos para uma moeda de escolha;

</details>

<details>
  <summary><strong>:memo: Habilidades</strong></summary><br />

Neste projeto, verificamos se você é capaz de:

- Criar um _contextos_ usando contextAPI

- Além dos demais conhecimentos estudados na disciplina

</details>

## Orientações

<details>
  <summary><strong>‼️ Antes de começar a desenvolver</strong></summary><br />

  1. Após clonar e acessar o repositório, instale as dependências e inicialize o projeto
     - Instale as dependências:
       - `npm install`

</details>

<details>
  <summary><strong>⌨️ Durante o desenvolvimento</strong></summary><br />

- Faça `commits` das alterações que você fizer no código regularmente

- Lembre-se de sempre após um (ou alguns) `commits` atualizar seu repositório 

</details>

<details>
  <summary><strong id="como-desenvolver">:convenience_store: Desenvolvimento </strong></summary><br />

  Neste projeto você vai desenvolver uma carteira de controle de gastos com conversor de moedas, utilizando ContextAPI. Na implementação você deverá **preferencialmente** utilizar o seguinte formato do estado global:

```
  {
    user
      email: '', // string que armazena o email da pessoa usuária (Contexto user)
    ,
    wallet //contexto carteira
      currencies: [], // array de string contendo as moedas
      expenses: [], // array de gastos para popular cada linha da tabela de gastos, com cada objeto tendo as chaves id, value, currency, method, tag, description e exchangeRates
    }
  
```

  </details>

  <details><summary><b> :bulb: Documentação da API de Cotações de Moedas</b></summary>

  Sua página _web_ irá consumir os dados da API do _awesomeapi API de Cotações_ para realizar a busca de câmbio de moedas. Para realizar essas buscas, vocês precisarão consultar o seguinte _endpoint_:

- <https://economia.awesomeapi.com.br/json/all>

  O retorno desse endpoint será algo no formato:

  ```json
  {
    {
      "USD": {
        "code":"USD",
        "codein":"BRL",
        "name":"Dólar Americano/Real Brasileiro",
        "high":"5.6689",
        "low":"5.6071",
        "varBid":"-0.0166",
        "pctChange":"-0.29",
        "bid":"5.6173",
        "ask":"5.6183",
        "timestamp":"1601476370",
        "create_date":"2020-09-30 11:32:53"
        },
        ...
    }
  }
  ```

  Se você quiser aprender mais informações sobre a API, veja a [documentação](https://docs.awesomeapi.com.br/api-de-moedas).
  </details><br />

</details>

<details>
  <summary><strong>💻 Protótipo do projeto no Figma</strong></summary><br />

  Além da qualidade do código e do atendimento aos requisitos, um bom layout é um dos aspectos responsáveis por melhorar a usabilidade de uma aplicação!

  Para isso, disponibilizamos esse [protótipo do Figma](https://www.figma.com/file/ibAEAbS7A6EBprCvXJNhbt/%5BProjeto%5D%5BFrontend%5D-TrybeWallet?node-id=0%3A1) para lhe ajudar !

  ⚠️ A estilização de sua aplicação utilizando esse protótipo é apenas uma **sugestão** e seu uso é **opcional**. Sinta-se à vontade para modificar o layout e deixá-lo do seu jeito.

</details>

## Requisitos

## Página de Login

Crie uma página para que a pessoa usuária se identifique, com email e senha. Esta página deve ser a página inicial de seu aplicativo. **não** é necessário criar conta, nem cadastro de usuário. Apenas uma tela de login que não permita o usuário entrar sem prencher os campos. Caso o usuário não preencha um dos campos uma mensagem de erro de ser apresentada.

## Um item que acrescenta ao seu projeto é implementar uma função de **no no**. Quer dizer que se o usuário tentar realizar o login sem algum dos campos o formulário deverá reproduzir uma animação de **no no**. Esse item não é obrigatório, mas acrescenta muito ao seu projeto.

<details><summary> Página de Login</summary>

  ![image](./imgs/login.gif)
</details><br />

## 1. Crie uma página inicial de login com os seguintes campos e características

- A rota para esta página deve ser `/`;

- <details><summary> Você deve criar um local para que a pessoa usuária insira seu e-mail e senha:</summary>

  - O email precisa estar em um formato válido, como 'alguem@alguem.com' **veja como validar o padrão usando expressões regulares**;
  - A senha precisa possuir 6 ou mais caracteres.
  - Todas as informações acima precisam ser validadas.

</details>

- <details><summary> Crie um botão com o texto <code>Entrar</code>:</summary>

  - O botão precisa estar **desabilitado** caso o e-mail não tenha um formato válido ou a senha possua um tamanho menor que 6 caracteres;

  - Salve o email no estado global da aplicação, no contexto user com a chave **_email_**, assim que a pessoa usuária _logar_;

  - A rota deve ser mudada para `/carteira` após o clique no botão '**Entrar**'.

</details>

<br />
<details><summary><strong>O que será verificado</strong></summary><br />

- A rota para esta página é `"/"`
- É renderizado um elemento para que o usuário insira seu email e senha
- É renderizado um botão com o texto `"Entrar"`
- <details><summary> Foram realizadas as seguintes verificações nos campos de email, senha e botão:</summary>

  - É um e-mail no formato válido;
  - A senha tem 6 ou mais caracteres;
  - Desabilita o botão `Entrar` caso e-mail e/ou senha estiverem no formato inválido
  - Habilita o botão `Entrar` caso e-mail e senha sejam válidos
  </details><br />
- Salva o email no estado da aplicação, com a chave email, assim que o usuário logar
- A rota é alterada para `"/carteira"` após o clique no botão

</details>

---

## Página da Carteira

Crie uma página para gerenciar a carteira de gastos em diversas moedas e que traga a despesa total em real que é representado pelo código 'BRL'. Esta página deve ser renderizada por um componente chamado **_Wallet_**.

- A rota para esta página deve ser `/carteira`;

<details><summary> Página da carteira:</summary>
  
  ![image](./imgs/carteira.gif)
</details><br />

---

## Header

## 2. Crie um header para a página de carteira contendo as seguintes características

- O componente `Header` deve ser renderizado dentro do componente [`Wallet`](#página-da-carteira);

- <details><summary> Um elemento que exiba o e-mail da pessoa usuária que fez login:</summary>

  - :bulb: **Dica**: você deve pegar o e-mail do estado global da aplicação (com o contextAPI).

</details>

- <details><summary> Um elemento com a despesa total gerada pela lista de gastos:</summary>

  - Inicialmente esse elemento deve exibir o valor `0`;

</details>

- <details><summary> Um elemento que mostre qual câmbio está sendo utilizado, que neste caso será 'BRL': (Esse valor é fixo)</summary>

</details><br />

<details>
  <summary><strong>O que será verificado</strong></summary>

- O elemento renderiza o email salvo no estado global.
- O elemento inicialmente renderiza o valor `0`.
- O elemento renderiza o texto `BRL`.

</details>

---

## 3. Desenvolva um formulário para adicionar uma despesa contendo as seguintes características

- O componente `WalletForm` deve ser renderizado dentro do componente [`Wallet`](#página-da-carteira);

- <details><summary> Um campo para adicionar valor da despesa:</summary>

</details>

- <details><summary> Um campo para adicionar a descrição da despesa:</summary>

</details>

- <details><summary> Um campo para selecionar em qual moeda será registrada a despesa.</summary>

  - O campo deve ser um `<select>`.
  - As options devem ser preenchidas pelo valor da chave `currencies` do estado global (context wallet).
    - Os valores da chave <code>currencies</code> no estado global devem ser puxados através de uma requisição à API no endpoint `https://economia.awesomeapi.com.br/json/all`;
    - Remova, das informações trazidas pela API, a opção **USDT**;
    - A chave `currencies` do estado global deve ser um array.

</details>

- <details><summary> Um campo para adicionar qual método de pagamento será utilizado.</summary>

  - Este campo deve ser um `<select>`.
  - A pessoa usuária deve poder escolher entre os campos: 'Dinheiro', 'Cartão de crédito' e 'Cartão de débito' (Apenas essas opções).

</details>

- <details><summary> Um campo para selecionar uma categoria (tag) para a despesa.</summary>

  - O campo deve ser um `<select>`.
  - Este campo deve ser um dropdown. a pessoa usuária deve poder escolher entre os campos: 'Alimentação', 'Lazer', 'Trabalho', 'Transporte' e 'Saúde'.

</details>

<details>
  <summary><strong>Observações Importantes:</strong></summary><br />

  Note que os campos `<select>` já iniciam com um valor selecionado no seu navegador.

  Para ilustrar, imagine que o estado inicial seja uma string vazia. Neste caso a pessoa usuária poderá facilmente causar um problema onde ele acredita que a opção já está selecionada (uma vez que o select mostra um valor), quando na verdade ela ainda não está (o estado foi inicalizado com uma string vazia). Por esse motivo é importante sincronizar o mesmo valor inicial do `<select>` em seu estado no react, ao invés de inicializar com uma string vazia.
</details>

<br />

<details><summary> Ilustração do formulário</summary>

  ![image](./imgs/addItem.gif)
</details><br />

<details>
  <summary><strong>O que será verificado</strong></summary>

- O campo para adicionar o valor da despesa está presente.
- O campo para adicionar a descrição stá presente.
- O campo para selecionar em qual moeda será registrada a despesa stá presente.
  - A API é chamada com o endpoint `https://economia.awesomeapi.com.br/json/all`
  - O valor da chave `currencies` no estado global é um array que possui as siglas das moedas que vieram da API.
  - O campo para selecionar em qual moeda será registrada a despesa possui options com os valores iguais ao do array localizado na chave currencies do estado global.
- O campo para selecionar qual método de pagamento stá presente.
- O campo para selecionar qual método de pagamento será utilizado possui options com os valores `Dinheiro`, `Cartão de crédito` e `Cartão de débito`.
- O campo para selecionar uma categoria (tag) da despesa está presente.
- O campo para selecionar uma categoria (tag) da despesa possui options com os valores `Alimentação`, `Lazer`, `Trabalho`, `Transporte` e `Saúde`.

</details>

---

## 4. Salve todas as informações do formulário no estado global

- Crie um botão com o texto \'Adicionar despesa\'. Ele servirá para salvar as informações da despesa no estado global e atualizar a soma de despesas no header.

- <details><summary> Desenvolva a funcionalidade do botão "Adicionar despesa" de modo que, ao clicar no botão, as seguintes ações sejam executadas:</summary>

  - <details><summary> Os valores dos campos devem ser salvos no estado da aplicação, na chave <b><i>expenses</i></b>, dentro de um array contendo todos gastos que serão adicionados:</summary>

    - O `id` da despesa **deve** ser um número sequencial, começando em 0. Ou seja: a primeira despesa terá id 0, a segunda terá id 1, a terceira id 2, e assim por diante.
    - :bulb: **Atenção nesse ponto**: você deverá fazer uma requisição para a API e buscar a cotação no momento que o botão de `Adicionar despesa` for apertado.
    </details>

  - <details><summary> Após adicionar a despesa:</summary>

    - Atualize a soma total das despesas (utilize a chave `ask` para realizar essa soma). Essa informação deve ficar no [`header`](#2-crie-um-header-para-a-página-de-carteira-contendo-as-seguintes-características) dentro do elemento com `data-testid="total-field"`;
      - O valor total deverá ser exibido com 2 casas decimais. Exemplo: (valor - ponto - duas casas decimais) `100.00` `23.50`
      - Limpe os inputs de valor e descrição.
    </details>

  - <details><summary> As despesas salvas no estado global ficarão com um formato semelhante ao seguinte:</summary>

      ```javascript
      expenses: [{
        "id": 0,
        "value": "3",
        "description": "Hot Dog",
        "currency": "USD",
        "method": "Dinheiro",
        "tag": "Alimentação",
        "exchangeRates": {
          "USD": {
            "code": "USD",
            "name": "Dólar Comercial",
            "ask": "5.6208",
            ...
          },
          "CAD": {
            "code": "CAD",
            "name": "Dólar Canadense",
            "ask": "4.2313",
            ...
          },
          "EUR": {
            "code": "EUR",
            "name": "Euro",
            "ask": "6.6112",
            ...
          },
          "GBP": {
            "code": "GBP",
            "name": "Libra Esterlina",
            "ask": "7.2498",
            ...
          },
          "ARS": {
            "code": "ARS",
            "name": "Peso Argentino",
            "ask": "0.0729",
            ...
          },
          "BTC": {
            "code": "BTC",
            "name": "Bitcoin",
            "ask": "60299",
            ...
          },
          "LTC": {
            "code": "LTC",
            "name": "Litecoin",
            "ask": "261.69",
            ...
          },
          "JPY": {
            "code": "JPY",
            "name": "Iene Japonês",
            "ask": "0.05301",
            ...
          },
          "CHF": {
            "code": "CHF",
            "name": "Franco Suíço",
            "ask": "6.1297",
            ...
          },
          "AUD": {
            "code": "AUD",
            "name": "Dólar Australiano",
            "ask": "4.0124",
            ...
          },
          "CNY": {
            "code": "CNY",
            "name": "Yuan Chinês",
            "ask": "0.8278",
            ...
          },
          "ILS": {
            "code": "ILS",
            "name": "Novo Shekel Israelense",
            "ask": "1.6514",
            ...
          },
          "ETH": {
            "code": "ETH",
            "name": "Ethereum",
            "ask": "5184",
            ...
          },
          "XRP": {
            "code": "XRP",
            "name": "Ripple",
            "ask": "1.4",
            ...
          }
        }
      }]
      ```

    </details>

</details><br />
<details>
  <summary><strong>O que será verificado</strong></summary>

- É renderizado um botão com o texto "Adicionar despesa".
- Ao clicar no botão "Adicionar despesa"
  - é feita uma requisição a API
  - é salva uma nova despesa na chave `expenses` do estado global
  - o valor total do elemento de valor total é atualizado.
  - cada despesa possui um id sequencial.
  - os inputs de valor e descrição voltam ao valor inicial, contendo o valor `""`
  - é exibido o total das despesas com 2 casas decimais no elemento, levando em consideração a cotação localizada na chave `ask`.

</details>

---

## Tabela de Gastos

## 6. Desenvolva uma tabela com os gastos contendo as seguintes características

- O componente `Table` deve ser renderizado dentro do componente [`Wallet`]
**é possível usar uma tabela HTML ou um GRID para criar a tabela de gastos**(#página-da-carteira);

- <details><summary> A tabela deve possuir um cabeçalho com os seguintes valores:</summary>

  - Descrição;
  - Tag;
  - Método de pagamento;
  - Valor;
  - Moeda;
  - Câmbio utilizado;
  - Valor convertido;
  - Moeda de conversão;
  - Editar/Excluir (Botões ou ícones).
 
</details><br />

<details>
  <summary><strong>O que será verificado</strong></summary>

- A tabela possui um cabeçalho com elementos `<th>` com os valores `Descrição`, `Tag`, `Método de pagamento`,`Valor`, `Moeda`, `Câmbio utilizado`, `Valor convertido`, `Moeda de conversão` e `Editar/Excluir`.

</details>

---

## 7. Implemente a lógica para que a tabela seja alimentada pelo estado da aplicação

- <details><summary> A tabela deve ser alimentada pelo estado da aplicação, que estará disponível na chave <b><i>expenses</i></b> que vem do <i>estado global</i> <code>wallet</code>:</summary>

  - O campo de `Moeda` deverá conter o nome da moeda. Portanto, ao invés de 'USD' ou 'EUR', deve conter "Dólar Americano/Real Brasileiro" e "Euro/Real Brasileiro", respectivamente;

  - O elemento que exibe a `Moeda de conversão` deverá ser sempre 'Real';

  - Atenção também às casas decimais dos campos. Como são valores contábeis, eles devem apresentar duas casas após o ponto. Arredonde sua resposta somente na hora de renderizar o resultado e, para os cálculos, utilize sempre os valores vindos da API (utilize o campo `ask` que vem da API).

  - Utilize sempre o formato `0.00` (número - ponto - duas casas decimais).

</details><br />

<details>
  <summary><strong>O que será verificado</strong></summary>

- A tabela é atualizada com as informações vindas da chave `expense` do estado global.
</details>

---

## 8. Crie um botão para deletar uma despesa da tabela contendo as seguintes características

<details><summary> Ilustração do botão</summary>

  ![image](./imgs/deleteBtn.gif)
</details>

- O botão deve ser o último item da linha da tabela

- Após o botão ser clicado, a seguintes ações deverão ocorrer:
  - A despesa deverá ser deletada do estado global
  - A despesa deixará de ser exibida na tabela
  - O valor total exibido no header será alterado.

<br /><details>
  <summary><strong>O que será verificado</strong></summary>

- O botão se encontra no último elemento da tabela.
- Ao clicar no botão, a despesa é removida do estado global e consequentemente da tabela.
- Ao clicar no botão, a despesa total é atualizada no header, subtraindo o valor correspondente.

</details>

---

## 9. Crie um botão para editar uma despesa da tabela contendo as seguintes características

<details><summary> Ilustração do botão</summary>

  ![image](./imgs/editBtn.gif)
</details>

- O botão deve estar dentro do último item da linha da tabela antes do botão deletar

- <details><summary> Ao ser clicado, o botão habilita um formulário para editar a linha da tabela. Ao clicar em "Editar despesa" ela é atualizada, alterando o estado global.</summary>

  - O formulário deverá ter os mesmos campos. Você pode reaproveitá-lo.

  - O botão para submeter a despesa para edição deverá conter  o texto "Editar despesa"

  - Após a edição da despesa, a ordem das despesas na tabela precisa ser mantida.

  - :bulb: **Obs**: para esse requisito, não é necessário popular os inputs com os valores prévios da despesa. A imagem do gif é apenas uma sugestão.

  - :bulb: Lembre-se de utilizar o formato do estado global da aplicação  <a href="#como-desenvolver">Desenvolvimento</a>

  - **Atenção**: o câmbio utilizado na edição deve ser o mesmo do cálculo feito na adição do gasto.

</details><br />

<details>
  <summary><strong>O que será verificado</strong></summary>

- O botão se encontra no último elemento .
- Ao ser clicado, o formulário de adição passa a ser um formulário de edição.
- Ao ser clicado, o botão com o texto `"Adicionar Despesa"` é alterado para `"Editar despesa"`.
- Após editar uma despesa a chave `expenses` no estado global é atualizada com o novo valor.
- A ordem das despesas é mantida após a edição.
- O valor no campo com o `data-testid="total-field"` é atualizado após a edição de uma despesa.

</details>

