# Infraestrutura e Deployments

A malha só cresce quando alguém topa levantar um nó. Esta página reúne diretrizes, boas práticas e locais candidatos.

## 🏷️ Classificação de nós

- **CLIENT** — seu rádio pessoal. A maioria.
- **CLIENT_MUTE** — CLIENT que não retransmite. Use em áreas já cobertas.
- **ROUTER** — nó fixo em ponto alto, 24/7. Prioriza tráfego alheio.
- **REPEATER** — variante mais enxuta do ROUTER, sem recursos de cliente.

!!! warning "ROUTER não é decisão individual"
    Configurar seu rádio doméstico como ROUTER em cidade já coberta satura a malha. Antes de subir um nó como ROUTER, avise a comunidade e confirme que o local agrega.

## ☀️ Repetidoras solares

A receita que tem funcionado em SC (umidade alta, muitos dias nublados):

1. **Painel solar** de 10 a 20 W.
2. **Controlador de carga MPPT** para LiFePO4.
3. **Bateria LiFePO4** 6–12 Ah (nunca chumbo-ácido pequena, morre rápido).
4. **Rádio RAK4631** com firmware atual, modo `ROUTER`.
5. **Antena colinear** 8–10 dBi com cabo LMR-400 curto.
6. **Case IP66** com silica gel e prensa-cabos.

Detalhes de dimensionamento e custo em [Hardware](hardware.md#kit-diy-repetidora-solar).

!!! tip "O cabo é o inimigo"
    Rádio sempre o mais próximo possível da antena. Cada metro de RG-58 a 915 MHz consome quase 1 dB. Prefira rádio dentro de um case pequeno no topo do mastro, alimentado por PoE DC barato, do que cabo coaxial longo subindo o mastro.

## 📍 Pontos ativos

Locais que já têm repetidora dedicada operando na rede SC Mesh:

- **Morro dos Muller — Antônio Carlos** — cobre boa parte da Grande Florianópolis norte.

*Esta lista cresce conforme a comunidade formaliza cada nó. Se o seu nó fixo atende a rede, nos avise para incluirmos aqui.*

## 🎯 Locais candidatos (chamada aberta)

Pontos altos estratégicos que ainda precisam de operador/padrinho. Se você tem acesso a um deles, fale com a comunidade:

### Litoral e Grande Florianópolis
- Morro da Cruz (Florianópolis)
- Morro do Cambirela (Palhoça)
- Morro dos Cavalos (Palhoça)
- Pico do Gavião (Governador Celso Ramos)

### Vale do Itajaí
- Morro da Tromba (Blumenau)
- Serra dos Índios (Indaial)
- Alto do Mirante (Gaspar)

### Norte
- Serra Dona Francisca (Joinville)
- Morro do Boa Vista (Joinville)

### Serra Catarinense
- Morro da Igreja (Urubici)
- Serra do Rio do Rastro

### Oeste e Meio-Oeste
- Parque Estadual Fritz Plaumann (Concórdia)
- Morros altos ao redor de Chapecó

Tem acesso, familiares ou pode interceder por autorização em algum ponto acima? Entre em contato pelo [WhatsApp](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ).

## 🧰 Planejamento de um novo nó

Antes de instalar, responda:

1. **Há visada** para pelo menos um nó já na rede? Use [Calculadora de enlace](https://link.ui.com/) com as coordenadas.
2. **Quem opera?** Nó sem operador definido é nó que vira sucata em 6 meses.
3. **Energia e acesso** — painel solar ou tomada? Como chegar para manutenção?
4. **Autorização formal** — é área pública, privada, concessionada? Documente permissão.
5. **Padrão de naming** — use `<Cidade>-<Ponto>-<NN>`, ex.: `BNU-Tromba-01`.

## 🛠️ Manutenção

Todo nó fixo precisa ter:

- **Etiqueta** com contato do operador, data de instalação e firmware.
- **Acesso remoto** via Bluetooth documentado, ou canal administrativo dedicado.
- **Revisão semestral** física (vedação, silica, bateria, fixação do mastro).
- **Plano de contingência** — se o operador principal sumir, quem herda o nó?

## 📊 Métricas da rede

Acompanhe o estado da malha em tempo real pelo mapa:

- [MeshMap](https://meshmap.net/) — mapa global de nós Meshtastic.
- [Plataforma Meshtastic Brasil](https://platform.meshbrasil.com/) — visão com foco no Brasil.

> Nota: ambos dependem de nós com MQTT ativo para aparecer. Como a SC Mesh prefere operar 100 % off-grid, muitos de nossos nós **não** aparecem nesses mapas — e tudo bem.
