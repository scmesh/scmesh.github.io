# Documentação Técnica

### 🧠 Como o Protocolo Funciona
O Meshtastic utiliza uma técnica chamada *Flooding Mesh*. Quando um pacote é enviado, todos os nós que o ouvem o retransmitem (até um limite de saltos), garantindo que a mensagem chegue o mais longe possível.

### 🌐 MQTT e Gateways
Priorizamos a utilização somente do LoRa, sem conexão com a internet. Por favor, não ative o MQTT.

### ❓ FAQ
**P: Qual o alcance real?**
R: De 500m em cidades densas até 100km+ com visada direta entre morros.

**P: É legalizado?**
R: Sim, operamos em frequências ISM (915MHz) que não exigem licença de rádio, desde que respeitados os limites de potência da Anatel.