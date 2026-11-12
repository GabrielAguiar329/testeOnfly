# Primeiro erro solucionado
## Conversão de valores para BRL

O primeiro erro solucionado foi a da conversão dos valores para BRL. O erro foi causado por um siples erro de lógica no
 /service/currency_converter.py, onde no fim do método estava retornando a divisao entre  o **amount** e o **rate**. Descobri o motivo
  do erro após observar o os resultados dos testes e ver que dava um valor anormalmente baixo, e observando o método, encontrei a divisão e a troquei por uma multiplicação!

### Testes passados após mudança

Após a mudança no método de conversão dois testes foram solucionados, o teste  **test_currency.py** e também **test_regression_report.py**

# Segundo erro solucionado
## erro de cálculo das diárias de diferentes meses

esse erro é bem parecido com o primeiro, era causado por que o método do calculo apenas subtraia os dias do checkin e do checkout, fazendo dar o valor de -28 no teste.
para solucionar, criei uma variavel *nights* e atribui o valor de chackout menos checkin com o atributo **days** atributo que calcula a diferença entre duas datas. após, retornei a multiplicação de *nights* por *rooms* como pedia o comentário do método.

### Testes passados após mudança

após a mudança do método solucionei **test_nights.py**

# terceiro erro solucionado
## Falha na validação dos status faturaveis

O método responsavél por validar os status das reservas estava retornando ao contrario do que a lógica pedia, o método excluia apenas as reservas com o *status* igual a 
*"CANCELED"*, mantendo as reservas com status de *"NO_SHOW"* e as considerando faturável. para corrigir, eu em vez de verificar se o status **não** é "CANCELED", comecei a verificar se **É** "CONFIRMED". Assim, somente reservas confirmadas entram no faturamento. Descobri que o erro era no método após observer que no teste aparecia o *amount* de cada status, e como estava passando 120, e o valor correto era 100, o erro estava contabilizando o "NO_SHOW".

### Testes passados após mudança

após a mudança do método solucionei **test_status_rules.py**

# Quarto erro solucionado
## Erro na ordenação do ranking de hotéis

O erro estava na ordenação da lista de hotéis no arquivo **report_builder.py**. O método *sorted()* estava organizando os hotéis em ordem crescente de faturamento, fazendo com que os hotéis com menor receita aparecessem primeiro. Identifiquei o problema ao analisar a ordenação e perceber que ela não correspondia ao ranking esperado. Para corrigir, adicionei o sinal negativo antes do valor de faturamento na função *lambda*, invertendo a ordem para decrescente. Assim, os hotéeis com maior faturamento passaram a aparecer primeiro.

### Testes passados após mudança

Após a alteração, solucionei o teste **test_top_hotels.py**.