# Protocolos de Emergência

A SC Mesh nasceu pensando em cenários onde as redes convencionais falham: enchentes no Vale do Itajaí, vendavais no Litoral, deslizamentos na Serra ou qualquer evento que derrube torres de celular e internet. Esta página descreve como a rede deve ser usada nesses momentos.

!!! warning "Leia antes da emergência"
    A hora de aprender a usar o rádio **não** é durante o desastre. Faça testes periódicos, mantenha baterias carregadas e deixe o app Meshtastic instalado e pareado com o seu dispositivo.

## 🚨 Canais de Emergência

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

## 🔕 Disciplina de Rádio

Durante eventos críticos a rede fica saturada. Ajude a manter o canal livre:

- **Silêncio útil:** não responda só para confirmar recebimento. Se for repassar, repasse a mensagem inteira para outro grupo/pessoa.
- **Desative telemetria** (bateria, temperatura, posição automática) em situações de pico. Cada pacote automático concorre com um pedido de socorro.
- **Evite grupos/chats paralelos** no canal primário. Crie canais privados com PSK para conversas entre amigos.
- **Hop Limit 3** é suficiente para quase toda Santa Catarina com a malha saudável. Não aumente sem motivo — pacotes com hop alto se multiplicam e congestionam a rede.

## 🔋 Kit Mínimo para 72 horas

- Rádio Meshtastic com antena de no mínimo 3 dBi.
- Bateria externa ≥ 10.000 mAh ou painel solar pequeno (5–10 W).
- Celular carregado com o app Meshtastic e mapas offline da sua região.
- Lista impressa com coordenadas de referência (hospital, bombeiros, abrigos, casa de familiares).
- Cabo USB-C de reserva.

## 🧭 Coordenação com Defesa Civil e Bombeiros

A SC Mesh **não substitui** o 190, 192 ou 199 — sempre que houver sinal convencional, use os canais oficiais. A rede entra em cena quando eles falham ou estão saturados.

Se você é voluntário formal de Defesa Civil, Bombeiros ou ONG de resposta a desastres e quer integrar-se à operação, entre em contato pela [Comunidade no WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ).

## 🧪 Simulados

A comunidade realiza simulados trimestrais para testar alcance, formato de mensagem e tempo de resposta. Acompanhe o grupo para datas e participe — é a forma mais eficaz de garantir que a rede funcionará quando precisar.
