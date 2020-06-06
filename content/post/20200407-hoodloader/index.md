---
layout:         post 
title:          "O Arduino Uno tem 2 microcontroladores!"
subtitle:       "E vou te mostrar como usá-los :)"
description:    "Artigo explicando como utilizar independentemente os dois microcontroladores que os Arduinos Uno e Mega possuem."
date:           2020-04-07
author:         "Alexandre Alvaro"
image:          "/post/20200407-hoodloader/capa.jpg"
thumbnail:      "/post/20200407-hoodloader/thumb.jpg"
categories:     [ Arduino ]
tags:
                - arduino
                - tutorial
                - intermediário
                - prototipação
                - eletrônica
                - iot
---

# Introdução
O Arduino é uma plataforma de eletrônica de baixo custo, open source, baseada em hardware e software fáceis de usar.

As placas do Arduino são capazes de ler entradas - luz em um sensor, um dedo em um botão, uma mensagem no Twitter - e transformá-las em uma saída - ativando um motor, ligando um LED, publicando algo online. 

Por padrão, a programação é feita utilizando uma linguagem baseada em C/C++, sem a necessidade de equipamentos extras além de um cabo USB.

O que vamos tratar neste artigo demanda um conhecimento intermediário de Arduíno, mas se você se interessou e quiser entender mais sobre o assunto, dá uma olhada [nesse material sensacional sobre o assunto no Manual do Mundo](https://youtu.be/sv9dDtYnE1g).

...

# Bom… bora começar!

As vezes focamos em algo principal e nos esquecemos dos detalhes.  
O Arduino Uno tem como microcontrolador principal o ATmega328p, assim como o Mega tem o Mega2560, certo?  
Mas eles também têm um outro microcontrolador, o 16u2, que geralmente ignoramos, pois achamos que “ele só serve pra fazer a comunicação USB com o computador”.  
Bom… na verdade se olharmos para o Arduino Pro Micro e o Leonardo por exemplo, notamos que eles usam o 32u4, que é um microcontrolador similar ao 16u2 que vem com o Uno/ Mega, sendo que este último tem menos memória, pinos, e outros recursos, porém é um microcontrolador totalmente funcional e também podemos usá-lo!  
O que quero dizer é que é possível ter 2 microcontroladores trabalhando ao mesmo tempo e de forma independente na mesma placa. É como se tivéssemos uma versão mais simples do Arduino Leonardo/ Micro embutido no Arduino Uno/ Mega!!!  
Pra ter acesso a esse microcontrolador (16u2) pela IDE do Arduino vamos precisar alterar o Bootloader padrão (que é o DFU no Uno/Mega e CDC no Leonardo/Micro) por um Bootloader CDC + Fast USB-Serial tudo junto, o [Hoodloader2](https://github.com/NicoHood/HoodLoader2).  
![](1.jpg)

>*Só verifique, pois, alguns Arduinos usam o CH340G, que é apenas conversor serial para ser mais barato.  
Aí não funciona 🙁

# Instalação do Hoodloader2

Para fazer uso do 16u2 usamos o próprio ATmega328p para configurá-lo. Mudando o bootloader, não o firmware. Pra isso basta usar o próprio Arduino, 1 cabo USB, 4 fios e um capacitor de 100nF.

1) Prepare o seu arduino: Não deixe nenhum componente ou fiação.

2) Faça download do sketch de instalação clicando no link.

{{< rawhtml >}}
    <div style="width:210px">
       <a href="https://drive.google.com/file/d/1-7QA6vro2y2pgKnfFBE6pauRNGdwlwL6/view?usp=sharing"><img src="2.png" style="cursor: pointer;" /></a>
    </div>
{{< /rawhtml >}}

3) Descompacte o conteúdo e abra o sketch Installation_Sketch.ino na IDE do Arduino.

4) Se necessário mude a configuração HEXFILE para a sua placa.

![](3.png)

5) Conecte o cabo USB, selecione a sua placa normalmente (como faz para descarregar qualquer sketch) e carregue o sketch para a placa.

6) Espere até aparecer “Done uploading“. Vai demorar um tempinho.

7) Desconecte o cabo USB do Arduino.

8) Conecte os cabos e componentes no Arduino conforme imagem:

![](4.jpg)

>*É a mesma configuração para o Mega2560

