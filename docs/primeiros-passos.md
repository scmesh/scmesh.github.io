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

## 🧪 Teste inicial

Depois de configurado, abra o app e:

1. Envie uma mensagem no canal `LongFast` dizendo "Teste de alcance, sou novo na rede, cidade X". Espere alguém responder.
2. Veja a lista de nós (*Nodes*). Você deve enxergar pelo menos um vizinho se houver cobertura na sua região.
3. Confira RSSI e SNR dos vizinhos. Se RSSI estiver abaixo de -120 dBm, sua antena/posição precisa melhorar.

## ➡️ Próximos passos

- Leia as [Regras e Etiqueta](comunidade-governanca.md#regras-e-etiqueta) antes de começar a transmitir.
- Se quiser contribuir com um nó fixo, veja [Infraestrutura](infraestrutura.md).
- Dúvidas? Comece pelo [FAQ](faq.md) e depois [WhatsApp da comunidade](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ).
