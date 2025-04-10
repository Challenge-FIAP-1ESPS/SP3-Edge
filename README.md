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

Basicamente, o projeto visa criar um sistema de monitoramento de estoque, uma vez que é possível fazer a leitura de IDs de cartões dos funcionários responsáveis pela entrada e retirada de medicamentos, e um sensor ultrassônico para medir a distância, que simula a quantidade de estoque disponível. Em termos de simulação, as informações são exibidas em tempo real em um LCD 16x2 para visualização local e também são enviadas ao Serial Monitor para fins de diagnóstico e monitoramento. Contudo, trazendo para a aplicação real, será conectado ao dashboard NODE-RED para o controle visual do estoque. 

## Benefícios
- Automação: Automatiza o processo de leitura de estoque e controle de inventário com RFID.
- Interatividade Local: O LCD proporciona uma interface visual imediata.
- Simplicidade e Custo-Benefício: Usa componentes acessíveis e fáceis de integrar, como o Arduino UNO, RFID e sensores ultrassônicos.

## Link Wowki
https://wokwi.com/projects/426442063798337537 

## Estrutura do projeto de Arduino -  Especificações Técnicas
### Como Funciona?
1. O ESP32 lê o ID do cartão RFID (hipoteticamente) e a distância do sensor ultrassônico. 
2. Os dados coletados são enviados via serial para o ESP32.
3. O ESP32 conecta-se ao Wi-Fi e publica esses dados no Azure IoT Hub via MQTT. //perguntar para o professor
4. O Node-RED recebe e exibe os dados no Dashboard.

### Configuração do Wokwi 
No Wokwi, simulamos: 
- ESP32: Lê RFID (hipoteticamente) e envia os dados via serial.
- Broker MQTT (Azure IoT Hub): Responsável pela comunicação dos dados (atualmente não funcional). //perguntar para o professor

### Bibliotecas Utilizadas
- #include <Wire.h>
- #include <LiquidCrystal_I2C.h>

### Componentes Utilizados
- ESP32: Controlador principal responsável pela leitura dos sensores, controle do LCD e comunicação Wi-Fi.
- Sensor RFID MFRC522: Utilizado para ler o ID de um cartão RFID, simulando a identificação de um produto no estoque. /AINDA NAO USADO
- Sensor Ultrassônico HC-SR04: Usado para medir a distância entre o sensor e um objeto, com o intuito de simular a quantidade de estoque restante.
- LCD 16x2 I2C: Display utilizado para mostrar informações ao usuário: ID do cartão e a distância medida pelo sensor ultrassônico.
- Cabos e Protoboard: Para realizar as conexões físicas entre os componentes.

### Configurações e Definições
- LiquidCrystal_I2C lcd(0x27, 16, 2): Endereço padrão LCD e definição do display escolhido 16 colunas e 2 linhas (16x2).
- #define TRIG_PIN 13 & #define ECHO_PIN 12: Definição dos pinos do Sensor Ultrassônico.

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
![image](https://github.com/user-attachments/assets/afbaec04-1fa4-4411-863b-f9a03cb86258)

### Explicação do Fluxograma

- Início: O sistema é iniciado.
- Importar Bibliotecas: As bibliotecas necessárias são carregadas.
- Conectar no Wi-Fi: Ao utilizar a rede de Wi-Fi do Wowki, ele conecta automaticamente.
- Conectar no MQTT: Existe um broker (servidor), o "tópico" que é publicado pelos dispositivos e uma porta (1883). Tudo isso é gratuito e não é considerado muito seguro. Por isso, na próxima SPRINT será um processo mais refinado e personalizado.
- Configurar LCD: O display LCD é inicializado.
- Exibir Dados no LCD: O ID RFID e a distância são mostrados na tela.
- Nova leitura de estoque?: O sistema verifica se deve continuar a leitura.
  - Se "Sim": O fluxo retorna à exibição dos dados.
  - Se "Não": O sistema finaliza a execução.

## Links Externos
- Documentação do Projeto:
- Pitch:
- Elaboração Geral: 
