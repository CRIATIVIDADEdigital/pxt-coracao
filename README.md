# Coração piscando

## Introdução 

Este programa faz com que os LEDs do Micro:bit pisquem a forma de um coração.  

## ~avatar

Qualquer dúvida na construção, use o **link (texto azul)** para abrir o vídeo que apresenta como realizar aquele passo. Para acessar o vídeo com o tutorial completo, use [**este link**](https://youtu.be/DXEgQ9iTP_g).

## ~

## Como funciona
1. [Baixe](https://youtu.be/DXEgQ9iTP_g?t=1m41s) o programa no seu computador.
1. [Conecte](https://youtu.be/DXEgQ9iTP_g?t=2m10s) o Micro:bit e [transfira](https://youtu.be/DXEgQ9iTP_g?t=2m51s) o arquivo HEX.
1. Ao término da transferência, o programa iniciará automaticamente em seu Micro:bit.

## Sugestões de modificação
Quer experimentar modificar este programa? Então, confira as sugestões apresentadas abaixo.

## Trocando o coração por um emoji
[O programa funciona](https://youtu.be/DXEgQ9iTP_g?t=5m29s) por meio de um *loop* (ou repetição) infinito em que o bloco  ``||basic:mostrar leds||`` primeiro apresenta a imagem de um coração. 
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

[Para alterar a imagem apresentada](https://youtu.be/DXEgQ9iTP_g?t=6m01s) na matriz de LEDs do Micro:bit, temos que alterar o conjunto de LEDs dentro do bloco ``||basic:mostrar leds||``.

Por exemplo, [experimente trocar o coração](https://youtu.be/DXEgQ9iTP_g?t=6m29s) por um *smile*. 
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
Após a alteração veja como ficou o programa [usando o simulador](https://youtu.be/DXEgQ9iTP_g?t=6m51s) ou baixando a nova versão do código no seu Micro:bit.

Agora, dê asas a sua imaginação.

Você pode fazer uma [carinha triste](https://youtu.be/DXEgQ9iTP_g?t=7m30s):
```blocks
    basic.showLeds(`
        . . . . .
        . # . # .
        . . . . . 
        . # # # .
        # . . . #`);
```

Uma ["caveira"](https://youtu.be/DXEgQ9iTP_g?t=7m54s):
```blocks
   basic.showLeds(`
        . # # # .
        # . # . #
        # # # # #
        . # # # .
        . # # # .`);
```

Uma ["seta para a direita"](https://youtu.be/DXEgQ9iTP_g?t=8m16s):
```blocks
   basic.showLeds(`
        . . . . .
        . . . # .
        # # # # #
        . . . # .
        . . . . .`);
```

## Sorteando uma imagem
[Podemos usar os recursos](https://youtu.be/DXEgQ9iTP_g?t=8m33s) do Micro:bit para fazer uma brincadeira em que, ao sacudi-lo, 
o Micro:bit apresenta automaticamente uma imagem diferente.

Para programar esta funcionalidade, vamos [utilizar o *acelerometro*](https://youtu.be/DXEgQ9iTP_g?t=8m46s) disponível no Micro:bit. 
Ele é capaz de medir um movimento aplicada à placa.  

Faremos isso usando dois blocos disponíveis para programação. Primeiro o ```||input:em agitar||```, 
que identifica automaticamente que a placa do Micro:bit foi movimentada, 
e depois o ```||math:escolher aleatório||``` para sortear qual imagem vai ser apresenta. 

[Acompanhe os passos](https://youtu.be/DXEgQ9iTP_g?t=9m34s) abaixo.

Primeiro vamos construir o trecho do programa que vai controlar o processo de sorteio da imagem.
1. [Coloque o bloco](https://youtu.be/DXEgQ9iTP_g?t=9m41s) ```||input:em agitar||``` na área de programação. Ele está disponível no grupo ```||input:Entrada||```.
1. [Crie uma variável](https://youtu.be/DXEgQ9iTP_g?t=10m02s) chamada ```||variable:imagem sorteada||```. Você faz isso por meio do grupo ```||variable:Variáveis||```.
1. [Ainda usando](https://youtu.be/DXEgQ9iTP_g?t=10m32s) o grupo ```||variable:Variáveis||``` arraste para dentro do ```||input:em agitar||``` o bloco ```||variable:definir imagem sorteada para||```.
1. [Vá até o grupo](https://youtu.be/DXEgQ9iTP_g?t=11m07s) ```||math:Matemática||``` e arraste o bloco ```||math:escolher aleatório||``` em cima do número ```||variable:0||``` presente na variável ```||variable:imagem sorteada||```.
1. [Altere os parâmetros](https://youtu.be/DXEgQ9iTP_g?t=11m59s) para que seja sorteado um número de ```||math:1||``` até ```||math:3||```.
1. O código vai ficar assim:

```blocks
    input.onGesture(Gesture.Shake, () => {
    let imagem_sorteada = Math.randomRange(1, 3)
})
```
[Agora que já temos](https://youtu.be/DXEgQ9iTP_g?t=12m31s) a imagem escolhida guardada na variável ```||variable:imagem sorteada||```,
vamos utilizar o valor escolhido (ou sorteado) para definir qual imagem o Micro:bit deverá apresentar. 
Usaremos o *loop* infinito ```||basic:sempre||``` para incluir a verificação de qual imagem deve ser apresentada.
1. [Primeiro vamos retirar todos os blocos](https://youtu.be/DXEgQ9iTP_g?t=13m04s) que estiverem dentro do ```||basic:sempre||``` para programarmos o controle do zero.
1. [Para controlar](https://youtu.be/DXEgQ9iTP_g?t=13m26s) qual imagem será apresentada, utilizaremos o bloco condicional ```||logic:se verdadeiro então||``` e de comparação ```||logic:0 = 0||```.  
1. Vá até o grupo ```||logic:Lógica||``` e arraste o bloco ```||logic:se verdadeiro então||``` para dentro do *loop* ```||basic:sempre||```.
1. [Ainda usando o grupo](https://youtu.be/DXEgQ9iTP_g?t=14m19s)  ```||logic:Lógica||``` arraste o bloco ```||logic:0 = 0||``` sobre o ```||logic:verdadeiro||```. 
1. [No grupo](https://youtu.be/DXEgQ9iTP_g?t=14m44s)  ```||variable:Variáveis||``` pegue o bloco ```||variable:imagem sorteada||``` e arraste sobre o primeiro ```||logic:0||``` do bloco ```||logic:se 0 = 0 então||```.
1. O código vai ficar assim:

```blocks
let imagem_sorteada = 0
basic.forever(function () {
    if (imagem_sorteada == 0) {
    	
    }
})
```
Pronto! Já temos tudo preparado para colocar as imagens que serão apresentadas de acordo com o número sorteado. Então vamos lá...
1. [Altere o primeiro](https://youtu.be/DXEgQ9iTP_g?t=15m25s) ```||logic:se||``` para que tenha o valor ```||logic:1||```. 
1. [Dentro do](https://youtu.be/DXEgQ9iTP_g?t=15m44s) ```||logic:se||``` use o bloco ```||basic:mostrar leds||```, que fica no grupo ```||basic:Básico||```, para apresentar a imagem do coração. 
1. [Na sequência](https://youtu.be/DXEgQ9iTP_g?t=16m21s), ao final do bloco ```||logic:se||```, coloque um ```||basic:mostrar leds||``` para que o coração fique piscando.

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
[Para acrescentar as próximas imagens](https://youtu.be/DXEgQ9iTP_g?t=17m02s) vamos repetir o processo acima, ou seja, acrescentar um bloco ```||logic:se||``` para cada imagem. 
Veja o resultado no trecho de código abaixo. Se for sorteado o número ```||logic:1||``` apresentamos um coração, 
se for sorteado o número ```||logic:2||``` apresentamos um "sorriso". 
Se for o número ```||logic:3||``` apresentamos uma "carinha triste".  

[Veja o resultado](https://youtu.be/DXEgQ9iTP_g?t=19m55s) final desta programação.
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
    if (imagem_sorteada == 2) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            # . . . #
            . # # # .
            `)
    }
    if (imagem_sorteada == 3) {
        basic.showLeds(`
            . . . . .
            . # . # .
            . . . . .
            . # # # .
            # . . . #
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
Após a alteração veja como ficou a brincadeira [usando o simulador](https://youtu.be/DXEgQ9iTP_g?t=20m28s) ou [baixando a nova versão do código](https://youtu.be/DXEgQ9iTP_g?t=21m39s) no seu Micro:bit.

[Você pode usar este programa](https://youtu.be/DXEgQ9iTP_g?t=22m50s) e o Micro:bit para brincar com a turma. Ele pode ser a função de um "dado" em um jogo. 
[Por exemplo](https://youtu.be/DXEgQ9iTP_g?t=24m02s), quem tirar coração vale 5 pontos. Se tirar uma carinha feliz ganha somente 1. Carinha triste não dá ponto nenhum...

E, claro, agora que já sabe como alterar o programa, [você pode criar](https://youtu.be/DXEgQ9iTP_g?t=24m21s) as suas próprias imagens e regras de sorteio.

## Créditos
Esta atividade foi criado pelo [APRENDER.digital](https://aprender.digital) usando como base o código do [Flashing Heart](https://makecode.microbit.org/projects/flashing-heart).
  
