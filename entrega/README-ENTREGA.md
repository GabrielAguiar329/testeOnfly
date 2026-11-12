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
