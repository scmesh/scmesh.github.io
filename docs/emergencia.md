# Protocolos de Emergência

A SC Mesh nasceu pensando em cenários onde as redes convencionais falham: enchentes no Vale do Itajaí, vendavais no Litoral, deslizamentos na Serra ou qualquer evento que derrube torres de celular e internet. Esta página descreve como a rede deve ser usada nesses momentos.

!!! warning "Leia antes da emergência"
    A hora de aprender a usar o rádio **não** é durante o desastre. Faça testes periódicos, mantenha baterias carregadas e deixe o app Meshtastic instalado e pareado com o seu dispositivo.

## ☎️ Contatos oficiais

Antes de qualquer coisa: **se o sinal convencional funciona, ligue para os canais oficiais**.

| Serviço | Número | Observação |
| :--- | :--- | :--- |
| Bombeiros Militar SC | **193** | 24/7 |
| SAMU | **192** | 24/7 |
| Polícia Militar | **190** | 24/7 |
| Polícia Rodoviária Federal | **191** | 24/7 |
| Defesa Civil de Santa Catarina | **199** (emergência) / **(48) 3664-7000** (expediente) | Emergência 24/7 |
| Defesa Civil municipal | Varia por cidade | Cheque o site da prefeitura |

Site oficial da [Defesa Civil de SC](https://www.defesacivil.sc.gov.br/).

## 🚨 Canais de Emergência na SC Mesh

| Canal | Uso | PSK |
| :--- | :--- | :--- |
| `LongFast` | Canal primário, conversas gerais | Padrão público |
| `SC-EMERGENCIA` | Reservado para relatos de ocorrência | A ser definido pela comunidade |
| `SC-LOGISTICA` | Coordenação entre voluntários e repetidoras | A ser definido pela comunidade |

Mantenha `SC-EMERGENCIA` sempre habilitado. Ele deve permanecer silencioso em dias normais — qualquer mensagem nele é sinal de que alguém precisa de atenção.

## 📢 Formato Padrão de Mensagem

Para facilitar leitura e repasse, siga o formato abaixo. Menos caracteres = mais chance da mensagem trafegar:

```
[SOS] Cidade/Bairro | Coord aprox | Situação | Quem sou
```

Exemplos:

```
[SOS] Blumenau Garcia | -26.94,-49.07 | Casa alagada, 2 pessoas no telhado | Joao N7
```

```
[INFO] Rodeio | BR-470 km 42 | Estrada interditada por deslizamento | Ana
```

```
[OK] Rio do Sul Centro | Todos bem, sem luz mas seguros | Familia Lima
```

### Prefixos recomendados

- `[SOS]` — risco de vida, precisa de resgate.
- `[URG]` — urgência médica ou estrutural sem risco imediato.
- `[INFO]` — informação de situação (estrada, abrigo, área afetada).
- `[REQ]` — pedido de recurso (água, medicamento, combustível).
- `[OK]` — relato de que você e seus próximos estão bem.

## 🔀 Fluxo de ativação durante crise

```
Você observa / sofre um incidente
          │
          ▼
Canais oficiais (190 / 192 / 193 / 199) funcionam?
          │
     ┌────┴────┐
     │         │
    SIM       NÃO
     │         │
     ▼         ▼
Use-os.    Monitore SC-EMERGENCIA.
SC Mesh    Envie mensagem no formato padrão.
é apoio.   Se você é radioamador licenciado:
           pode escalonar para REER-SC.
```

1. **Avalie primeiro se há canal oficial.** Se celular funciona ainda que fraco, tente 190/192/193/199 antes de qualquer coisa.
2. **Se falharem ou estiverem saturados**, monitore `SC-EMERGENCIA`. Envie mensagens curtas no formato padrão.
3. **Se você é radioamador licenciado**, pode escalonar para a REER-SC (veja abaixo).
4. **Operadores de nó fixo**: desativem telemetria automática, aumentem a prioridade do canal `SC-EMERGENCIA`, mantenham-se atentos ao repasse.

## 🔕 Disciplina de Rádio

Durante eventos críticos a rede fica saturada. Ajude a manter o canal livre:

- **Silêncio útil:** não responda só para confirmar recebimento. Se for repassar, repasse a mensagem inteira para outro grupo/pessoa.
- **Desative telemetria** (bateria, temperatura, posição automática) em situações de pico. Cada pacote automático concorre com um pedido de socorro.
- **Evite grupos/chats paralelos** no canal primário. Crie canais privados com PSK para conversas entre amigos.
- **Hop Limit 3** é suficiente para quase toda Santa Catarina com a malha saudável. Não aumente sem motivo — pacotes com hop alto se multiplicam e congestionam a rede.

## 📻 Integração oficial — REER-SC e RENER

A **REER-SC (Rede Estadual de Emergência de Radioamadores de Santa Catarina)** é a rede oficial vinculada à Secretaria Estadual de Proteção e Defesa Civil, acionada quando canais convencionais falham. É composta por radioamadores voluntários devidamente licenciados.

### Requisitos para integrar a REER-SC

- **Licença de Radioamador** válida pela Anatel.
- **COER** — Certificado de Operador de Estação de Radioamador.
- Cadastro na RENER (federal) pela [LABRE](https://www.labre.org.br/cadastro-rener/).
- Aguardar publicação da Instrução Normativa estadual que formalizará o cadastro local.

### Links úteis

- [RENER — Rede Nacional de Emergência de Radioamadores](http://sgrainternet.mdr.gov.br/) (Ministério do Desenvolvimento Regional).
- [LABRE — Cadastro RENER](https://www.labre.org.br/cadastro-rener/).
- [LABRE-SC](https://labrescapital.com.br/) — seção catarinense.

!!! note "SC Mesh ≠ REER-SC"
    A SC Mesh é uma **rede comunitária** baseada em Meshtastic/LoRa; a REER-SC é uma **rede formal de radioamadores** em HF/VHF/UHF com vínculo institucional. Podem e devem coexistir: nossos operadores que também são radioamadores atuam nas duas frentes, servindo de ponte entre a Mesh e as autoridades.

## 🔋 Kit Mínimo para 72 horas

**Comunicação:**

- Rádio Meshtastic com antena de no mínimo 3 dBi.
- Bateria externa ≥ 10.000 mAh ou painel solar pequeno (5–10 W).
- Celular carregado com o app Meshtastic e mapas offline da sua região.
- Lista impressa com coordenadas de referência (hospital, bombeiros, abrigos, casa de familiares).
- Cabo USB-C de reserva.
- Fone de ouvido (economiza bateria do celular ao monitorar).

**Sobrevivência básica (72 h):**

- Água potável (3 L/pessoa/dia = 9 L mínimo).
- Alimentos não perecíveis.
- Medicamentos pessoais com receita.
- Documentos em envelope plástico vedado (RG, CPF, comprovantes).
- Lanterna frontal (deixa as mãos livres) + pilhas reserva.
- Apito (ouvido a longa distância com pouco esforço físico).
- Fósforos/isqueiro em saco plástico selado.
- Canivete/multi-ferramenta.
- Mudas de roupa quente e impermeável.
- Kit de primeiros socorros.

Referência: [Defesa Civil SC — Como se preparar](https://www.defesacivil.sc.gov.br/).

## 🧪 Treinamento e simulados

### Simulado estadual anual

A Defesa Civil de SC realiza anualmente um dos maiores simulados de desastres do Brasil, com disparo de alerta via Cell Broadcast e mobilização de voluntários. É a melhor oportunidade de testar a integração da SC Mesh com órgãos oficiais. Acompanhe o [site da Defesa Civil SC](https://www.defesacivil.sc.gov.br/).

### Simulados da comunidade

A SC Mesh realiza simulados trimestrais próprios para testar:

- **Alcance** — até onde chega a malha em estado normal.
- **Formato de mensagem** — quão rápido todos adotam os prefixos.
- **Tempo de resposta** — do `[SOS]` ao acknowledgment.
- **Autonomia em off-grid** — nós solares passam 72 h sem operador.

Acompanhe o [grupo no WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ) para datas.

## 🧭 Coordenação com Defesa Civil e Bombeiros

Se você é voluntário formal de Defesa Civil, Bombeiros Militar, SAMU ou ONG de resposta a desastres e quer integrar-se à operação:

1. Entre em contato pela [Comunidade no WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ).
2. Leve o assunto à sua coordenação local — SC Mesh pode entregar equipamento emprestado para testes.
3. Proponha simulados conjuntos com a corporação.
