# Coração piscando

## Introdução 

Este programa faz com que os LEDs do Micro:bit pisquem a forma de um coração.  

## Como funciona
1. Baixe o programa no seu computador.
1. Conecte o Micro:bit e transfira o arquivo HEX.
1. Ao término da transferência, o programa iniciará automaticamente em seu Micro:bit.

## Sugestões de modificação
Quer experimentar modificar este programa? Então, confira as sugestões apresentadas abaixo.

## Trocando o coração por um emoji
O programa funciona por meio de um *loop* (ou repetição) infinito em que o bloco  ``||basic:mostrar leds||`` primeiro apresenta a imagem de um coração. 
Em seguida ele é substituído por uma "imagem vazia". 

Veja abaixo.

```blocks
basic.forever(function() {
    basic.showLeds(`
        . # . # .
        # # # # #
        # # # # #
        . # # # .
        . . # . .
        `);
    basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .`);
})
```

Para alterar a imagem apresentada na matriz de LEDs do Micro:bit, temos que alterar o conjunto de LEDs dentro do bloco ``||basic:mostrar leds||``.

Por exemplo, experimente trocar o coração por um *smile*. 
```blocks
basic.forever(function() {
    basic.showLeds(`
        . . . . .
        . # . # .
        . . . . .
        # . . . #
        . # # # .`);
    basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .`);
})
```
Após a alteração veja como ficou o jogo usando o simulador ou baixando a nova versão do código no seu Micro:bit.

Agora, dê asas a sua imaginação.

Você pode fazer uma carinha triste:
```blocks
    basic.showLeds(`
        . . . . .
        . # . # .
        . . . . . 
        . # # # .
        # . . . #`);
```

Uma "caveira":
```blocks
   basic.showLeds(`
        . # # # .
        # . # . #
        # # # # #
        . # # # .
        . # # # .`);
```

Uma "seta para a direita":
```blocks
   basic.showLeds(`
        . . . . .
        . . . # .
        # # # # #
        . . . # .
        . . . . .`);
```

## Gerando uma imagem surpresa
Podemos usar os recursos do Micro:bit para fazer uma brincadeira em que, ao sacudi-lo, 
o Micro:bit apresenta automaticamente uma imagem diferente.

Para programar esta funcionalidade, vamos utilizar o *acelerometro* disponível no Micro:bit. 
Ele é capaz de medir um movimento aplicada à placa.  

Faremos isso usando dois blocos disponíveis para programação. Primeiro o ```||input:em agitar||```, 
que identifica automaticamente que a placa do Micro:bit foi movimentada, 
e depois o ```||math:escolher aleatório||``` para sortear qual imagem vai ser apresenta. 

Acompanhe os passos abaixo.

Primeiro vamos construir o trecho do programa que vai controlar o processo de sorteio da imagem.
1. Coloque o bloco ```||input:em agitar||``` na área de programação. Ele está disponível no grupo ```||input:Entrada||```.
1. Crie uma variável chamada ```||variable:imagem sorteada||```. Você faz isso por meio do grupo ```||variable:Variáveis||```.
1. Ainda usando o grupo ```||variable:Variáveis||``` arraste para dentro do ```||input:em agitar||``` o bloco ```||variable:definir imagem sorteada para||```.
1. Vá até o grupo ```||math:Matemática||``` e arraste o bloco ```||math:escolher aleatório||``` em cima do número ```||variable:0||``` presente na variável ```||variable:imagem sorteada||```.
1. Altere os parâmetros para que seja sorteado um número de ```||math:1||``` até ```||math:3||```.
1. O código vai ficar assim:

```blocks
    input.onGesture(Gesture.Shake, () => {
    let imagem_sorteada = Math.randomRange(1, 3)
})
```
Agora que já temos a imagem escolhida guardada na variável ```||variable:imagem sorteada||```,
vamos utilizar o valor escolhido (ou sorteado) para definir qual imagem o Micro:bit deverá apresentar. 
Usaremos o *loop* infinito ```||basic:sempre||``` para incluir a verificação de qual imagem deve ser apresentada.
1. Primeiro vamos retirar todos os blocos que estiverem dentro do ```||basic:sempre||``` para programarmos o controle do zero.
1. Para controlar qual imagem será apresentada, utilizaremos o bloco condicional ```||logic:se verdadeiro então||``` e de comparação ```||logic:0 = 0||```.  
1. Vá até o grupo ```||logic:Lógica||``` e arraste o bloco ```||logic:se verdadeiro então||``` para dentro do *loop* ```||basic:sempre||```.
1. Ainda usando o grupo ```||logic:Lógica||``` arraste o bloco ```||logic:0 = 0||``` sobre o ```||logic:verdadeiro||```. 
1. No grupo ```||variable:Variáveis||``` pegue o bloco ```||variable:imagem sorteada||``` e arraste sobre o primeiro ```||logic:0||``` do bloco ```||logic:se 0 = 0 então||```.
1. O código vai ficar assim:

```blocks
let imagem_sorteada = 0
basic.forever(function () {
    if (imagem_sorteada == 0) {
    	
    }
})
```
Pronto! Já temos tudo preparado para colocar as imagens que serão apresentadas de acordo com o número sorteado. Então vamos lá...
1. Altere o primeiro o ```||logic:se||``` para que tenha o valor ```||logic:1||```. 
Dentro dele use o bloco ```||basic:mostrar leds||```, que fica no grupo ```||basic:Básico||```, para apresentar a imagem do coração. 
Na sequência, ao final do bloco ```||logic:se||```, coloque um ```||basic:mostrar leds||``` para que o coração fique piscando.

```blocks
let imagem_sorteada = 0
basic.forever(function () {
    if (imagem_sorteada == 1) {
        basic.showLeds(`
            . # . # .
            # # # # #
            # # # # #
            . # # # .
            . . # . .
            `)
    }
    basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
})
```
Para acrescentar as próximas imagens vamos repetir o processo acima, ou seja, acrescentar um bloco ```||logic:se||``` para cada imagem. 
Veja o resultado no trecho de código abaixo. Se for sorteado o número ```||logic:1||``` apresentamos um coração, 
se for sorteado o número ```||logic:2||``` apresentamos um "sorriso". 
Se for o número ```||logic:3||``` apresentamos uma "carinha triste".  