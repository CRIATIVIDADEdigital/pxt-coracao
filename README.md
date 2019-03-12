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
        . . . . .
        . . . # .
        # # # # #
        . . . # .
        . . . . .
        `);
```