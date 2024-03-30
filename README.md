RMs: 556319; 557571 Nomes: Felipe Marques de Oliveira; Felipe Men dos Santos

Projeto:
Este projeto será utilizado para medir a intensidade da luz de um armazem de uma vinícola, já que os vinhos precisar ter uma certa quantidade suva de luz para que não comecem a ter reações químicas indesejadas.

Desafios encontrados:
Primeiramente estavamos com dificuldade de escrever as condições dos LEDs para que ligassem apenas quando desejados, porém após algumas pesquisas e vídeos conseguimos consertar as condições e o codígo estava funcionando do jeito que queriamos
Depois de consertar o código encontramos alguns problemas com resistores de potencia errada e fios nas posições erradas, mas após revisar os componentes encontrados os problemas e resolvemos com facilidade.

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
Nome	Quantidade	Componente
U1	      1	      Arduino Uno R3
R1	      1	      1 kΩ Resistor
R2	      1	      Fotorresistor
D1	      1	      Vermelho LED
D2	      1	      Amarelo LED
D3	      1	      Verde LED
R3
R4
R5
R6	      4	      220 kΩ Resistor
PIEZO2	  1      	Piezo


Código Utilizado:
int ValorLDR;        // Variável para armazenar o valor lido pelo sensor LDR
int IntensidadeLuz;  // Variável para armazenar a intensidade da luz calculada
int pinoLDR = A0;    // Pino analógico ao qual o sensor LDR está conectado
int ledVerde = 9;    // Pino digital ao qual o LED verde está conectado
int ledVerm = 11;    // Pino digital ao qual o LED vermelho está conectado
int ledAma = 10;     // Pino digital ao qual o LED amarelo está conectado
int buzina = 3;      // Pino digital ao qual a buzina está conectada

void setup(){
  Serial.begin(9600);        // Inicializa a comunicação serial com uma taxa de 9600 bps
  pinMode(pinoLDR, INPUT);    // Configura o pino do sensor LDR como entrada
  pinMode(ledVerm, OUTPUT);   // Configura o pino do LED vermelho como saída
  pinMode(ledAma, OUTPUT);    // Configura o pino do LED amarelo como saída
  pinMode(ledVerde, OUTPUT);  // Configura o pino do LED verde como saída
  pinMode(buzina, OUTPUT);    // Configura o pino da buzina como saída
}

void loop(){
  ValorLDR = analogRead(pinoLDR);                // Lê o valor do sensor LDR
  IntensidadeLuz = map(ValorLDR, 0, 1023, 0, 101); // Mapeia o valor lido para o intervalo de 0 a 100
  Serial.print("Intensidade de Luz = ");         // Imprime um texto indicando a intensidade da luz
  Serial.println(IntensidadeLuz);                // Imprime a intensidade da luz
  delay(300);                                     // Aguarda 300 milissegundos

  if(IntensidadeLuz <= 33){  // Se a intensidade da luz for menor ou igual a 33:
    digitalWrite(ledVerm, HIGH);  // Acende o LED vermelho
    digitalWrite(ledVerde, LOW);   // Apaga o LED verde
    digitalWrite(ledAma, LOW);     // Apaga o LED amarelo
    tone(buzina, 1000);            // Ativa a buzina com tom de 1000 Hz
    delay(1000);                   // Aguarda 1 segundo
    noTone(buzina);                // Desativa a buzina
    delay(1000);                   // Aguarda 1 segundo
  }
  else if(IntensidadeLuz < 66){   // Se a intensidade da luz for menor que 66:
    digitalWrite(ledAma, HIGH);   // Acende o LED amarelo
    digitalWrite(ledVerde, LOW);  // Apaga o LED verde
    digitalWrite(ledVerm, LOW);   // Apaga o LED vermelho
    tone(buzina, 450);             // Ativa a buzina com tom de 450 Hz
    delay(1000);                   // Aguarda 1 segundo
    noTone(buzina);                // Desativa a buzina
    delay(1000);                   // Aguarda 1 segundo
  }
  else if(IntensidadeLuz <= 100){ // Se a intensidade da luz estiver entre 66 e 100:
    digitalWrite(ledVerde, HIGH); // Acende o LED verde
    digitalWrite(ledVerm, LOW);   // Apaga o LED vermelho
    digitalWrite(ledAma, LOW);    // Apaga o LED amarelo
  }
}
![image](https://github.com/FelipeMen10/CP1-Edge-Computing/assets/153327403/fc91e7d9-5c2e-4247-9d51-d1bc4b1e77df)
