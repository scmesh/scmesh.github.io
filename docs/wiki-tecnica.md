# Documentação Técnica

Conteúdo mais denso sobre como a rede funciona por baixo do capô. Para perguntas rápidas, veja o [FAQ](faq.md).

## 🧠 Protocolo Meshtastic

O Meshtastic é um firmware open-source que roda sobre módulos LoRa e implementa uma rede mesh **flood-routing** otimizada para baixa largura de banda.

### Pacote

- **Payload máximo:** ~237 bytes por pacote.
- **Header:** IDs de origem/destino (4 bytes cada), channel hash, flags, hop limit.
- **Encriptação:** AES256-CTR aplicada ao payload quando há PSK no canal.

### Roteamento

- **Managed flood:** cada nó que recebe o pacote aguarda um backoff aleatório proporcional ao SNR da recepção e então retransmite — nós com sinal ruim esperam mais, dando chance ao melhor repetidor entrar primeiro. Se o nó ouve outro retransmitindo o mesmo pacote antes do seu turno, ele **desiste**, evitando duplicação.
- **Hop limit:** padrão 3. Cada retransmissão decrementa; em 0 o pacote morre.
- **Want ack:** quando habilitado, o destinatário confirma recebimento com ACK. Útil para DMs, péssimo para broadcasts grandes.

Mais detalhes no [repositório oficial do firmware](https://github.com/meshtastic/firmware).

## 📶 Radio e modulação LoRa

LoRa é uma modulação *chirp spread spectrum* patenteada pela Semtech. Parâmetros principais:

- **Bandwidth (BW):** largura do chirp (125/250/500 kHz). Maior BW = maior taxa, menor sensibilidade.
- **Spreading Factor (SF):** quantidade de *chips* por símbolo (SF7 a SF12). Maior SF = maior alcance, menor taxa.
- **Coding Rate (CR):** FEC (4/5 até 4/8). Mais robusto, mais lento.

### Presets Meshtastic

| Preset | BW | SF | Taxa aprox. | Alcance típico |
| :--- | :--- | :--- | ---: | :--- |
| `ShortFast` | 250 kHz | SF7 | 6,8 kbps | < 10 km |
| `ShortSlow` | 250 kHz | SF8 | 3,9 kbps | ~15 km |
| `MediumFast` | 250 kHz | SF9 | 2,1 kbps | ~20 km |
| `MediumSlow` | 250 kHz | SF10 | 1,2 kbps | ~25 km |
| **`LongFast` (padrão SC)** | 250 kHz | SF11 | ~670 bps | ~30 km |
| `LongSlow` | 125 kHz | SF11 | ~290 bps | ~40 km |
| `VLongSlow` | 125 kHz | SF12 | ~180 bps | 50+ km (visada) |

> Todos os nós da rede **precisam** usar o mesmo preset. Mudou o preset, saiu da malha.

## 📜 Regulamentação Anatel

No Brasil o Meshtastic opera nas faixas ISM de **902–907,5 MHz** e **915–928 MHz**. São faixas secundárias, de uso livre, desde que respeitados os limites de radiação.

**Resolução aplicável:** Resolução Anatel 680/2017 (radiação restrita) e atualizações.

### Limites principais

- **Potência EIRP máxima:** +30 dBm (1 W).
- **Duty cycle:** não há duty cycle fixo como na Europa; a responsabilidade é de "não causar interferência".
- **Não é necessária licença** individual para operar em potência dentro do limite.
- **Não confundir com radioamadorismo:** radioamadores (licenciados) operam em faixas separadas com regras próprias. A SC Mesh em 915 MHz ISM não exige licença nem indicativo.

!!! warning "Cuidado ao amplificar"
    Existem amplificadores LoRa no mercado que ultrapassam +30 dBm. Usá-los te coloca em infração Anatel e pode saturar a malha toda. Não faça.

Cheque sempre atualizações diretamente em [anatel.gov.br](https://www.anatel.gov.br/).

## 🔐 Criptografia

O Meshtastic cifra o **payload** de cada pacote em canais que tenham PSK (Pre-Shared Key). Apenas quem tem a chave consegue decifrar. O que **não** é cifrado:

- IDs dos nós de origem e destino (permite análise de tráfego).
- Timestamps e contadores.
- Canal hash (quem sabe a PSK consegue identificar o canal).
- Telemetria/posição em canais sem PSK.

### Canal público vs. privado

| Tipo | PSK | Quem lê |
| :--- | :--- | :--- |
| Canal público `LongFast` padrão | PSK conhecida (0x01) | Qualquer dispositivo Meshtastic |
| Canal com PSK customizada | Sua PSK | Só quem tem a chave |
| DM (mensagem direta) | Chave derivada do par origem-destino | Origem + destino |

**Regra:** trate `LongFast` como rádio aberto. Converse em canal privado com PSK se quiser privacidade.

Para ameaças específicas e recomendações, veja [Segurança e Privacidade](seguranca-privacidade.md).

## ⏱️ Airtime e duty cycle

*Airtime* é quanto tempo um pacote ocupa o ar. Em `LongFast`, uma mensagem curta pode levar **1–2 segundos**. Um pacote grande em `LongSlow` pode passar de 4 segundos. Três coisas decorrem daí:

1. **Duty cycle prático:** embora a Anatel não imponha limite rígido, a rede satura se todos ficarem transmitindo. Mantenha-se abaixo de **10 % de air utilization** visto no app.
2. **Telemetria é cara.** Um pacote de telemetria a cada 15 min de 50 nós consome mais ar do que todas as conversas humanas somadas. Por isso: intervalo ≥ 1 h em canais públicos.
3. **Hop limit multiplica.** Um pacote com hop 3 em rede densa gera até 3 retransmissões por nó — cada uma come ar. Use hop 3 como padrão; só suba se souber o que está fazendo.

Calculadora útil: [Semtech LoRa Calculator](https://www.semtech.com/design-support/lora-calculator) para estimar airtime antes de ajustar parâmetros.

## 🌐 MQTT e Gateways

A SC Mesh prioriza comunicação **somente via rádio**. Por favor, **não ative o MQTT** no seu nó.

Justificativas:

- **Privacidade:** mensagens pulam para a internet e para servidores externos.
- **Cultura off-grid:** o valor da rede é funcionar sem infra centralizada. MQTT volta a depender dela.
- **Ruído:** gateways MQTT costumam "poluir" a malha com nós virtuais de outros continentes.

Se precisar de MQTT para fins específicos (ex.: dashboard interno de uma empresa), use um canal próprio com PSK dedicada, desvinculado de `LongFast`.
