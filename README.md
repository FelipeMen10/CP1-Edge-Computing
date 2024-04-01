RMs: 556319; 557571 Nomes: Felipe Marques de Oliveira; Felipe Men dos Santos

Projeto:
Este projeto será utilizado para medir a intensidade da luz de um armazem de uma vinícola, já que os vinhos precisar ter uma certa quantidade suva de luz para que não comecem a ter reações químicas indesejadas.

Como replicar o projeto:
Conectar o Sensor LDR (Light Dependent Resistor):

Conecte uma perna do LDR ao pino analógico A0 do Arduino.
Conecte a outra perna do LDR ao GND (terra) do Arduino.
O LDR é um componente passivo, então não há polaridade correta para conectá-lo.
Conectar os LEDs:

Conecte o LED verde ao pino digital 9 do Arduino.
Conecte o LED vermelho ao pino digital 11 do Arduino.
Conecte o LED amarelo ao pino digital 10 do Arduino.
Conecte o terminal positivo (anodo) de cada LED a um resistor limitador de corrente (normalmente entre 220Ω e 1kΩ) e, em seguida, conecte o outro terminal do resistor ao pino do Arduino. O terminal negativo (catodo) do LED deve ser conectado ao GND (terra) do Arduino.
Conectar a Buzina:

Conecte a buzina ao pino digital 3 do Arduino.
A buzina pode ter polaridade, portanto, verifique o datasheet ou observe as marcas de polaridade para conectá-la corretamente. O terminal positivo da buzina deve ser conectado ao pino digital 3 do Arduino e o terminal negativo à terra (GND) do Arduino.
Conectar a Alimentação:

Conecte o pino 5V do Arduino à linha de alimentação positiva dos LEDs e da buzina, por meio de um resistor adequado para limitar a corrente (se necessário).
Conecte o pino GND (terra) do Arduino à linha de alimentação negativa dos LEDs, da buzina e ao terminal do sensor LDR.

Componentes Utilizados:
![image](https://github.com/FelipeMen10/CP1-Edge-Computing/assets/153327403/19006f8d-55b2-457d-a2a3-7b97bf655fbb)

Imagem simulada do projeto:
![image](https://github.com/FelipeMen10/CP1-Edge-Computing/assets/153327403/fc91e7d9-5c2e-4247-9d51-d1bc4b1e77df)
