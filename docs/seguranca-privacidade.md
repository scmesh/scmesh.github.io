# Segurança e Privacidade

A SC Mesh é **comunicação por rádio**. Rádio é, por definição, um meio aberto: qualquer um com equipamento compatível e dentro do alcance pode capturar seus pacotes. O que o Meshtastic oferece é criptografia forte de conteúdo — mas o tráfego em si permanece visível. Esta página explica o que está protegido, o que não está, e como se comportar.

## 🎯 Modelo de ameaça

Antes de aplicar "recomendações", pergunte contra quem você quer se proteger. Cada nível exige cuidados diferentes:

| Ameaça | Proteção nativa | O que você precisa fazer |
| :--- | :--- | :--- |
| Vizinho curioso com Meshtastic | Alta em canal com PSK | Não usar só `LongFast` |
| Pessoa específica que sabe que você usa LoRa | Média | Rotacionar PSK, não publicar QR |
| Adversário com SDR dedicado e tempo | Baixa no metadado | Não compartilhar padrões de uso |
| Estado-nação com recursos ilimitados | Nenhuma garantia | Não use Meshtastic para isso |

!!! warning "Meshtastic não é Signal"
    Se o cenário é proteger jornalismo investigativo, denúncia grave, segredo de vida ou morte — **use Signal sobre internet** ou ferramentas realmente projetadas para contrainteligência. Meshtastic é comunicação resiliente off-grid, não comunicação anônima.

## 🔐 O que é cifrado

- **Payload** de mensagens em canal com PSK (AES256-CTR).
- **Payload** de DMs (chave derivada do par origem-destino).
- **Telemetria** e posição **se** enviados em canal cifrado.

## 🔓 O que NÃO é cifrado

- **ID de origem** e **ID de destino** do nó — quem falou com quem é visível.
- **Timestamp** e contadores — quando aconteceu é visível.
- **Channel hash** — o canal usado é identificável (quem tem a mesma PSK descobre).
- **Tamanho do pacote** — dá para inferir "mensagem curta" vs. "mensagem longa".
- **Localização física** do transmissor — tecnicamente detectável por *direction finding* com 2+ receptores.

### O que isso significa na prática

Um observador pode afirmar: "o nó `FSG1` conversou com `FSG2` às 14:32, trocou 3 pacotes de ~80 bytes cada". O **conteúdo** ele não sabe. Mas o **fato da comunicação** e o **padrão** ele sabe.

## 📶 Canais

### Canal público `LongFast`

- PSK padrão, conhecida por todo firmware Meshtastic.
- **Trate como rádio aberto.** Qualquer pessoa em qualquer lugar do mundo com Meshtastic em modo público lê tudo.
- Use-o para: anúncios à comunidade, pedido de teste de alcance, coordenação geral.
- **Não use para:** combinar encontros privados, falar sobre rotinas, compartilhar coordenadas de casa.

### Canal com PSK customizada

- Você gera uma chave de 256 bits; só quem tem a chave lê.
- Compartilhe o QR code com **cuidado**: quem tirar print e compartilhar abre o canal para qualquer um.
- Rotacione a PSK se desconfiar de vazamento ou se alguém sair do grupo.
- Canais separados por contexto: um para família, outro para trilheiros, outro para vizinhança.

### DMs (Mensagens Diretas)

- Cifradas com chave derivada do par origem–destino.
- **Só existem entre dois nós conhecidos entre si** — é preciso que ambos tenham se "encontrado" na rede antes (trocaram pacotes no mesmo canal).
- Uma DM não é mais privada que uma mensagem em canal privado que só você e a outra pessoa estão — na prática são equivalentes em termos de criptografia.

## 🛡️ Recomendações práticas

### Para o usuário comum

1. **Crie ao menos um canal privado** para família/grupo próximo. Não dependa só do `LongFast`.
2. **Nunca publique QR codes** de canais privados em rede social, grupo aberto ou print de celular em post público.
3. **Desative MQTT.** Ele espelha seu tráfego (incluindo pacotes que seu nó só ouviu retransmitindo) para servidores na internet.
4. **Mude o PIN do Bluetooth** (padrão `123456` é o mesmo para todos).
5. **Limite compartilhamento de posição.** Se não precisa, deixe GPS desligado; se precisa, envie só em canal privado.
6. **Evite "short name" com dado pessoal.** `Joao CPF 123` é má ideia; `JVN1` basta.

### Para quem opera repetidora

1. **Nó fixo exposto fisicamente** é tentador para vandalismo ou clonagem. Considere acesso só por Bluetooth com PIN forte.
2. **Documente o acesso admin** num canal interno da comunidade, não em local público.
3. **Revise PSKs** trimestralmente em canais administrativos.
4. **Atualize firmware** — correções de segurança saem com frequência.

### Para quem tem modelos de ameaça específicos

- **Jornalistas/ativistas:** não use Meshtastic como canal único. Combine com Signal sobre dados móveis ou Tor.
- **Operações comerciais sensíveis:** use MQTT **em rede interna** cifrada, não canal público.
- **Resposta a desastres:** aceite que a rede é aberta. Evite dados pessoais identificáveis (CPF, endereço completo) em `[SOS]`.

## 🕵️ Análise de tráfego — o ponto fraco

Mesmo que ninguém leia suas mensagens, saber que você **se comunica** regularmente com certos nós, em certos horários, já revela muito. Se isso é uma preocupação:

- Misture-se ao tráfego: deixe seu nó ligado mesmo sem usar.
- Evite padrões horários (ex.: "toda noite às 22h mando pro cônjuge").
- Use canais de grupo em vez de DMs para diluir a relação um-para-um.

## 📜 Aspectos legais

- Capturar pacotes LoRa de terceiros em ISM é tecnicamente legal — é uma banda de uso compartilhado sem expectativa legal de sigilo no ar.
- Mas **decifrar** um canal privado sem autorização é análogo a invasão — pode ser enquadrado em crime cibernético (Lei 12.737/2012).
- Publicar conteúdo de mensagens privadas de terceiros extraídas da rede é violação de privacidade (LGPD e legislação geral).

Se suspeitar de abuso (captura e publicação de mensagens da rede), reporte à comunidade e considere notificação formal.

## 🔄 Quando rotacionar chaves

Rotacione PSK de um canal quando:

- Alguém saiu do grupo ou perdeu um dispositivo pareado.
- O QR code foi exposto (mesmo que você ache que foi "só rapidinho").
- O hardware que tinha a chave foi roubado.
- Periodicamente, a cada 6–12 meses, por higiene.

Para rotacionar: gere nova PSK no app, compartilhe presencialmente (ou por Signal) o novo QR com os membros.

## ℹ️ Leitura adicional

- [Meshtastic — Encryption docs](https://meshtastic.org/docs/overview/encryption/)
- [OWASP Threat Modeling](https://owasp.org/www-community/Threat_Modeling) — para pensar ameaças de forma estruturada.
- Relato técnico do protocolo em [github.com/meshtastic/firmware](https://github.com/meshtastic/firmware).
