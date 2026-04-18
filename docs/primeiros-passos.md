# Primeiros Passos

Aqui você aprenderá o básico para entrar na rede SC Mesh. Se for sua primeira vez com rádio digital, siga a ordem das seções abaixo.

## ✅ Checklist do iniciante

Antes de comprar qualquer coisa, veja o que você precisa ter em mãos:

- [ ] Um rádio Meshtastic compatível com 915 MHz.
- [ ] Um celular Android ou iOS para parear por Bluetooth.
- [ ] Uma antena (pode ser a que vem no kit — troque depois).
- [ ] Uma fonte de energia (bateria interna, USB ou power bank).
- [ ] Acesso à internet só na instalação inicial (para flashear o firmware).

## 🛠️ Qual rádio comprar?

Para começar, você precisará de um rádio compatível com Meshtastic operando na frequência de **915 MHz** (padrão brasileiro). Recomendados:

- **LILYGO T-Beam** — já vem com GPS e suporte a bateria 18650. Bom para uso móvel e trilhas.
- **Heltec V3** — econômico, com tela OLED. Ideal para quem está começando e vai usar em casa.
- **RAK WisBlock (RAK4631)** — melhor eficiência energética. Ideal para repetidoras solares.

Comparação mais detalhada em [Hardware](hardware.md).

## 📲 Configuração inicial

1. **Baixe o app Meshtastic:**
   - [Android](https://play.google.com/store/apps/details?id=com.geeksville.mesh)
   - [iOS](https://apps.apple.com/us/app/meshtastic/id1586432531)
2. **Flasheie o firmware:** use o [Meshtastic Flasher](https://flasher.meshtastic.org/) direto pelo navegador (Chrome/Edge). Escolha seu modelo, clique em *Flash* e aguarde.
3. **Pareie via Bluetooth** pelo aplicativo. O pin padrão é `123456` (mude depois).
4. **Defina um nome curto** (*Short Name*, 4 caracteres) e um longo (*Long Name*). Use seu nome, cidade ou indicativo de rádio.
5. **Configure a região:** `ANZ` (915 MHz).

## 📡 Canais e parâmetros padrão da SC Mesh

Para que todos se comuniquem na mesma malha, usamos os parâmetros abaixo:

| Parâmetro | Valor |
| :--- | :--- |
| Região | `ANZ` (915 MHz) |
| Preset primário | `LongFast` |
| Nome do canal primário | `LongFast` (padrão público) |
| Hop Limit | `3` |
| MQTT | **Desativado** |
| GPS Broadcast | A seu critério |

### Canais recomendados

- **`LongFast`** — canal público, padrão de fábrica. É onde a comunidade conversa.
- **`SC-EMERGENCIA`** — canal reservado para ocorrências. Mantenha habilitado mas silencioso. Detalhes em [Protocolos de Emergência](emergencia.md).
- **Canal privado próprio** — crie um com PSK própria para conversar só com sua família/grupo. Compartilhe via QR code pelo app.

## 🏷️ Tipo de nó (Role)

Na configuração do dispositivo, escolha o *role* correto:

- **CLIENT** — padrão. Seu rádio pessoal. Use este.
- **CLIENT_MUTE** — como CLIENT, mas não retransmite. Use em áreas já bem cobertas por outros nós.
- **ROUTER** — apenas para nós fixos em ponto alto, ligados 24/7. Não use no seu rádio pessoal.
- **ROUTER_CLIENT** — evite. Reservado para casos específicos.

## 🔐 Segurança inicial

Antes de sair transmitindo, revise estes pontos — 30 segundos de configuração que evitam dor de cabeça depois:

- **Desative MQTT.** Em *Module Config → MQTT*, deixe `Enabled = false`. A SC Mesh opera off-grid; habilitar MQTT espelha suas mensagens publicamente na internet.
- **Mude o PIN do Bluetooth.** Padrão `123456` é igual para todo mundo. Defina um seu em *Device Config → Security*.
- **Renomeie o nó.** Evite short name padrão tipo `abc1`. Use algo reconhecível (ex.: `FSG1` = "Floripa Saco dos Limões 1").
- **Revise o canal primário.** Se for conversar em canal público, saiba que qualquer um com Meshtastic lê. Para família/grupo, crie canal com PSK dedicada.

Aprofundamento em [Segurança e Privacidade](seguranca-privacidade.md).

## 🔄 Atualização de firmware

O firmware do Meshtastic evolui rápido. Recomendamos versão **2.5 ou superior**.

- **Onde ver a versão atual:** app → *Settings → About*.
- **Quando atualizar:** quando a comunidade migrar para nova versão major (2.x → 2.y) ou quando uma correção de bug te afeta. Não atualize no meio de uma operação crítica.
- **Como atualizar:**
    - Pela [Web Flasher](https://flasher.meshtastic.org/) (mais seguro para ESP32).
    - Pelo próprio app (OTA BLE) — mais conveniente, ocasionalmente falha e exige re-flash.
    - Pela CLI Python: `pip install meshtastic && meshtastic --export-config`.
- **Cuidado com downgrade.** Ir de 2.5 para 2.2 pode corromper configs. Exporte antes: `meshtastic --export-config > backup.yaml`.

## 🧪 Teste inicial

Depois de configurado, abra o app e:

1. Envie uma mensagem no canal `LongFast` dizendo "Teste de alcance, sou novo na rede, cidade X". Espere alguém responder.
2. Veja a lista de nós (*Nodes*). Você deve enxergar pelo menos um vizinho se houver cobertura na sua região.
3. Confira RSSI e SNR dos vizinhos — os números mais importantes que você vai aprender.

### Lendo RSSI e SNR

**RSSI** (intensidade do sinal recebido, em dBm) — quanto mais próximo de 0, melhor:

| RSSI | Qualidade |
| :--- | :--- |
| > -80 dBm | Excelente, vizinho próximo |
| -80 a -100 dBm | Bom |
| -100 a -115 dBm | Funcional |
| -115 a -125 dBm | No limite, mensagens começam a cair |
| < -125 dBm | Inviável |

**SNR** (relação sinal-ruído, em dB) — é mais importante que RSSI para LoRa:

| SNR | Qualidade |
| :--- | :--- |
| > 5 dB | Ótimo |
| 0 a 5 dB | Bom |
| -5 a 0 dB | OK, perda ocasional |
| -10 a -5 dB | No limite |
| < -15 dB | Abaixo do piso de decodificação |

Valores abaixo do esperado? Troque a antena ou mude a posição do rádio (perto da janela, longe de metal) antes de culpar o hardware.

Mais detalhes em [Glossário](glossario.md) e no [teste de alcance sistemático](infraestrutura.md#teste-de-alcance-sistematico).

## ➡️ Próximos passos

- Leia as [Regras e Etiqueta](comunidade-governanca.md#regras-e-etiqueta) antes de começar a transmitir.
- Se quiser contribuir com um nó fixo, veja [Infraestrutura](infraestrutura.md).
- Dúvidas? Comece pelo [FAQ](faq.md) e depois [WhatsApp da comunidade](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ).
