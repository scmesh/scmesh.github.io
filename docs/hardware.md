# Guia de Hardware

Escolher bem o hardware é o que separa uma experiência frustrante de uma rede que funciona. Abaixo está o que a comunidade SC Mesh recomenda e por quê.

## 📻 Comparativo de rádios

| Dispositivo | Prós | Contras | Uso recomendado |
| :--- | :--- | :--- | :--- |
| **Heltec V3** | Barato, tela OLED integrada, USB-C | Consumo de energia alto | Nó fixo com tomada, primeiro rádio |
| **RAK WisBlock (RAK4631)** | Consumo baixíssimo, modular, robusto | Preço mais elevado, sem display por padrão | Repetidora solar, nó externo |
| **LILYGO T-Beam** | GPS integrado, suporte a 18650 | Grande, pesado, GPS consome bateria | Uso móvel, trilha, mochila |
| **Station G2** | Antena N integrada, feito para externo | Mais caro, menos opções de case | Nó fixo de longo prazo |
| **T-Deck / T-Deck Plus** | Teclado físico, tela, funciona standalone | Caro, bateria pequena | Uso em campo sem celular |

> Compre sempre a versão **915 MHz / US 915 / AU 915**. A versão europeia (868 MHz) **não** funciona aqui.

## 🛰️ Antenas

A antena que vem no kit serve para testar. Para uso real, troque.

| Cenário | Antena indicada | Ganho típico |
| :--- | :--- | :--- |
| Rádio portátil / mochila | Omnidirecional curta, flexível | 3 dBi |
| Nó fixo em apartamento | Omnidirecional interna | 5 dBi |
| Nó fixo externo urbano | Omnidirecional externa (fibra) | 5–8 dBi |
| Repetidora em morro | Colinear externa, N fêmea | 8–12 dBi |
| Enlace ponto a ponto | Yagi ou painel direcional | 12–18 dBi |

!!! tip "Antena boa > rádio caro"
    Investir R$ 200 numa antena decente faz mais diferença do que trocar de rádio. A física do LoRa agradece.

### Cabos e conectores

- Use cabos **LMR-400** ou equivalentes para trechos acima de 2 m.
- Prefira conectores **N** para uso externo (melhor vedação e perda menor que SMA).
- Conectores **SMA/RP-SMA**: confira qual sua placa usa antes de comprar. Trocar por engano estraga a rosca.
- Cada metro de cabo RG-58 a 915 MHz **perde quase 1 dB**. Por isso: rádio o mais perto possível da antena.

## 🔋 Energia

### Para nó fixo com tomada
- Fonte USB-C de 5 V / 2 A de boa procedência. Fontes ruins introduzem ruído de RF.
- UPS pequeno (ou power bank com *pass-through*) mantém o nó funcionando durante apagões curtos.

### Para nó externo / solar

Um setup típico de repetidora solar em SC (clima úmido, dias nublados) costuma ser:

```
Painel Solar (10–20 W) → Controlador de carga MPPT → Bateria LiFePO4 (6–12 Ah) → Rádio (RAK4631)
```

**Dimensionamento básico:**

- RAK4631 bem configurado consome 10–30 mA médios.
- 20 mA × 24 h = 480 mAh/dia. Uma LiFePO4 de 6 Ah dá ~12 dias de autonomia sem sol.
- Painel de 10 W gera em média 30 Wh em dia de sol pleno em SC. Com 3 dias seguidos de chuva forte e painel sujo, ainda sobra margem.

### Cases e proteção

- Use caixas herméticas **IP66 ou superior**.
- Entradas de cabo devem ter **prensa-cabo** com vedação (não fure a caixa e enfie o fio).
- Coloque **silica gel** dentro do case. Umidade condensando em placa é morte certa.
- Fixe o rádio sem pressionar componentes. Parafuso direto na placa é vergonhoso.

## 🧰 Kit DIY — Nó fixo caseiro

Custo aproximado (abril/2026) para um nó fixo decente:

| Item | Preço médio |
| :--- | ---: |
| Heltec V3 ou RAK4631 | R$ 180–400 |
| Antena 5 dBi com cabo 2 m | R$ 80–150 |
| Fonte USB-C de qualidade | R$ 40 |
| Adaptador / suporte de parede | R$ 30 |
| **Total** | **R$ 330–620** |

## 🧰 Kit DIY — Repetidora solar

Para quem quer instalar um nó fixo em morro ou sítio:

| Item | Preço médio |
| :--- | ---: |
| RAK4631 + antena GPS opcional | R$ 350–500 |
| Painel solar 10–20 W | R$ 100–250 |
| Controlador de carga MPPT para LiFePO4 | R$ 80–200 |
| Bateria LiFePO4 6–12 Ah | R$ 150–400 |
| Case IP66 + prensa-cabos | R$ 100–200 |
| Antena colinear 8 dBi + cabo LMR-400 10 m | R$ 250–500 |
| Conectores, fixadores, silica | R$ 100 |
| **Total** | **R$ 1.130–2.150** |

A comunidade costuma organizar *vaquinhas* para levantar parte desse custo quando o local é estratégico. Veja [Comunidade e Governança](comunidade-governanca.md).

## 🧯 Boas práticas de instalação

- **Aterramento:** em nó de morro, aterre o mastro e use protetor de surto na linha de antena. Raio não respeita orçamento.
- **Vedação:** sele todas as conexões externas com fita auto-fusão + fita isolante comum por cima.
- **Altura:** 1 metro a mais na antena costuma render mais alcance que trocar o rádio.
- **Identificação:** cole uma etiqueta no case com contato, data de instalação e versão do firmware. O próximo voluntário que for fazer manutenção agradece.
