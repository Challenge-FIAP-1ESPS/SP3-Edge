# Sprint 3 - Edge

## Integrantes
- Davi Daparé RM: 560721
- Erick Cardoso RM: 560440
- Gabrielly Candido RM: 560916
- João Victor Ferreira RM: 560439
- Luiza Ribeiro RM: 560200

## Ideia do projeto geral - Portal Digital para o Hospital Sabará

O portal digital foi desenvolvido para integrar médicos, pacientes e equipes de apoio (limpeza, farmácia, manutenção e administração) do Hospital Sabará. A solução visa resolver problemas como falhas na comunicação, atrasos nos agendamentos, dificuldade no acesso a informações e ineficiência nos processos administrativos, trazendo uma maior organização e eficiência para o hospital.

## Estrutura do projeto de Arduino
### Como Funciona?/////REVISAR
1 - O Arduino Uno lê o cartão RFID e a distância (controle de estoque).
2 - Envia o ID e dados da distância via serial para o ESP32.??
3 - O ESP32 publica esse ID no Azure via MQTT.??
4 - O Node-RED recebe e exibe os dados no Dashboard.

### Configuração do Wokwi /////REVISAR
No Wokwi, simulamos: 
✅ Arduino Uno → Lê RFID e envia via serial.
✅ ESP32 → Conecta ao Wi-Fi e publica dados no Azure via MQTT.
✅ Broker MQTT (Azure IoT Hub) → Gerencia a comunicação.

## Especificações Técnicas
COMPLETAR DEPOIS (principais componentes, etc)
### Bibliotecas Utilizadas
- #include <Wire.h>
- #include <LiquidCrystal_I2C.h>

### Configurações e Definições
- LiquidCrystal_I2C lcd(0x27, 16, 2): Endereço padrão LCD e definição do display escolhido 16 colunas e 2 linhas (16x2).
- #define TRIG_PIN 13 & #define ECHO_PIN 12: Defiição dos pinos do Sensor Ultrassônico.

### Simulações
- Função simulateRFID(): Retorna um valor fixo "12345678", simulando um cartão RFID. //O objetivo é pegar o valor real lido
- Função simulateDistance(): Gera um número aleatório entre 5 cm e 100 cm, simulando a leitura do sensor ultrassônico. //Teria que calcular a distância com base nos sinais de Trigger e ECHO.

### Configuração Inicial no setup()
1- Inicialização do LCD
2- Configuração do Sensor Ultrassônico
3- Inicialização da comunicação com a Serial

### Configuração no loop()
1- Obtenção do ID e Distância
2- Exibição do ID e Distância
3- Envio de dados para a Serial
4- Delay

## Diagrama da arquitetura e fluxo do projeto
IMAGEM E FAZER UMA DESCRIÇÃO DETALHADA

## Links Externos
- Documentação do Projeto:
- Pitch:
- Elaboração Geral: 
