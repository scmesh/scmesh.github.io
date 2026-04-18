# Glossário

Um apanhado rápido dos termos técnicos mais usados na rede SC Mesh e na comunidade Meshtastic. Serve para leigos, radioamadores e curiosos sem vocabulário comum de RF.

## A

**Anatel** — Agência Nacional de Telecomunicações. Regula o uso do espectro de rádio no Brasil. A faixa de 902–907,5 MHz e 915–928 MHz é ISM e permite o uso do Meshtastic sem licença, respeitando os limites de potência.

**AES256** — Algoritmo de criptografia simétrica usado pelo Meshtastic para cifrar o payload dos canais. Sem a chave (PSK), ninguém lê a mensagem.

**ANZ** — Código regional do Meshtastic para Austrália/Nova Zelândia, compatível com a faixa de 915 MHz permitida no Brasil. É a região configurada na SC Mesh.

## B

**Backbone** — Conjunto de repetidoras fixas em pontos altos que carregam o tráfego de longa distância da rede. São os "troncos" que fazem a malha alcançar várias cidades.

**Bandwidth** — Largura de banda do sinal LoRa. Quanto maior, mais rápido; quanto menor, mais sensível e longínquo.

## C

**Canal** — Conjunto lógico de nomes + PSK + parâmetros de modulação. Dois rádios só conversam se estiverem no mesmo canal.

**CLIENT** — Tipo de nó configurado para uso pessoal. Participa da malha, envia suas mensagens, mas dorme sempre que pode para economizar bateria.

**CLIENT_MUTE** — Como CLIENT, mas **não retransmite** pacotes de terceiros. Útil para não saturar áreas onde já existem muitos nós.

## F

**Flooding Mesh** — Estratégia de roteamento do Meshtastic. Cada nó que ouve um pacote retransmite (até o limite de hops), garantindo propagação sem necessidade de tabela de rotas.

**Fresnel (Zona de)** — Volume elipsoidal entre duas antenas. Obstáculos dentro dessa zona (mesmo sem cortar a visada direta) reduzem o sinal. Por isso antenas altas têm tanta diferença.

## G

**Gateway** — Nó que, além de rádio, tem conexão à internet e pode publicar mensagens via MQTT. **A SC Mesh desencoraja o uso de gateways MQTT** para preservar a natureza off-grid da rede.

## H

**Hop / Hop Limit** — Quantas retransmissões um pacote pode sofrer antes de ser descartado. Padrão: 3. Aumentar sem critério congestiona a rede.

## I

**ISM** — *Industrial, Scientific, Medical*. Faixas de espectro de uso livre (sem licença individual) em muitos países. O LoRa do Meshtastic opera em ISM.

## L

**LoRa** — *Long Range*. Modulação de espalhamento espectral (chirp) que permite comunicação de longo alcance a baixa potência. Base física do Meshtastic.

**LongFast** — Preset do Meshtastic que equilibra alcance e velocidade. É o padrão da SC Mesh.

**LongSlow** — Preset mais lento mas de maior alcance. Usado em enlaces muito longos entre morros.

## M

**Meshtastic** — Firmware + protocolo open-source que transforma módulos LoRa de baixo custo em uma rede de mensagens mesh.

**MQTT** — Protocolo de mensagens sobre TCP/IP. Pode ser usado pelo Meshtastic para espelhar mensagens na internet. A SC Mesh pede para **não habilitar**.

## N

**Nó (Node)** — Qualquer dispositivo Meshtastic na rede: seu rádio pessoal, uma repetidora solar, um gateway.

## P

**Preset** — Combinação pré-definida de parâmetros de modulação (bandwidth, spreading factor, coding rate). Ex.: `LongFast`, `MediumFast`.

**PSK** — *Pre-Shared Key*. Chave simétrica compartilhada que define quem consegue decifrar as mensagens de um canal.

## R

**RAK WisBlock** — Plataforma modular da RAKwireless. Muito usada para repetidoras solares por seu consumo extremamente baixo.

**RSSI** — *Received Signal Strength Indicator*. Intensidade do sinal recebido em dBm. Quanto mais próximo de zero, melhor (ex.: -60 dBm é ótimo, -120 dBm é no limite).

**ROUTER** — Tipo de nó fixo, em local alto, cuja função principal é retransmitir pacotes alheios. Não dorme.

**ROUTER_CLIENT** — Híbrido: retransmite e também é usado como cliente pessoal. Evite em repetidoras dedicadas.

## S

**SNR** — *Signal-to-Noise Ratio*. Relação entre sinal e ruído em dB. LoRa decodifica até valores negativos (ex.: -15 dB). Mais importante que o RSSI.

**Spreading Factor (SF)** — Parâmetro que define quantos chips por símbolo o LoRa usa. SF maior = mais alcance e mais lentidão.

## T

**Telemetria** — Pacotes automáticos com bateria, temperatura, pressão, posição etc. Útil, mas consome ar. Mantenha intervalos ≥ 1 hora em canais públicos.

## V

**Visada (LoS — Line of Sight)** — Reta geométrica entre duas antenas sem obstáculos. LoRa funciona sem visada em curta distância, mas só brilha de verdade com visada limpa.

---

Sentiu falta de algum termo? Abra uma *issue* ou PR no [repositório](https://github.com/scmesh/scmesh.github.io) e vamos complementando.
