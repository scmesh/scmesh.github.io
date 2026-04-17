# Perguntas Frequentes

Respostas curtas para as dúvidas que mais aparecem no grupo. Para termos técnicos, consulte o [Glossário](glossario.md).

## Sobre o projeto

### O que é a SC Mesh afinal?
Uma rede de rádio comunitária, voluntária e sem fins lucrativos, em Santa Catarina, usando o firmware Meshtastic sobre LoRa 915 MHz. Funciona sem internet, sem celular e sem servidor central.

### Quanto custa entrar?
Um rádio básico (Heltec V3 ou LILYGO T-Beam) sai por R$ 150–300 dependendo do câmbio e do fornecedor. Com bateria e antena decente, R$ 400 resolve. Não há mensalidade — a rede é mantida por quem a usa.

### É legal? Preciso de licença?
Sim, é legal. A faixa de 915 MHz é ISM e não exige licença de radioamador, desde que você respeite o limite de potência estabelecido pela Anatel (resumidamente: não ultrapasse 30 dBm / 1 W EIRP).

### A rede tem conexão com a internet?
Por escolha da comunidade, **não**. Priorizamos comunicação puramente via rádio. Por favor, **não habilite MQTT** em seu nó — isso espelharia as mensagens publicamente na internet e contraria o espírito do projeto.

## Alcance e performance

### Qual o alcance real de um rádio?
Depende muito do cenário:

- **Dentro de apartamento, cidade densa:** 200 m a 1 km.
- **Em bairro baixo, antena interna:** 1–3 km.
- **Antena externa em sacada alta:** 5–15 km.
- **Morro contra morro, visada limpa:** 30–100 km+. O recorde mundial passa de 300 km.

### Meu alcance está ruim, o que pode ser?
Na ordem mais comum:

1. **Antena ruim ou mal acoplada.** A antena que vem com o rádio é sofrível. Troque por uma de 3–5 dBi antes de qualquer outra coisa.
2. **Rádio dentro de casa, perto de paredes/lajes.** Coloque perto da janela virada para o próximo nó.
3. **Preset errado.** Fora do LongFast você não fala com ninguém.
4. **Região errada.** Tem que estar em `ANZ` (915 MHz). `EU` ou `US` não conversam.

### Meu pacote não chega a cidades vizinhas. É normal?
Sem um repetidor alto entre você e a outra cidade, é o esperado. O backbone está em construção — contribua instalando um nó em ponto alto se puder, ou apoie uma vaquinha comunitária.

## Uso e cotidiano

### Gasta muita bateria do celular?
Não. O app Meshtastic só conversa por Bluetooth com o rádio, que é quem faz o trabalho pesado. Algo como 2–5% de bateria extra por dia em uso normal.

### Posso usar sem GPS?
Pode. O GPS só serve para compartilhar sua posição — se não for útil para você, desative. Em rádios sem GPS (ex.: Heltec V3) você pode definir uma posição fixa manualmente.

### As minhas mensagens são privadas?
Mensagens diretas (DM) e canais com PSK própria são cifrados com AES256. Ninguém fora do canal lê. O canal `LongFast` público usa a PSK padrão — tecnicamente qualquer um com o firmware pode ler, então **trate-o como rádio aberto**.

### Dá pra mandar foto, áudio ou arquivo?
Não. O LoRa é baixíssima largura de banda. Só cabe texto curto (≤ 237 bytes por pacote), posição e telemetria.

### E se eu quiser conversar só com um grupo de amigos?
Crie um canal novo com nome e PSK próprios, compartilhe o QR code entre vocês. Suas mensagens trafegam pela malha, mas só vocês decifram.

## Hardware

### Qual rádio comprar primeiro?
Para começar rápido e barato: **Heltec V3**. Para uso em trilha com GPS: **LILYGO T-Beam**. Para repetidora solar: **RAK WisBlock com RAK4631**. Detalhes em [Hardware](hardware.md).

### Preciso soldar alguma coisa?
Não. Todos os rádios recomendados vêm prontos. Você só flasha o firmware pelo navegador (Meshtastic Flasher), conecta uma antena e pareia pelo celular.

### Antena de 18 dBi é melhor que de 5 dBi?
Depende. Antenas de ganho alto são mais direcionais — concentram o sinal num plano, perdendo cobertura vertical. Para um nó fixo no alto de um morro, ótimo. Para seu rádio portátil em movimento, antena de 3–5 dBi omnidirecional é mais útil.

## Rede e etiqueta

### Posso configurar meu rádio como ROUTER?
Só se ele ficará **24 horas ligado em ponto alto** e não tiver outro ROUTER cobrindo a mesma área. Rádio pessoal deve ficar como `CLIENT`. Cada `ROUTER` a mais em região já coberta só cria retransmissões redundantes e polui a malha.

### Com que frequência pode enviar telemetria?
Em canais públicos, intervalos ≥ 1 hora. Em canal privado seu, faz o que quiser. Lembre: cada pacote automático seu concorre com uma mensagem de outra pessoa.

### Alguém me mandou mensagem mas não vi a notificação
O app Meshtastic precisa estar autorizado a rodar em segundo plano e manter Bluetooth ligado. No Android, desative otimização de bateria para o app. No iOS, mantenha o app aberto ou use notificações push do Meshtastic Cloud (se você aceitar essa dependência).

## Emergência

### Posso pedir socorro pela rede?
Sim, esse é um dos objetivos do projeto. Mas **primeiro ligue para 190/192/193** se houver sinal. Use a SC Mesh quando os canais oficiais falharem. Veja o formato de mensagem em [Protocolos de Emergência](emergencia.md).

### A rede funciona sozinha num apagão?
Se houver repetidoras solares no caminho, sim. Essa é a motivação do nosso esforço de construir um backbone solar — ele precisa operar sem energia da rede pública.

---

Não achou sua pergunta? Pergunte no [WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ) — se a dúvida for comum, entra no FAQ.
