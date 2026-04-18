# Para Radioamadores

A SC Mesh **não é** radioamadorismo no sentido formal — opera em ISM 915 MHz, sem indicativo, sem licença individual. Mas há enorme sobreposição de cultura, conhecimento e missão entre as duas comunidades. Esta página é para o radioamador licenciado entender onde a Mesh se encaixa no seu repertório.

## 🆚 Mesh LoRa vs. radioamadorismo tradicional

| Característica | Meshtastic / SC Mesh | Radioamadorismo (HF/VHF/UHF) |
| :--- | :--- | :--- |
| Faixa | ISM 915 MHz (Brasil) | Faixas alocadas pela Anatel |
| Licença | Não exigida | COER (Anatel) |
| Indicativo | Short name livre | Indicativo oficial obrigatório |
| Modo | Texto curto digital (LoRa) | Voz, CW, digital (FT8, RTTY, PSK31, packet, APRS, D-STAR…) |
| Alcance típico | Até ~50 km/hop com visada | Local a global (HF) |
| Largura de banda | Muito baixa (~1 kbps) | De estreita a larga (até MHz) |
| Custo de entrada | R$ 200–400 | R$ 800+ (rádio) + curso/prova |
| Privacidade no canal | AES256 por PSK | Cifragem proibida em radioamador |
| Uso comercial | Permitido (com cuidado) | Proibido por regulamento |

## 🔄 Onde Mesh complementa

A Mesh resolve coisas que rádio amador faz mal e vice-versa:

- **Texto assíncrono.** Você não precisa estar na escuta. Mensagens chegam quando o nó capta.
- **Operação por leigos.** Sem treinamento de proa/popa de chamada — abriu o app, mandou mensagem.
- **Off-grid solar barato.** Repetidora autônoma de R$ 1.500 que opera por anos.
- **Privacidade de conteúdo.** Por ser ISM e não radioamador, **podemos** cifrar — e isso é desejável em muitos contextos.

## 🔗 Onde se conectam (REER-SC, RENER)

Em emergências, quem é radioamador licenciado pode atuar nos dois universos:

- Coordenar **localmente** via SC Mesh (texto, off-grid, qualquer voluntário tem).
- Escalonar para **REER-SC / RENER** via HF/VHF radioamador (alcance estadual/nacional, vínculo institucional com Defesa Civil).

Detalhes em [Emergência — REER-SC](emergencia.md#integracao-oficial-reer-sc-e-rener).

## 🛠️ Hardware aproveitado

Quem já é radioamador costuma ter parte do necessário:

- **Antenas de banda VHF/UHF** geralmente **não servem** para 915 MHz. SWR fica horrível.
- **Cabo coaxial** (LMR-400, RG-213): aproveita direto.
- **Conectores N, SMA, PL-259**: PL não é prático em 915 MHz; os outros sim.
- **Mastros, torres, aterramento**: aproveita 100 %.
- **Bancada e ferramentas** (NanoVNA, multímetro, fonte): tudo serve.
- **Energia solar**: mesmo conhecimento de dimensionamento.

## 📛 Identificação no nó

Recomendamos que radioamadores usem o indicativo (ou parte dele) como short name:

- `PY1AB` → short `PYAB`
- `PU2XYZ` → short `PXYZ`

Isso ajuda a comunidade a saber quem é radioamador licenciado, útil em ativações reais.

## 🎙️ Convivência com tradição radioamadora

Algumas coisas são diferentes de propósito; outras são herdadas:

**O que mantemos da tradição:**
- Etiqueta de canal (silêncio quando não há o que dizer).
- Disciplina em emergência (formato curto, conciso).
- Documentação de instalações.
- Ajuda mútua entre operadores.

**O que **não** se aplica:**
- Não dizemos "QSO", "QTH", "73" no LoRa — são códigos de voz/CW. Em texto, fala normal.
- Não há "dar passagem". O protocolo cuida disso.
- Não há indicativo obrigatório para identificar a transmissão (mas use, se quiser).

## 🤝 Ponte entre comunidades

Se você é radioamador e quer atuar como ponte entre LABRE-SC e SC Mesh:

- Apresente-se na [comunidade SC Mesh](https://chat.whatsapp.com/Hn19DdrY6460uGn0EkYwlQ).
- Avise quando houver mobilização REER-SC — operadores da Mesh podem oferecer apoio logístico complementar.
- Em encontros e eventos, ajude a explicar a diferença para o público leigo.
- Em palestras, considere apresentar em conjunto: Mesh para o público novo, radioamador para quem quer se aprofundar.

## 📚 Para aprofundar

- [LABRE-SC](https://labrescapital.com.br/) — seção catarinense da Liga Brasileira de Radioamadores.
- [Curso COER online](https://www.labre.org.br/) — para quem quer tirar a licença.
- [Anatel — Radiocomunicação](https://www.anatel.gov.br/) — regulamentação.
- [RENER](http://sgrainternet.mdr.gov.br/) — Rede Nacional de Emergência de Radioamadores.
