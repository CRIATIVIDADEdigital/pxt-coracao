# Coração piscando

## Introdução @unplugged

Aprenda como fazer o painel de LEDs do Micro:bit piscar emojis.

## Passo 1 @fullscreen

Para ativar os leds do Micro:bit utizamos o bloco ``||basic:mostrar leds||`` no loop ``||basic:sempre||``.

## Passo 2 @fullscreen

Clique nas posições do ``||basic:mostrar leds||`` para ligar/desligar os LEDs do painel do Micro:bit. Para fazer piscar um *smile* configure o bloco ``||basic:mostrar LEDs||`` como indicado abaixo.

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

## Passo 3 @fullscreen
Experimente outras imagens:

```blocks
basic.forever(function() {
    basic.showLeds(`
        . . . . .
        . # . # .
        . . . . .
        . # # # .
        # . . . #`);
    basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .`);
})
```

```blocks
basic.forever(function() {
    basic.showLeds(`
        . # # # .
        # . # . #
        # # # # #
        . # # # .
        . # # # .`);
    basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .`);
})
```