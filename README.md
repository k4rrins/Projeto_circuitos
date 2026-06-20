# Projeto de Circuitos Digitais – Minigame de Adivinhação

## Descrição

Este projeto foi desenvolvido utilizando o **Logisim ITA** e consiste em um minigame no qual o usuário deve adivinhar um número aleatório entre **0 e 15**, representado em binário.

O sistema fornece ao jogador informações sobre o resultado de cada tentativa por meio de LEDs e displays de sete segmentos, permitindo identificar tanto o acerto quanto a proximidade em relação ao número sorteado.


# Funcionamento Geral

O usuário informa um número binário de 4 bits através das entradas do circuito e pressiona o botão de confirmação.

O circuito compara o valor informado com o número gerado internamente e fornece um retorno visual ao jogador.

* Caso o número esteja correto, um LED de acerto é acionado.
* Caso o valor esteja incorreto, o LED RGB indica o quão próximo o palpite está do número sorteado.
* Os valores são exibidos em displays de sete segmentos para facilitar a visualização.


# Entradas e Controles

O sistema possui os seguintes controles:

* **Chute (4 bits):** permite ao usuário escolher um valor entre 0 e 15.
* **Botão Confirmar:** registra o palpite do jogador.
* **Botão Reset:** reinicia o circuito e gera um novo número aleatório.


# Arquitetura do Circuito

O projeto foi dividido em diversos subcircuitos, permitindo uma implementação modular e facilitando a compreensão do funcionamento do sistema.

## Gerador de Número Aleatório

O número a ser adivinhado é gerado pelo componente **Random** do Logisim, configurado para trabalhar com 4 bits, produzindo valores entre 0 e 15.

A cada reinicialização do circuito por meio do botão de reset, um novo número é gerado.


## Comparador de Valores

O circuito responsável pela verificação do acerto foi implementado utilizando portas XNOR.

Cada par de bits correspondente do número informado pelo usuário e do número sorteado é comparado individualmente por uma porta XNOR, que produz nível lógico alto quando os dois bits são iguais.

Os resultados dessas comparações são então combinados por uma porta AND, de forma que o sinal de acerto só seja ativado quando todos os quatro bits coincidirem simultaneamente.

Quando a igualdade é detectada, o LED de vitória é acionado, indicando que o jogador acertou o número.


## Sistema de Proximidade

Para tornar o jogo mais intuitivo, foi implementado um sistema baseado em LED RGB que indica o quão próximo o palpite está do número correto.

A cor apresentada varia de acordo com a distância entre os valores, permitindo que o usuário ajuste suas próximas tentativas.


# Cálculo da Distância

A distância entre os valores é obtida a partir do módulo da diferença entre o número informado pelo usuário e o número sorteado.

Foi utilizada uma abordagem baseada na inversão dos operandos quando o primeiro valor é menor que o segundo. Em um sistema de 4 bits, essa operação transforma:

* A em (15 − A)
* B em (15 − B)

Dessa forma, a subtração produz o valor:

**B − A**

obtendo-se o valor absoluto da diferença.

Embora diferente da abordagem tradicional baseada em complemento de 2, a solução produz corretamente a distância entre os valores e foi adotada na implementação do circuito.


# Subcircuito de Diferença

O módulo responsável pelo cálculo da diferença é composto por:

* Verificador de qual operando possui maior valor;
* Circuito de subtração;
* Seleção da ordem dos operandos.

Esse conjunto garante que a distância entre os números seja sempre positiva.


# Verificação A < B

Foi desenvolvido um subcircuito específico responsável por verificar se o valor informado pelo usuário é menor que o número sorteado.

Essa informação é utilizada pelo módulo de diferença para determinar a ordem correta da subtração.


# Subtrator Completo

O circuito de subtração foi implementado manualmente através de portas lógicas.

O subcircuito utiliza:

* Portas XOR;
* Portas AND;
* Portas OR.

Essa implementação realiza a subtração bit a bit, produzindo tanto a diferença quanto os sinais necessários para o funcionamento do circuito.


# Decodificador para Display de Sete Segmentos

Os displays de sete segmentos são controlados por um decodificador desenvolvido utilizando portas lógicas.

Cada segmento do display é acionado individualmente, permitindo a conversão dos valores binários em números decimais.

O decodificador foi implementado manualmente, sem a utilização de componentes prontos do Logisim, proporcionando maior compreensão do funcionamento interno da conversão binário-decimal.


# Componentes Utilizados

* Portas AND
* Portas OR
* Portas XOR
* Portas XNOR
* Portas NOT
* Gerador aleatório
* LED de acerto
* LED RGB
* Displays de sete segmentos
* Botões de confirmação e reset
