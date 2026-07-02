# SMD O Que?

**SMD O Que?** e um jogo/instalacao interativa feito em Godot 4.6 para apresentar o curso de Sistemas e Midias Digitais da UFC de forma mais participativa.

O projeto nasceu da ideia de explicar o SMD sem depender apenas de banners, textos ou apresentacoes lineares. Em vez disso, o visitante usa uma mira para descobrir, jogando, as areas que formam o curso.

## Objetivo

O jogo apresenta Sistemas e Midias Digitais como uma formacao interdisciplinar que mistura:

- Sistemas Multimidia
- Design Digital Interativo
- Animacao e Audiovisual
- Jogos Digitais

Cada trilha aparece como uma descoberta dentro do jogo, com exemplos visuais e pequenas explicacoes. A proposta e fazer o visitante entender rapidamente que SMD envolve programacao, design, audiovisual, jogos, interacao e producao de experiencias digitais.

## Como é o jogo

A experiencia e inspirada em jogos arcade como Duck Hunt:

- o jogador move uma mira;
- acerta alvos na tela;
- descobre as trilhas do curso;
- responde um desafio de memoria/projeto;
- ve uma tela final mostrando as trilhas se misturando para formar o SMD.

Tambem existem interacoes extras, como patos, bonus, filtro de TV antiga e um modo secreto/standby.

## Controles

O projeto aceita mais de uma forma de controle:

- Teclado: setas movem a mira e espaco atira/confirma.
- Arduino: entrada serial para joystick analogico e botao fisico.
- Webcam: a palma da mao controla a mira e o gesto de apertar/fechar a mao dispara.

No controle por webcam, o script Python detecta a mao e envia os dados para o Godot por UDP.

## Tecnologias e linguagens

O projeto usa:

- Godot 4.6
- GDScript
- Python
- OpenCV
- MediaPipe
- UDP para comunicacao entre Python e Godot
- PowerShell para ponte serial do Arduino

Principais partes:

- `scripts/`: logica do jogo em GDScript.
- `scenes/`: cenas do Godot.
- `python/webcam_controller.py`: controle por webcam.
- `tools/arduino_serial_bridge.ps1`: ponte serial para Arduino.
- `sprites/`: artes usadas no prototipo.
- `sounds/`: efeitos sonoros.

## Webcam

Para usar a webcam, instale as dependencias uma vez no computador:

```powershell
py -m pip install opencv-python mediapipe
```

Depois, ao abrir o jogo, o Godot tenta iniciar automaticamente o script da webcam.

Configuracoes importantes ficam em `project.godot`:

```ini
[webcam]
enabled=true
auto_start_python=true
python_executable="py"
show_preview=true
embed_preview=false
camera_index=0
udp_port=4242
```

Se a camera errada abrir, altere:

```ini
camera_index=1
```

ou outro numero.

## Exportacao

O preset de exportacao do Windows gera o executavel em:

```text
exports/SMD_O_Que.exe
```

Observacao importante: a exportacao inclui o script Python e o modelo de mao do MediaPipe, mas o computador que for rodar a instalacao ainda precisa ter Python e as bibliotecas `opencv-python` e `mediapipe` instaladas para o controle por webcam funcionar.

O jogo continua funcionando com teclado mesmo sem webcam.

## Creditos

Disciplina: Instalacoes Multimidia  
Professor: Clemilson Costa dos Santos  
Carlos Renan  
Davi Lisboa  
Gabriel Silva
