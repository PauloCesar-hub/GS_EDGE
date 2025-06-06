# 🌊 Projeto: Sistema Físico de Monitoramento de Enchentes com Arduino (Edge Computing & IoT)

## 🆘 Problema Identificado
Enchentes são um problema recorrente em muitas cidades brasileiras, especialmente em áreas de risco onde o escoamento pluvial é precário. A falta de sistemas de alerta locais pode agravar a situação, resultando em perdas materiais e, em casos mais graves, vítimas fatais.

##🎯 Solução Proposta
Este projeto propõe um sistema físico de monitoramento de enchentes usando sensores conectados a um Arduino Uno, com capacidade de detectar:

Temperatura e umidade relativa do ar (indicadores meteorológicos)

Nível de água (simulado por potenciômetro)

Intensidade de chuva (simulado por outro potenciômetro)

O sistema emite alertas locais com LEDs e buzzer, além de mostrar os dados em tempo real em um display LCD.

## 🧰 Componentes Utilizados
Componente	Função
Arduino Uno	Unidade de controle central
Sensor DHT22	Leitura de temperatura e umidade
2x Potenciômetros	Simulação do nível de água e da chuva
Display LCD 16x2 I2C	Exibição das informações
LEDs (Verde, Amarelo, Vermelho)	Indicação visual do nível de água
Buzzer	Alarme sonoro em caso de alerta

## 🖥️ Simulação no Wokwi
Este projeto pode ser simulado gratuitamente na plataforma Wokwi. Para isso:

Importe o arquivo diagram.json:

Baixe o arquivo diagram_dht22_ok.json

Vá em https://wokwi.com, clique em "Import Project" e selecione o arquivo

Cole o código a seguir no sketch.ino:

cpp
Copiar
Editar
#include <DHT.h>
#include <LiquidCrystal_I2C.h>

#define DHTPIN 6
#define DHTTYPE DHT22

DHT dht(DHTPIN, DHTTYPE);
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  Serial.begin(9600);
  dht.begin();
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("Monitorando...");
  delay(2000);
}

void loop() {
  float temp = dht.readTemperature();
  float hum = dht.readHumidity();

  lcd.clear();
  if (isnan(temp) || isnan(hum)) {
    lcd.setCursor(0, 0);
    lcd.print("Erro no sensor");
  } else {
    lcd.setCursor(0, 0);
    lcd.print("Temp: ");
    lcd.print(temp);
    lcd.print(" C");

    lcd.setCursor(0, 1);
    lcd.print("Umid: ");
    lcd.print(hum);
    lcd.print(" %");
  }

  delay(2000);
}
- 🔗 Link do Video Explicativo do Projeto no Youtube(https://youtube.com/shorts/RG7EyCWfr2E)
-🔗 Link do Projeto no wokwi(https://wokwi.com/projects/429233134750736385)
![tecnologias](https://github.com/user-attachments/assets/78bdeea2-498c-4956-a869-2dd01958c464)


## ✅ Avaliação Funcional
Este projeto foi testado e validado no simulador Wokwi, com todas as funcionalidades operando corretamente:

Leitura e exibição de temperatura e umidade

Funcionamento do display LCD

Sensor DHT22 inicializado corretamente

---

## 👨‍💻 Integrantes

- Paulo Cesar de Govea Junior - (RM:566034)
- Guilherme Vilela Perez - (RM:564422)
- Gustavo Panham Dourado - (RM:563904)
