# Projeto de Circuitos Digitais – Minigame de Adivinhação

## Descrição

Este projeto foi desenvolvido utilizando o Logisim ITA e consiste em um minigame no qual o usuário deve adivinhar um número aleatório entre 0 e 15, representado em binário. O circuito informa o quão próximo o palpite está do número sorteado por meio de LEDs RGB, além de indicar o acerto através de um LED dedicado e exibir valores em displays de sete segmentos.

## Funcionamento Geral

O usuário seleciona um número binário de 4 bits através das entradas do circuito e pressiona o botão de confirmação. O sistema compara o valor informado com o número gerado internamente e fornece um retorno visual sobre o resultado do palpite.

Caso o usuário acerte o número, o LED de acerto é ativado. Caso contrário, os LEDs RGB indicam a distância entre o chute e o número sorteado, permitindo ao jogador ajustar suas próximas tentativas.

## Componentes Implementados

### Entradas do Usuário

As entradas permitem que o jogador informe um valor entre 0 e 15 em formato binário. Um botão de confirmação registra o palpite e um botão de reset reinicia o funcionamento do circuito gerando um novo número aleatório.

### Conversão para Displays

Os valores binários são convertidos para displays de sete segmentos por meio de decodificadores, permitindo a visualização dos números em formato decimal.

### Comparação dos Valores

O circuito compara o número escolhido pelo usuário com o número armazenado internamente, verificando se houve acerto ou erro.

### Indicador de Acerto

Quando o palpite coincide com o número sorteado, um LED específico é acionado para indicar a vitória do jogador.

### Sistema de Proximidade

Para tornar o jogo mais intuitivo, foi planejado um sistema baseado em LEDs RGB para indicar o quão distante o palpite está do valor correto. A proposta consiste em utilizar diferentes combinações de cores para representar a proximidade entre o valor informado pelo usuário e o número sorteado, permitindo ao jogador ajustar suas próximas tentativas de forma mais eficiente.

* Esta funcionalidade ainda se encontra em fase de implementação no momento da elaboração desta documentação.

### Cálculo da Distância

A distância entre os valores foi obtida a partir do módulo da diferença entre o número informado pelo usuário e o número sorteado.

Foi utilizada uma abordagem baseada na inversão dos bits dos operandos quando o primeiro valor era menor que o segundo. Em um sistema de 4 bits, essa operação transforma A em (15 − A) e B em (15 − B), fazendo com que a subtração resulte em B − A, equivalente ao valor absoluto da diferença.

Embora diferente da abordagem convencional baseada em complemento de 2, a solução produz o mesmo resultado para o cálculo da distância entre os valores e foi adotada na implementação do circuito.
