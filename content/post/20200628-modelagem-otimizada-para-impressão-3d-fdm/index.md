---
title: Modelagem otimizada para impressão 3D FDM
subtitle: Como modelar um objeto de forma eficiente para imprimir em 3D?
description: Conheça boas práticas para produzir objetos de forma ágil e resistente
date: 2020-06-28T01:22:21.923Z
authors:
  - Pedro Emmel
image: 3d-printer.jpg
thumbnail: 3d-printer.jpg
categories:
  - 3D
  - equipamento
  - modelagem
tags:
  - impressão 3d
  - modelagem3d
  - fusion360
  - autodesk
  - prototipação
  - projeto
  - equipamento
---
# Introdução

Existem diferentes formas de modelar um mesmo objeto em 3D porém quando se trata de tornar esse modelo algo palpável precisamos conhecer muito bem as capacidades e limitações da técnica de fabricação digital que iremos empregar caso contrário essa tarefa pode se tornar demorada, custosa e inceficiente.  Vamos primeiramente compreender o funcionamento da tecnologia e seguimos para um exemplo prático



# Impressão 3D FDM

A impressão FDM (Fused Deposition Modeling) é uma das técnicas impressão mais amplamente utilizadas para fabricação de protótipos e peças funcionais. O processo é baseado na extrusão de polímero através de um bico aquecido, o material é depositado em uma plataforma formando a camada inicial que serve de base para a deposição das demais camadas acima. Todo o processo funciona através de cordenadas e comandos gerados por um software específico para esta tarefa. A simplicidade, confiabilidade e custo da impressão FDM tornou esta tecnologia amplamente adotada e reconhecida no meio indústrial, acadêmico e até mesmo comercial.  Sua grande vantagem está na eficiência e flexibilidade de produção, enquanto outras tecnologias levariam meses para materializar uma prova de conceito a impressão 3d é capaz de realizar esta tarefa em algumas horas. Outra grande vantagem é a possibilidade de realizar rápidas alterações aos modelos e em uma mesma máquina, inclusive ao mesmo tempo imprimir diferentes objetos. Seu uso em departamentos de P&D tornou-se indispensável devido ao volume de testes e alterações que rotineiramente acontecem ao desenvolver um novo produto.

![](c2c56986e5242fca-3d-printing-a-look-at-four-types-of-additive-manufacturing.gif)

# Modelando para fabricação FDM

Ao desenhar um objeto em 3d a ser produzido com a FDM precismos observar algumas características para tirar o melhor da tecnologia.

esqueleto: 

não é possível depositar material no ar\
\
velocidade em Z inferior a XY 

Resistência inferior em Z