# Casos de Uso

Para que usar, concretamente, uma rede mesh LoRa em Santa Catarina? Abaixo estão os cenários que a comunidade tem explorado. Se você usa ou já usou a rede em situação real, relate pela [comunidade no WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ) ou num Pull Request — vamos incorporando aqui.

## 🥾 Trilhas e montanhismo

A Serra Catarinense, Aparados da Serra e Parque da Serra do Tabuleiro têm longos trechos sem cobertura celular. Um rádio Meshtastic na mochila permite:

- **Coordenar deslocamento** entre grupos que se separaram.
- **Enviar posição** por GPS ao ponto-base ou ao familiar que ficou no carro.
- **Pedir socorro** com formato `[SOS]` se houver qualquer nó dentro do alcance — mesmo que seja outro grupo na mesma trilha.
- **Check-in periódico** com quem ficou em casa.

Combine com apps de mapa offline (Organic Maps, Gaia, Locus Map) carregados com os contornos da serra.

## ⛵ Vela, pesca e navegação costeira

Entre ilhas e costas, o 915 MHz se propaga bem sobre água. Casos práticos:

- **Comunicação entre barcos** do mesmo grupo em regatas amadoras.
- **Posição em tempo real** entre embarcação e apoio em terra sem pagar rádio VHF marítimo com licença.
- **Alerta de problema** sem depender de sinal de celular distante da costa.

Lembre: em emergência marítima real, o canal oficial continua sendo **Canal 16 VHF** (156,8 MHz) — Meshtastic é complementar, não substituto.

## 🏞️ Comunicação entre sítios e áreas rurais

Em regiões rurais de SC onde o sinal de celular some em pontos específicos:

- Conectar casa principal a galpão ou curral a 500–2000 m.
- Botão de alerta entre idosos que moram sozinhos e parentes no mesmo vale.
- Sensor remoto (porteira, poço, bomba d'água) reportando via Meshtastic + módulo externo.

A vantagem sobre Wi-Fi ponto-a-ponto é não precisar de energia em pontos intermediários e funcionar sem planejamento de visada rígido.

## 🏁 Eventos comunitários

Eventos onde celular trava por saturação de rede (muita gente concentrada em pouco espaço):

- Festivais e eventos de rua.
- Provas de corrida e mountain bike — postos de controle reportam chegadas ao cronometrista central.
- Feira e mercados rurais com organização distribuída.
- Jogos de *airsoft/paintball* em campos grandes.

## 🌊 Resposta a eventos climáticos

Santa Catarina tem histórico de enchentes no Vale do Itajaí e deslizamentos na Serra. Nos eventos de 2023 e 2024:

- Defesa Civil reportou colapso das torres de celular em bairros inteiros.
- Radioamadores da RENER prestaram apoio oficial em diversos trechos.
- Voluntários informais coordenaram abrigos e resgates por grupos de WhatsApp — que também cairam quando a internet falhou.

A SC Mesh busca preencher esse vão: comunicação **local**, **sem infra**, **resistente a apagão**. Veja [Protocolos de Emergência](emergencia.md) para o protocolo completo.

## 🏠 Vizinhança organizada

Bairros com histórico de furto ou ocorrências de rotina têm montado canais privados para alerta rápido:

- Avisar avistamento suspeito sem postar em grupo de WhatsApp aberto.
- Ligar sensores de portão a um nó central que repassa aviso.
- Sincronizar ronda comunitária.

Importante: **não é substituto de 190** — é primeira camada de coordenação entre vizinhos.

## 🎓 Educação e experimentação

Escolas técnicas e universidades em SC têm usado Meshtastic como plataforma didática para:

- Disciplinas de RF e telecomunicações.
- Projetos de IC em IoT e redes mesh.
- Robótica e drones com telemetria off-grid.

Se você é educador e tem um projeto Meshtastic, avise a comunidade — gostaríamos de catalogar.

## 🧪 O que a rede **não** é boa em

Honestidade técnica para setar expectativas:

- **Chamada de voz.** Não. LoRa é para texto curto.
- **Alta banda.** Esqueça fotos, áudio, vídeo.
- **Comunicação em tempo real ininterrupta.** Airtime limitado — muita gente falando ao mesmo tempo satura.
- **Substituto de telefone.** É um meio secundário; planeje a redundância, não a substituição.
- **Anonimato ou privacidade de ouro.** Veja [Segurança e Privacidade](seguranca-privacidade.md).

## 📣 Conte seu caso

Você usou (ou vai usar) a rede em situação real?

- Relate no [WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ) com: contexto, resultado, o que funcionou, o que faltou.
- Prefere formalizar? Abra um Pull Request no [repositório](https://github.com/scmesh/scmesh.github.io) adicionando sua história nesta página.
- Vamos construindo um histórico útil para quem chega.
