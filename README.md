# Sprint 3 - Edge

## Integrantes
- Davi Daparé RM: 560721
- Erick Cardoso RM: 560440
- Gabrielly Candido RM: 560916
- João Victor Ferreira RM: 560439
- Luiza Ribeiro RM: 560200

## Ideia do projeto geral - Portal Digital para o Hospital Sabará

O portal digital foi desenvolvido para integrar médicos, pacientes e equipes de apoio (limpeza, farmácia, manutenção e administração) do Hospital Sabará. A solução visa resolver problemas como falhas na comunicação, atrasos nos agendamentos, dificuldade no acesso a informações e ineficiência nos processos administrativos, trazendo uma maior organização e eficiência para o hospital.

## Ideia da aplicação com Arduino

Basicamente, o projeto visa criar um sistema de monitoramento de estoque, uma vez que é possível fazer a leitura de IDs de cartões e um sensor ultrassônico para medir a distância, que simula a quantidade de estoque disponível. As informações são exibidas em tempo real em um LCD 16x2 para visualização local e também são enviadas ao Serial Monitor para fins de diagnóstico e monitoramento. //mudar isso falando mqtt

## Benefícios
- Automação: Automatiza o processo de leitura de estoque e controle de inventário com RFID.
- Interatividade Local: O LCD proporciona uma interface visual imediata.
- Simplicidade e Custo-Benefício: Usa componentes acessíveis e fáceis de integrar, como o Arduino UNO, RFID e sensores ultrassônicos.

## Link Wowki
https://wokwi.com/projects/426419492478971905 

## Estrutura do projeto de Arduino
### Como Funciona?
1. O ESP32 lê o ID do cartão RFID e a distância do sensor ultrassônico. //ainda nao usado rfid
2. Os dados coletados são enviados via serial para o ESP32.
3. O ESP32 conecta-se ao Wi-Fi e publica esses dados no Azure IoT Hub via MQTT.
4. O Node-RED recebe e exibe os dados no Dashboard (ainda não testado completamente).

### Configuração do Wokwi /////REVISAR
No Wokwi, simulamos: 
- ESP32: Lê RFID e envia os dados via serial.
- Broker MQTT (Azure IoT Hub): Responsável pela comunicação dos dados (atualmente não funcional).

## Especificações Técnicas
COMPLETAR DEPOIS (principais componentes, etc)
### Bibliotecas Utilizadas
- #include <Wire.h>
- #include <LiquidCrystal_I2C.h>

### Componentes Utilizados
- ESP32: Controlador principal responsável pela leitura dos sensores, controle do LCD e comunicação Wi-Fi.
- Sensor RFID MFRC522: Utilizado para ler o ID de um cartão RFID, simulando a identificação de um produto no estoque. //ainda nao usado
- Sensor Ultrassônico HC-SR04: Usado para medir a distância entre o sensor e um objeto, com o intuito de simular a quantidade de estoque restante.
- LCD 16x2 I2C: Display utilizado para mostrar informações ao usuário: ID do cartão e a distância medida pelo sensor ultrassônico.
- Cabos e Protoboard: Para realizar as conexões físicas entre os componentes.

### Configurações e Definições
- LiquidCrystal_I2C lcd(0x27, 16, 2): Endereço padrão LCD e definição do display escolhido 16 colunas e 2 linhas (16x2).
- #define TRIG_PIN 13 & #define ECHO_PIN 12: Defiição dos pinos do Sensor Ultrassônico.

### Funções principais
- simulateRFID(): Retorna um valor fixo "12345678", simulando um cartão RFID. //O objetivo é pegar o valor real lido
- readDistance(): Retorna a distância real baseada nos sinais de TRIGGER e ECHO

### Configuração Inicial setup()
1. Inicialização do LCD
2. Configuração do Sensor Ultrassônico
3. Inicialização da comunicação com a Serial

### Configuração no loop()
1. Obtenção do ID e Distância
2. Exibição do ID e Distância
3. Envio de dados para a Serial
4. Delay

## Diagrama da arquitetura e fluxo do projeto
![SP3-Challenge2025 drawio](https://github.com/user-attachments/assets/54395624-ed06-41a0-80ca-dee0e70a1d4c)

### Explicação do Fluxograma

- Início: O sistema é iniciado.
- Importar Bibliotecas: As bibliotecas necessárias são carregadas.
- Configurar LCD: O display LCD é inicializado.
- Exibir Dados no LCD: O ID RFID e a distância são mostrados na tela.
- Nova leitura de estoque?: O sistema verifica se deve continuar a leitura.
  - Se "Sim": O fluxo retorna à exibição dos dados.
  - Se "Não": O sistema finaliza a execução.

## Links Externos
- Documentação do Projeto:
- Pitch:
- Elaboração Geral: 
