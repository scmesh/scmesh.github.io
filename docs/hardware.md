# Guia de Hardware

Escolher bem o hardware é o que separa uma experiência frustrante de uma rede que funciona. Abaixo está o que a comunidade SC Mesh recomenda e por quê.

## 📻 Comparativo de rádios

| Dispositivo | MCU | Rádio | GPS | Display | Uso recomendado |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [Heltec LoRa32 V3](https://heltec.org/project/wifi-lora-32-v3/) | ESP32-S3 | SX1262 | Não | OLED 0.96″ | Nó fixo com tomada, primeiro rádio |
| [RAK WisBlock RAK4631](https://www.rakwireless.com/en-us/products/wisblock) | nRF52840 | SX1262 | Módulo | Módulo | Repetidora solar, nó externo |
| [LILYGO T-Beam S3](https://lilygo.cc/products/t-beam-s3-core) | ESP32-S3 | SX1262 | Sim (L76K) | Opcional | Uso móvel, trilha, mochila |
| [B&Q Station G2](https://muzi.works/products/station-g2) | ESP32-S3 | SX1262 | Opcional | Não | Nó fixo externo de longo prazo |
| [LILYGO T-Deck Plus](https://lilygo.cc/products/t-deck-plus) | ESP32-S3 | SX1262 | Sim | Sim + teclado | Uso em campo sem celular |
| [Heltec Mesh Node T114](https://heltec.org/project/mesh-node-t114/) | nRF52840 | SX1262 | Opcional | OLED | Nó solar compacto |

> Compre sempre a versão **915 MHz / US 915 / AU 915**. A versão europeia (868 MHz) **não** funciona aqui.

**Lista oficial completa:** [meshtastic.org/docs/hardware/devices](https://meshtastic.org/docs/hardware/devices/).

### Qual plataforma escolher

| Se você quer... | Vá de... |
| :--- | :--- |
| Começar barato com tomada próxima | ESP32 (Heltec V3) |
| Rodar a bateria dias/semanas | nRF52 (RAK4631, T114) |
| Carregar junto o rádio com GPS | ESP32 com GPS (T-Beam S3) |
| Montar nó externo robusto | nRF52 + case IP66 + antena externa |

!!! tip "Regra prática"
    **nRF52 para solar, ESP32 para tomada.** Em média, um nó nRF52 consome cerca de 10× menos que um ESP32 equivalente.

## 🔋 Consumo de energia real

Números observados pela comunidade Meshtastic (firmware 2.5+). Use como referência, **meça o seu**.

| Dispositivo | TX (pico) | RX ativo | Idle (sem sleep) | Deep sleep | Autonomia típica com 2.500 mAh |
| :--- | ---: | ---: | ---: | ---: | ---: |
| Heltec V3 (ESP32-S3) | ~130 mA | ~80 mA | ~60 mA | ~13 µA (power_saving) | ~19 h uso normal |
| RAK4631 (nRF52840) | ~110 mA | ~15 mA | ~8 mA | **~2 µA** | Vários dias / semanas |
| T-Beam S3 com GPS ativo | ~150 mA | ~120 mA | ~100 mA | ~80 µA | ~16 h contínuo |
| T-Deck | ~160 mA | ~100 mA | ~80 mA | ~200 µA | Horas (bateria pequena) |

**Observações importantes:**

- O [guia oficial de medição de consumo](https://meshtastic.org/docs/hardware/solar-powered/measure-power-consumption/) mostra como validar no seu dispositivo.
- O Heltec T114 ainda tem [um problema conhecido](https://github.com/meshtastic/firmware/discussions/9026) em que o deep sleep estaciona em ~8 mA em vez dos ~11 µA esperados. Verifique o firmware antes de usá-lo em solar.
- GPS sempre ligado custa caro. Se só precisa da posição quando se desloca, use **smart position update**.
- Display ligado 24/7 custa 10–30 mA constantes. Em nó fixo, desative.

### Configurações Meshtastic de economia

Do [Power Configuration](https://meshtastic.org/docs/configuration/radio/power/):

| Parâmetro | O que faz | Sugestão |
| :--- | :--- | :--- |
| `is_power_saving` | Desativa BT, serial, WiFi e tela quando ocioso. | `true` em nó solar. |
| `ls_secs` (ESP32) | Quanto tempo até entrar em light sleep. | Padrão 300 s; reduza em nó fixo. |
| `min_wake_secs` | Tempo mínimo acordado após receber pacote. | Padrão 10 s; aumente se cair chamada. |
| `wait_bluetooth_secs` | Espera por conexão BLE antes de desligar rádio BT. | Padrão 60 s; em nó solar, baixe para 10 s. |
| `on_battery_shutdown_after_secs` | Desliga rádio após X s sem fonte externa. | Útil em drone/balão, **não** em solar. |
| `adc_multiplier_override` | Corrige leitura de tensão da bateria. | Só se o firmware reportar errado. |

Configure pelo app (Radio Configuration → Power) ou via CLI:

```bash
meshtastic --set power.is_power_saving true --set power.min_wake_secs 15
```

## 🛰️ Antenas — escolha e teste

A antena que vem no kit serve só para teste inicial. Troque antes de sair medindo alcance.

| Cenário | Antena indicada | Ganho | Conector típico |
| :--- | :--- | :--- | :--- |
| Rádio portátil / mochila | Whip flexível (MESHTAC, Signal Plus) | 2,5–3 dBi | SMA macho |
| Nó fixo em apartamento | Omni interna cerâmica ou whip rígida | 5 dBi | SMA macho |
| Nó fixo externo urbano | Omni fibra de vidro | 5–8 dBi | N fêmea |
| Repetidora em morro | Colinear externa | 8–10 dBi | N fêmea |
| Enlace ponto a ponto | Yagi ou painel direcional | 12–18 dBi | N fêmea |

**Onde comprar (referência):** Rokland, Atlavox, MuziWorks (internacional); no mercado nacional, marcas como **GIZONT** e **Ziisor** têm sido bem avaliadas pela comunidade. Procure revendedores por `antena LoRa 915 MHz SMA` ou `antena 915 N macho omnidirecional`.

### Mito vs. fato

!!! warning "Ganho alto nem sempre é melhor"
    Uma antena de 12 dBi concentra o sinal num plano horizontal estreitíssimo. Ótima para ligar dois morros distantes. **Péssima** em topo de morro que precisa cobrir vale abaixo — o feixe passa por cima das casas.

Para nó em ponto alto que cobre região abaixo, prefira ganho moderado (5–8 dBi) ou antenas com *downtilt*.

### VSWR e NanoVNA

Antes de instalar, **teste a antena**. Um NanoVNA custa hoje ~R$ 250 e paga-se na primeira antena ruim que você flagra antes de subir no telhado.

- Alvo: **VSWR < 2.0** em 902–928 MHz. Ideal < 1.5, mas a diferença entre 1.2 e 1.5 é imperceptível na prática.
- Calibre com os padrões **Open/Short/Load** no cabo que vai usar na instalação — sem calibração, a leitura é lixo.
- Afaste o corpo antes de dar *sweep*. Ao comprimento de onda de 33 cm a 915 MHz, mão e parede distorcem tudo.
- Teste a antena na posição final de montagem quando possível.
- Documente com foto da tela ou export do software do NanoVNA.

**Referências de testes da comunidade:**

- [meshtastic/antenna-reports](https://github.com/meshtastic/antenna-reports)
- [pdxlocations/Meshtastic-Antenna-Reports](https://github.com/pdxlocations/Meshtastic-Antenna-Reports)

### Cabos e conectores

- **LMR-400** para trechos ≥ 2 m em uso externo (~0,22 dB/m a 915 MHz).
- **RG-58** só para patches curtos (~1 dB/m — cabo ruim vale menos que antena de 3 dBi).
- **Conectores N** para uso externo: melhor vedação e menor perda que SMA.
- **SMA vs. RP-SMA:** confira o conector da sua placa antes de comprar antena. Trocar por engano estraga a rosca.
- Cada metro de RG-58 a 915 MHz **come ~1 dB**. Rádio o mais perto possível da antena.

## 🔋 Energia — implementação

### Para nó fixo com tomada

- Fonte USB-C de 5 V / 2 A de boa procedência. Fontes baratas injetam ruído de RF que piora a sensibilidade do rádio.
- UPS pequeno ou power bank com *pass-through* mantém o nó operando durante apagões curtos.
- Se a casa tem no-break da PC, ligue o rádio nele.

### Para nó externo / solar

Setup típico em SC (clima úmido, muitos dias nublados):

```
Painel Solar (10–20 W) → Controlador MPPT LiFePO4 → Bateria LiFePO4 6–12 Ah → Rádio (RAK4631)
```

**Dimensionamento:**

- RAK4631 bem configurado: 10–30 mA médios.
- 20 mA × 24 h = **480 mAh/dia**. LiFePO4 de 6 Ah → ~12 dias de autonomia sem sol.
- Painel 10 W em SC rende ~30 Wh em dia de sol pleno. Em dia de chuva forte e painel sujo, ~5 Wh. Com 3 dias nublados seguidos, ainda sobra margem.
- **LiFePO4** é preferível a Li-ion convencional: ciclos de vida 3–5×, tolera mais calor, não inflama.

### Cases e proteção

- Caixas herméticas **IP66 ou superior**.
- Entradas de cabo com **prensa-cabo** vedado. Nunca fure e enfie o fio.
- **Silica gel** trocada a cada inspeção. Umidade em placa é morte certa em SC.
- Fixe o rádio sem pressionar componentes. Parafuso direto na placa é vergonhoso.
- Pinte ou envolva o case em alumínio para reduzir temperatura interna se for pegar sol direto.

## 🧰 Kit DIY — Nó fixo caseiro

Custo aproximado (abril/2026) para um nó fixo decente:

| Item | Preço médio |
| :--- | ---: |
| Heltec V3 ou RAK4631 | R$ 180–400 |
| Antena 5 dBi com cabo 2 m | R$ 80–150 |
| Fonte USB-C de qualidade | R$ 40 |
| Adaptador / suporte de parede | R$ 30 |
| **Total** | **R$ 330–620** |

## 🧰 Kit DIY — Repetidora solar

Para quem quer instalar um nó fixo em morro ou sítio:

| Item | Preço médio |
| :--- | ---: |
| RAK4631 + antena GPS opcional | R$ 350–500 |
| Painel solar 10–20 W | R$ 100–250 |
| Controlador MPPT para LiFePO4 | R$ 80–200 |
| Bateria LiFePO4 6–12 Ah | R$ 150–400 |
| Case IP66 + prensa-cabos | R$ 100–200 |
| Antena colinear 8 dBi + LMR-400 10 m | R$ 250–500 |
| Conectores, fixadores, silica | R$ 100 |
| Protetor de surto em linha de antena | R$ 80–150 |
| **Total** | **R$ 1.210–2.300** |

A comunidade costuma organizar *vaquinhas* para levantar parte desse custo quando o local é estratégico. Veja [Comunidade e Governança](comunidade-governanca.md).

## 🧯 Boas práticas de instalação

- **Aterramento:** em nó de morro, aterre o mastro e use protetor de surto na linha de antena. Raio não respeita orçamento.
- **Vedação:** sele todas as conexões externas com fita auto-fusão + fita isolante comum por cima.
- **Altura:** 1 metro a mais na antena costuma render mais alcance que trocar o rádio.
- **Identificação:** cole uma etiqueta no case com contato, data de instalação e versão do firmware. O próximo voluntário que for fazer manutenção agradece.
- **Documentação:** faça fotos do setup, registre SWR medido, guarde no repositório do site.
