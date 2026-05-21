# Pong Game Using Microcontroller And Computer Interface

[![Assista ao Vídeo](https://img.shields.io/badge/YouTube-Video_Explicativo-red?logo=youtube)](https://youtu.be/zmxPOv1QS3Y)
[![Simulação Tinkercad](https://img.shields.io/badge/Tinkercad-Simula%C3%A7%C3%A3o_do_Sistema-blue)](https://www.tinkercad.com/things/4twfonFw2j7)

Este projeto consiste na recriação e modernização do clássico jogo **"Pong"** (originalmente criado pela Atari Inc. em 1972) através de uma composição mista de **Hardware** e **Software**. 

O sistema utiliza uma interface de jogo interativa desenvolvida na linguagem **Processing**, integrada a um ecossistema físico controlado por um microcontrolador **Arduino UNO**, que lê comandos analógicos e digitais de controles personalizados.

<div align="center">
  <img src="https://user-images.githubusercontent.com/100162696/177075106-77e521ad-62d0-47f2-a0ed-95a49621b024.PNG" width="600"/>
</div>

## 🚀 Funcionalidades do Jogo
* **Tela Inicial Dinâmica:** Menu interativo para iniciar a partida ou acessar configurações.
* **Menu de Instruções:** Tela dedicada explicando o objetivo do jogo e os comandos dos periféricos.
* **Sistema de Pause Cooperativo:** O jogo pode ser pausado e retomado/reiniciado através da ação combinada dos botões de ambos os jogadores.
* **Tela de Fim de Jogo (Vencedor):** Detecção automática de pontuação máxima e declaração em tempo real do jogador vencedor (Lado Esquerdo vs. Lado Direito).

## 🛠️ Especificações Técnicas (Componentes)

### Hardware
* **1x Microcontrolador:** Arduino UNO R3 (responsável pela coleta de dados dos sensores).
* **2x Potenciômetros:** Utilizados como *joysticks* analógicos de precisão para movimentar as barras de forma unidimensional.
* **2x Botões (Push-buttons):** Para comandos de seleção nos menus e acionamento do modo de pause.
* **3x Resistores de 1KΩ:** Proteção do circuito (utilizado também o recurso interno de resistores de *Pull-Up* do Arduino).
* **2x Cases Plásticas Customizadas:** Controles ergonômicos do tipo *Paddle Game Controller* modelados e fabricados via **Impressão 3D**.
* Fios conectores e protoboard para prototipagem.

### Software e Ferramentas
* **Processing IDE:** Ambiente e linguagem (baseada em C/Java) utilizada no desenvolvimento da lógica do jogo e renderização gráfica orientada a objetos (classes para bola, barras e botões).
* **Arduino IDE:** Programação do firmware embarcado no microcontrolador.
* **TinkerCAD:** Plataforma online utilizada para simulação e validação prévia de todo o circuito eletrônico antes da montagem física.
* **Visual Studio Code & GitHub:** Ferramentas auxiliares de codificação e versionamento.

## 🔌 Protocolo de Comunicação Serial
Para transferir os estados dos controles físicos do Arduino para a interface gráfica no computador, foi estruturado um modelo de **Comunicação Serial** simplificado via cabo USB.

1.  O Arduino realiza a leitura analógica dos potenciômetros e digital dos botões (utilizando a propriedade `INPUT_PULLUP`).
2.  Os dados lidos são mapeados (`map()`) para uma escala de `0 a 255`.
3.  O microcontrolador concatena todos os estados em um único pacote de string estruturado no formato `[v_pot1-v_pot2-v_b01-v_b02\n]`.
4.  O código em **Processing** recebe essa string continuamente através da biblioteca Serial, realiza o *parsing* (separação dos caracteres delimitados por `-`) e atualiza instantaneamente as posições das barras e as ações de tela no jogo.

## 🎮 Como Executar o Projeto

1.  **Montagem do Hardware:** Monte o circuito conforme o esquema validado na [Simulação do TinkerCAD](https://www.tinkercad.com/things/4twfonFw2j7).
2.  **Upload do Firmware:** Abra o código do Arduino presente na pasta de firmware e faça o upload para a sua placa Arduino UNO.
3.  **Execução do Jogo:** Com o Arduino conectado ao computador via USB, abra o código principal no ambiente do **Processing**, certifique-se de selecionar a porta COM correspondente e clique em *Run*.

---
Desenvolvido como um projeto prático e aplicado de engenharia de computação e eletrônica.
