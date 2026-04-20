# Infraestrutura e Deployments

A malha só cresce quando alguém topa levantar um nó. Esta página reúne diretrizes, ferramentas, boas práticas e locais candidatos.

## 🏷️ Classificação de nós

- **CLIENT** — seu rádio pessoal. A maioria.
- **CLIENT_BASE** — nó fixo em casa/escritório; prioriza tráfego de nós favoritos sem exigir ponto alto.
- **CLIENT_MUTE** — CLIENT que não retransmite. Use em áreas já cobertas.
- **ROUTER** — nó fixo em ponto alto, 24/7. Prioriza tráfego alheio.

!!! warning "REPEATER foi descontinuado"
    A role `REPEATER` foi descontinuada no firmware Meshtastic a partir da versão **2.7.11**. Em nós novos, use `ROUTER`. Se você ainda tem um rádio configurado como `REPEATER`, atualize o firmware e migre a role na próxima janela de manutenção.

!!! warning "ROUTER não é decisão individual"
    Configurar seu rádio doméstico como ROUTER em cidade já coberta satura a malha. Antes de subir um nó como ROUTER, avise a comunidade e confirme que o local agrega.

## ☀️ Repetidoras solares

Receita que tem funcionado em SC (umidade alta, muitos dias nublados):

1. **Painel solar** de 10 a 20 W.
2. **Controlador de carga MPPT** para LiFePO4.
3. **Bateria LiFePO4** 6–12 Ah (nunca chumbo-ácido pequena, morre rápido).
4. **Rádio RAK4631** com firmware atual, modo `ROUTER`.
5. **Antena colinear** 8–10 dBi com cabo LMR-400 curto.
6. **Case IP66** com silica gel e prensa-cabos.

