**ESP32 Smart Lamp Controller**
 Este projeto demonstra um sistema de controle de lâmpada inteligente utilizando um ESP32, MQTT e FIWARE. O ESP32 atua como um dispositivo IoT, controlando o estado de uma lâmpada LED conectada ao pino D4. O controle é realizado através de comandos MQTT publicados em um tópico específico.

-> Funcionalidades:
- Conexão Wi-Fi: O ESP32 se conecta a uma rede Wi-Fi configurada.
- Comunicação MQTT: O ESP32 se conecta a um broker MQTT e se inscreve em um tópico para receber comandos.
- Controle da lâmpada: O ESP32 controla o estado da lâmpada LED (ligada/desligada) com base nos comandos MQTT recebidos.
- Publicação de status: O ESP32 publica o estado atual da lâmpada em um tópico MQTT separado.

-> Hardware Necessário:
- Placa ESP32
- LED
- Resistor (150 ohms)
- Jumper wires

-> Software Necessário:
- Arduino IDE
- Bibliotecas:
    + WiFi.h
    + PubSubClient.h
- Python 3 (para scripts de controle)
- Biblioteca Paho MQTT para Python (pip install paho-mqtt)

-> Configuração:
- Configurações do ESP32:
    + Abra o código do ESP32 no Arduino IDE.
    + Modifique as seguintes variáveis no início do código com suas informações:
        >> SSID: Nome da sua rede Wi-Fi.
        >> PASSWORD: Senha da sua rede Wi-Fi.
        >> BROKER_MQTT: Endereço IP do seu broker MQTT.
        >> BROKER_PORT: Porta do seu broker MQTT.
        >> TOPICO_SUBSCRIBE: Tópico MQTT para receber comandos (ex: /TEF/device001/cmd).
        >> TOPICO_PUBLISH_1: Tópico MQTT para publicar o estado da lâmpada (ex: /TEF/device001/attrs).
        >> ID_MQTT: ID único para o dispositivo MQTT (ex: fiware_001).
        >> D4: Pino do ESP32 conectado ao LED (pino 2 por padrão).

- Scripts de controle Python:
    + Configure os scripts I.py e II.py com o endereço IP do seu broker MQTT (Broker) e a porta (PortaBroker).
    + O script I.py publica o comando device001@on| no tópico /TEF/device001/cmd, que liga a lâmpada.
    + O script II.py publica o comando device001@off| no tópico /TEF/device001/cmd, que desliga a lâmpada.

-> Utilização:
    1. Carregue o código do ESP32 na sua placa.
    2. Abra o monitor serial do Arduino IDE para acompanhar as mensagens de log do ESP32.
    3. Execute o script I.py para ligar a lâmpada.
    4. Execute o script II.py para desligar a lâmpada.

-> Integração com FIWARE:
  Este projeto pode ser facilmente integrado com a plataforma FIWARE para gerenciar e monitorar a lâmpada inteligente.
- Context Broker: Crie uma entidade na plataforma FIWARE para representar a lâmpada, com atributos como status (ligada/desligada) e luminosidade.
- IoT Agent: Utilize um IoT Agent para conectar o ESP32 ao Context Broker e enviar/receber dados.
- Wirecloud: Crie um dashboard no Wirecloud para visualizar o estado da lâmpada e controlá-la remotamente.

-> Próximos Passos: 
- Implementação de controle de luminosidade: utilize um sensor de luminosidade para ajustar o brilho da lâmpada automaticamente.
- Integração com assistentes de voz: permita o controle da lâmpada através de comandos de voz.
- Criação de cenários de automação: configure a lâmpada para ligar/desligar automaticamente em horários específicos ou com base em outros eventos.

-> Notas:
- O código do ESP32 inclui uma função InitOutput() que realiza um teste inicial da lâmpada LED, piscando-a por 10 vezes.
- A função VerificaConexoesWiFIEMQTT() garante que o ESP32 esteja conectado ao Wi-Fi e ao broker MQTT.
- A função EnviaEstadoOutputMQTT() publica o estado atual da lâmpada no tópico MQTT a cada segundo.
- Os scripts Python fornecidos são exemplos básicos de controle da lâmpada. Você pode criar seus próprios scripts para implementar funcionalidades mais complexas.