```
Capacitor 100nF:
328/2560 RESET - GND

Conexões dos pinos:
328/2560 - 16u2
MOSI     - MOSI
MISO     - MISO
SCK      - SCK
PIN 10   - 16u2 RESET
```

9) Sobrescreva o bootloader:

Uma vez que o microcontrolador principal estiver com o sketch, nós estamos aptos a sobrescrever o bootloader para o 16u2.

Este processo acontece sem a interação do usuário!

Verifique novamente se as conexões estão corretas, plugue o arduino na porta USB e espere.

O led vai piscar lentamente por 10 segundos, tentar sobrescrever o bootloader e depois piscar rapidamente (a cada 100ms). Espere pelo menos 30 segundos antes de remover o cabo USB, para ter certeza que tudo ocorreu como deveria.

Caso tenha problemas, consulte o [FAQ oficial](https://github.com/NicoHood/HoodLoader2/wiki/Troubleshoot-FAQ) (em inglês).

Desconecte o capacitor e fiações e pode começar a utilizar os 2 microcontroladores!

# Utilizando os 2 microcontroladores

## Sobre o Hardware.. Como fica a pinagem?

![](5.jpg)

No 16u2 Nós passamos a ter acesso a 7 pinos (fundo cor creme na imagem acima):

D1 – PB1 PCINT1 SCLK
D2 – PB2 PCINT2 MOSI
D3 – PB3 PCINT3 MISO
D4 – PB4 PCINT4
D5 – PB5 PCINT5
D6 – PB6 PCINT6
~D7 – PB7 PCINT7 TIMER1C PWM
…

Dica: Para facilitar o uso, gosto de soldar conectores nos pinos PB4, PB5, PB6 e PB7:

![](6.jpg)


Configurando a IDE do Arduino
A instalação de novos drivers não é necessária para Windows10/ MacOS/ Linux. Mas se estiver usando Windows 7/ 8 siga as [etapas de instalação dos drivers CDC](https://github.com/NicoHood/HoodLoader2/wiki/Software-Installation#1-cdc-driver-installation-windows-78-only).

1) Abra as preferências da IDE e adicione o endereço a seguir no campo “URLs Adicionais para Gerenciadores de Placas”

```
https://raw.githubusercontent.com/NicoHood/HoodLoader2/master/package_NicoHood_HoodLoader2_index.json
```

![](7.png)

2) Instale o Hoodloader2 pelo Gerenciador de Placas (Ferramentas > Placa > Gerenciador de Placas)

![](8.png)

# Certo! E como descarrego meus Sketches?

Depois de configurado na IDE do Arduino e alterado o Bootloader do 16u2, basta selecionar se quer descarregar o Sketch para o 16u2 ou para o ATmega328p (ou Mega2560).

![](9.jpg)

Para ter os 2 sketches rodando descarregue primeiro do ATmega328p/ Mega2560 e somente depois o do 16u2. Se descarregar ao contrário ele vai considerar apenas o que foi pro ATmega328p/ Mega2560.

Ah!… e uma coisa bacana do 16u2 é que, assim como os Arduinos Leonardo e Pro Micro, ele pode funcionar como uma conexão plug n’ play com o USB do PC, da TV, do Android, do videogame (Conhecido como HID – Human interface Device), … Ou seja, sem precisar de driver de instalação, assim como os teclados, mouses e joysticks fazem.

Pronto! Agora utilize sua criatividade para tirar vantagem do uso dos 2 microcontroladores simultaneamente!

# Alguns exemplos de aplicação:

[HID-Project](https://github.com/NicoHood/HID)

[Simple HID Bridge](https://github.com/NicoHood/HoodLoader2/tree/master/avr/examples/HID-Bridge)

[USB-Serial](https://github.com/NicoHood/HoodLoader2/blob/master/avr/examples/USB-Serial/USB-Serial.ino)

[Run Bootloader](https://github.com/NicoHood/HoodLoader2/blob/master/avr/examples/RunBootloader/RunBootloader.ino)

[Blink](https://github.com/NicoHood/HoodLoader2/blob/master/avr/examples/Blink/Blink.ino)

[PWM Fade](https://github.com/NicoHood/HoodLoader2/blob/master/avr/examples/PWM_Fade/PWM_Fade.ino)

[Serial Keyboard](https://github.com/NicoHood/HoodLoader2/blob/master/avr/examples/SerialKeyboard/SerialKeyboard.ino)

# Referências

https://github.com/NicoHood/HoodLoader2