Detalhes de dimensionamento e custo em [Hardware](hardware.md#kit-diy-repetidora-solar).

!!! tip "O cabo é o inimigo"
    Rádio sempre o mais próximo possível da antena. Cada metro de RG-58 a 915 MHz consome quase 1 dB. Prefira rádio dentro de um case pequeno no topo do mastro, alimentado por PoE DC barato, do que cabo coaxial longo subindo o mastro.

## 🗺️ Ferramentas para escolher o ponto alto

Antes de subir em qualquer morro, simule. As ferramentas abaixo vão do gratuito ao profissional e cobrem 99 % dos casos:

| Ferramenta | Custo | Para que serve |
| :--- | :--- | :--- |
| [Google Earth Pro](https://www.google.com/earth/versions/) | Grátis | Perfil de elevação entre dois pontos, visualização 3D do terreno. |
| [HeyWhatsThat](https://www.heywhatsthat.com/) | Grátis | Gera o horizonte visível de qualquer coordenada com elevação. Excelente para avaliar pontos altos. |
| [Ubiquiti airLink](https://link.ui.com/) | Grátis | Cálculo de enlace PtP com perfil de terreno, zona de Fresnel e estimativa de sinal. |
| [Radio Mobile (VE2DBE)](https://www.ve2dbe.com/english1.html) | Freeware | Simulação Longley-Rice com mapas SRTM. Offline, clássico entre radioamadores. |
| [CloudRF](https://cloudrf.com/) | Free tier < 10 km; pago acima | Simulação profissional com LiDAR e clutter; API para automação. |
| [RadioPlanner 3.0](https://www.wireless-planning.com/radioplanner) | Comercial (demo disponível) | Planejamento multi-site para redes IoT/LPWAN incluindo LoRa. |
| [Calculadora de zona de Fresnel](https://www.everythingrf.com/rf-calculators/fresnel-zone-calculator) | Grátis | Verifica raio da 1ª zona de Fresnel em função de distância e frequência. |
| [QGIS](https://qgis.org/) + dados SRTM/ALOS | Grátis | Para quem quer granularidade máxima e análise espacial customizada. |

**Fluxo recomendado para avaliar um ponto:**

1. Abra HeyWhatsThat com a coordenada do candidato e veja que horizonte ele alcança.
2. Identifique os 2–3 nós mais próximos que aparecem no horizonte.
3. Para cada par, rode o airLink ou Radio Mobile e confira visada limpa + Fresnel.
4. Se tudo OK, faça **visita técnica presencial** com GPS e um rádio Meshtastic para validar antes de subir a repetidora.

## ✅ Critérios para um bom ponto alto

Antes de investir numa repetidora, o local deve atender:

- **Visada limpa** para ao menos 1 nó já existente na rede (confirmada em simulação).
- **Zona de Fresnel** 1 com ≥ 60 % livre. Menos que isso atenua demais.
- **Acesso razoável** para manutenção: estrada/trilha até o ponto, sem travessias perigosas.
- **Autorização formal documentada** do proprietário (prefeitura, concessionária, fazenda, igreja). Email ou contrato simples resolve.
- **Energia viável:** insolação direta ≥ 4 h/dia em dia típico, ou tomada próxima.
- **Baixo vandalismo** — evitar pontos com tráfego humano aleatório se a caixa for visível.
- **Operador local definido** — alguém no perímetro de 30 min de carro, disponível para manutenção.

## 🧰 Planejamento de um novo nó

Antes de comprar hardware:

1. **Há visada** para pelo menos um nó já na rede? Use airLink/Radio Mobile.
2. **Quem opera?** Nó sem operador definido é nó que vira sucata em 6 meses.
3. **Energia e acesso** — painel solar ou tomada? Como chegar para manutenção?
4. **Autorização formal** — documente por escrito.
5. **Padrão de naming** — use `<Cidade>-<Ponto>-<NN>`, ex.: `BNU-Tromba-01`.

## 📍 Pontos ativos

Locais que já têm repetidora dedicada operando na rede SC Mesh:

- **Morro dos Muller — Antônio Carlos** — cobre boa parte da Grande Florianópolis norte.

*Esta lista cresce conforme a comunidade formaliza cada nó. Se o seu nó fixo atende a rede, nos avise para incluirmos aqui.*

## 🎯 Locais candidatos (chamada aberta)

Pontos altos estratégicos que ainda precisam de operador/padrinho:

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

## 🛠️ Manutenção

### Cronograma

| Frequência | O que fazer |
| :--- | :--- |
| **Mensal** | Inspeção remota: uptime, bateria, SNR dos vizinhos, air utilization. |
| **Trimestral** | Visita física: vedação do case, silica, limpeza do painel, fixação do mastro. |
| **Semestral** | Manutenção pesada: trocar silica, verificar conexões de antena, medir VSWR de novo, atualizar firmware. |
| **Anual** | Checar bateria LiFePO4 (SoC, tensão por célula, resistência interna). Trocar se necessário. |

### Diagnóstico remoto

Tudo isso dá para monitorar pelo app Meshtastic sem sair de casa:

- **SNR** dos vizinhos diretos — queda = obstáculo novo ou antena desalinhada.
- **RSSI** — mudança brusca = cabo/conector degradado.
- **Air utilization %** — > 25 % por muito tempo = tráfego saturando; investigar.
- **Uptime** — reinícios espontâneos = bug de firmware ou brownout de bateria.
- **Bateria** — comparar tensão pela manhã (antes do sol) ao longo dos dias; queda sistemática = painel, controlador ou célula morrendo.

### Kit de manutenção para levar ao campo

- Chave Philips/Allen variada.
- Fita auto-fusão + isolante (roubo comum é só levar a isolante e esquecer a de fusão).
- Silica gel nova (em embalagem selada).
- Multímetro básico.
- NanoVNA para checar antena no próprio local.
- Câmera/celular para documentar.
- Rádio Meshtastic extra para testar comunicação ponto a ponto.
- Cabo USB-C ou Bluetooth para atualizar firmware in-situ.

### Log de manutenção

Sugerimos manter um log Markdown no próprio repositório do site por nó, em `docs/manutencao/<cidade>-<ponto>.md`, com data, intervenção, VSWR medido, fotos e próximo passo. Isso evita que a "sabedoria oral" sobre a repetidora se perca quando o operador muda.

## 📡 Teste de alcance sistemático

Antes de afirmar que um nó cobre X km, faça um teste estruturado:

1. **Posição fixa do nó testado** com GPS. Registre coordenadas.
2. Escolha 5–10 pontos a distâncias crescentes (1, 3, 5, 10, 20 km…).
3. Em cada ponto, envie 5 mensagens numeradas com horário e coordenada sua.
4. Registre, em planilha: distância, mensagens enviadas, mensagens recebidas, RSSI, SNR, obstáculos observados.
5. Depois plote a **distância máxima confiável** (≥ 80 % de recebimento) — essa é a cobertura real daquele nó.

Modelo de planilha sugerido (colunas): `Data | Ponto | Coord | Dist (km) | Enviadas | Recebidas | RSSI min | SNR min | Observação`.

## 📊 Métricas da rede

Acompanhe o estado da malha em tempo real pelo mapa:

- [MeshMap](https://meshmap.net/) — mapa global de nós Meshtastic.
- [Plataforma Meshtastic Brasil](https://platform.meshbrasil.com/) — visão com foco no Brasil.

> Nota: ambos dependem de nós com MQTT ativo para aparecer. Como a SC Mesh prefere operar 100 % off-grid, muitos de nossos nós **não** aparecem nesses mapas — e tudo bem.
