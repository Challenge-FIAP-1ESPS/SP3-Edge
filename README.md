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
### Como Funciona?
1 - O Arduino Uno lê o cartão RFID.
2 - Envia o ID via serial para o ESP32.
3 - O ESP32 publica esse ID no Azure via MQTT.
4 - O Node-RED recebe e exibe os dados no Dashboard.

### Configuração do Wokwi
No Wokwi, simulamos: 
✅ Arduino Uno → Lê RFID e envia via serial.
✅ ESP32 → Conecta ao Wi-Fi e publica dados no Azure via MQTT.
✅ Broker MQTT (Azure IoT Hub) → Gerencia a comunicação.

## Especificações Técnicas
COMPLETAR DEPOIS (principais componentes, etc)

## Diagrama da arquitetura e fluxo do projeto
IMAGEM E FAZER UMA DESCRIÇÃO DETALHADA

## Funcionalidades Gerais
- **Comunicação Eficiente:** Canal centralizado entre médicos, pacientes e equipes.
- **Automatização de Processos:** Agendamento de consultas, registros médicos e controle de medicamentos.
- **Acesso Centralizado:** Interface para prontuários, relatórios e atualizações em tempo real.
- **Eficiência Operacional:** Redução de erros administrativos e otimização de tempo.
- **Gamificação:** Atividades interativas para crianças, tornando o ambiente mais acolhedor.

## Benefícios Gerais
- **Para Pacientes e Familiares:** Comunicação direta com médicos, acompanhamento de tratamentos e acesso a resultados.
- **Para Médicos e Equipes de Saúde:** Acesso rápido a informações clínicas, melhor coordenação e redução de tarefas manuais.
- **Para Funcionários de Apoio:** Organização de tarefas de limpeza e distribuição de medicamentos.
- **Para Gestores:** Relatórios para decisões rápidas e gestão de recursos otimizada.

## Estrutura Geral
- **Dashboards:** Para cada home existe um dashboard personalizado de acordo com as necessidades do tipo de cadastro.
- **Área de Login e Cadastro:** O paciente e os funcionários do hospital terão um login e senha para entrar no portal. Isso permite a segurança e personalização das informações armazenadas.
- **Automatização de Processos:** No portal, é possível fazer qualquer atividade do setor hospitalar que envolva a enfermaria, medicina, farmácia, limpeza, manutenção e administração. 
- **Chatbot:** Desenvolvimento de Chatbot para facilitar a comunicação entre as áreas.
