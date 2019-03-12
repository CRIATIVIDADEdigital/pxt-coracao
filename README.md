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

## Criando uma imagem surpresa
Podemos usar os recursos do Micro:bit para fazer uma brincadeira em que, ao sacudi-lo, 
o Micro:bit apresenta automaticamente uma imagem diferente.

Para programar esta funcionalidade, vamos utilizar o *acelerometro* disponível no Micro:bit. 
Ele é capaz de medir um movimento aplicada à placa.  

Faremos isso usando dois blocos disponíveis para programação. Primeiro o ```||input:em agitar||```, 
que identifica automaticamente que a placa do Micro:bit foi movimentada, 
e depois o ```||math:escolher aleatório||``` para sortear qual imagem vai ser apresenta. 

Acompanhe os passos abaixo.
1. Coloque o bloco ```||input:em agitar||``` na área de programação. Ele está disponível no grupo ```||input:Entrada||```.
1. Crie uma variável chamada ```||variable:imagem sorteada||```. Você faz isso por meio do grupo ```||variable:Variáveis||```.
1. Ainda usando o grupo ```||variable:Variáveis||``` arraste para dentro do ```||input:em agitar||``` o bloco ```||variable:definir imagem sorteada para||```.
1. Vá até o grupo ```||math:Matemática||``` e arraste o bloco ```||math:escolher aleatório||``` em cima do número ```||variable:0||``` presente na variável ```||variable:imagem sorteada||```. 